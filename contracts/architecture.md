# Smart Contract Architecture

<div align="center">
  <img src="../assets/images/icons/collateral.svg" alt="Architecture Icon" width="80" height="80">
  <p><em>Technical Blueprint of the Cirqa Protocol Smart Contracts</em></p>
</div>

<div class="cirqa-highlight">
  <h2>System Overview</h2>
  <p>The Cirqa protocol is built on a modular smart contract architecture that enables secure lending and borrowing of digital assets. The system consists of several key contracts that work together to provide the core functionality.</p>
  
  <div style="display: flex; justify-content: center; margin: 20px 0;">
    <div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; max-width: 800px;">
      <pre style="margin: 0; overflow: auto;">
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│                 │     │                 │     │                 │
│   CirqaToken    │◄────┤  CirqaProtocol  │────►│   CirqaOracle   │
│                 │     │                 │     │                 │
└─────────────────┘     └────────┬────────┘     └─────────────────┘
                                 │
                                 │
                        ┌────────▼────────┐
                        │                 │
                        │ InterestModel   │
                        │                 │
                        └─────────────────┘
      </pre>
    </div>
  </div>
</div>

## CirqaToken

<div style="background-color: #f0f8ff; padding: 20px; border-radius: 8px; margin-bottom: 20px;">
  <h3 style="margin-top: 0;">Token Specifications</h3>
  <div style="display: grid; grid-template-columns: 1fr 2fr; gap: 10px;">
    <div><strong>Name:</strong></div>
    <div>Cirqa Token</div>
    <div><strong>Symbol:</strong></div>
    <div>CIRQA</div>
    <div><strong>Max Supply:</strong></div>
    <div>10,000,000,000</div>
    <div><strong>Decimals:</strong></div>
    <div>18</div>
    <div><strong>Contract Standard:</strong></div>
    <div>ERC20</div>
  </div>
</div>

### Key Features

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-bottom: 20px;">
  <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1);">
    <h4 style="margin-top: 0; color: #3498db;">ERC20Burnable</h4>
    <p>Allows token holders to burn their tokens, permanently removing them from circulation and reducing the total supply.</p>
    <pre style="background-color: #f8f9fa; padding: 10px; border-radius: 4px; font-size: 0.9em;">function burn(uint256 amount) external</pre>
  </div>
  <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1);">
    <h4 style="margin-top: 0; color: #3498db;">Ownable</h4>
    <p>The contract has an owner with administrative privileges for protocol governance and parameter updates.</p>
    <pre style="background-color: #f8f9fa; padding: 10px; border-radius: 4px; font-size: 0.9em;">function transferOwnership(address newOwner) external onlyOwner</pre>
  </div>
  <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1);">
    <h4 style="margin-top: 0; color: #3498db;">Minting Control</h4>
    <p>Only the designated minter address can mint new tokens, up to the MAX_SUPPLY limit.</p>
    <pre style="background-color: #f8f9fa; padding: 10px; border-radius: 4px; font-size: 0.9em;">function setMinter(address _minter) external onlyOwner
function mint(address to, uint256 amount) external onlyMinter</pre>
  </div>
</div>

## CirqaProtocol

<div class="cirqa-note">
  <p>The <code>CirqaProtocol</code> contract is the core of the lending and borrowing functionality, managing all user positions, asset markets, and reward distributions.</p>
</div>

### Data Structures

<div style="display: flex; flex-direction: column; gap: 20px; margin: 20px 0;">
  <div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
    <h4 style="margin-top: 0; color: #2c3e50;">UserInfo Struct</h4>
    <p>Stores user-specific data for each asset:</p>
    
    ```solidity
struct UserInfo {
    uint256 supplied;      // Amount of asset supplied
    uint256 borrowed;      // Amount of asset borrowed
    uint256 rewardDebt;    // For calculating rewards
    bool useAsCollateral;  // If asset is used as collateral
}
    ```
    
    <div style="background-color: #e8f4fc; padding: 10px; border-radius: 4px; margin-top: 10px;">
      <p style="margin: 0;"><strong>Usage:</strong> Mapped to each user address and asset index in the protocol.</p>
      <p style="margin: 5px 0 0;"><code>mapping(address => mapping(uint256 => UserInfo)) public userInfo;</code></p>
    </div>
  </div>
  
  <div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
    <h4 style="margin-top: 0; color: #2c3e50;">AssetInfo Struct</h4>
    <p>Stores information about each supported asset market:</p>
    
    ```solidity
struct AssetInfo {
    IERC20 asset;            // Token address
    uint256 allocPoint;      // Allocation points for rewards
    uint256 lastRewardTime;  // Last reward distribution time
    uint256 accCirqaPerShare; // Accumulated rewards per share
    uint256 totalPoints;     // Total points (supply + borrow)
    uint256 totalSupplied;   // Total supplied amount
    uint256 totalBorrowed;   // Total borrowed amount
}
    ```
    
    <div style="background-color: #e8f4fc; padding: 10px; border-radius: 4px; margin-top: 10px;">
      <p style="margin: 0;"><strong>Storage:</strong> Stored in an array to track all supported assets.</p>
      <p style="margin: 5px 0 0;"><code>AssetInfo[] public assetInfo;</code></p>
    </div>
  </div>
</div>

### Protocol State Variables

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 15px; margin: 20px 0;">
  <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1);">
    <h4 style="margin-top: 0; color: #3498db;">Reward Parameters</h4>
    <ul>
      <li><code>cirqaToken</code>: CIRQA token address</li>
      <li><code>cirqaPerSecond</code>: Emission rate</li>
      <li><code>totalAllocPoint</code>: Sum of all allocation points</li>
    </ul>
  </div>
  <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1);">
    <h4 style="margin-top: 0; color: #3498db;">Fee Configuration</h4>
    <ul>
      <li><code>protocolFeeBps</code>: Fee in basis points</li>
      <li><code>protocolFeeRecipient</code>: Fee recipient address</li>
    </ul>
  </div>
  <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1);">
    <h4 style="margin-top: 0; color: #3498db;">External Dependencies</h4>
    <ul>
      <li><code>oracle</code>: Price oracle interface</li>
      <li><code>interestModel</code>: Interest rate model</li>
    </ul>
  </div>
</div>

### Core Logic

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin: 20px 0;">
  <div style="background-color: #e8f6f3; padding: 20px; border-radius: 8px;">
    <h4 style="margin-top: 0; color: #16a085;">Lending & Borrowing</h4>
    <p>Core functions that enable users to interact with the protocol:</p>
    <ul>
      <li><code>supply(uint256 _pid, uint256 _amount)</code>: Supply assets to the protocol</li>
      <li><code>withdraw(uint256 _pid, uint256 _amount)</code>: Withdraw supplied assets</li>
      <li><code>borrow(uint256 _pid, uint256 _amount)</code>: Borrow assets against collateral</li>
      <li><code>repay(uint256 _pid, uint256 _amount)</code>: Repay borrowed assets</li>
    </ul>
  </div>
  
  <div style="background-color: #eaf2f8; padding: 20px; border-radius: 8px;">
    <h4 style="margin-top: 0; color: #2980b9;">Collateral Management</h4>
    <p>Users can manage which assets serve as collateral:</p>
    <ul>
      <li><code>setCollateralStatus(uint256 _pid, bool _useAsCollateral)</code>: Enable or disable an asset as collateral</li>
      <li>Assets used as collateral increase borrowing capacity</li>
      <li>Each asset has a collateral factor determining its borrowing power</li>
    </ul>
  </div>
  
  <div style="background-color: #fef9e7; padding: 20px; border-radius: 8px;">
    <h4 style="margin-top: 0; color: #f39c12;">Reward Distribution</h4>
    <p>The protocol distributes CIRQA tokens as rewards:</p>
    <ul>
      <li><code>pendingCirqa(uint256 _pid, address _user)</code>: Calculate pending rewards</li>
      <li><code>updatePool(uint256 _pid)</code>: Update reward variables for an asset</li>
      <li>Rewards are distributed based on allocation points and user activity</li>
      <li>Both suppliers and borrowers earn rewards</li>
    </ul>
  </div>
  
  <div style="background-color: #f8f5fd; padding: 20px; border-radius: 8px;">
    <h4 style="margin-top: 0; color: #8e44ad;">Fee Mechanism</h4>
    <p>Protocol fees are collected on borrowing activities:</p>
    <ul>
      <li>Fee percentage is set in basis points (1/100 of 1%)</li>
      <li>Fees are taken from borrowed amounts</li>
      <li>Collected fees are sent to the protocol fee recipient</li>
      <li>Fees can be adjusted by governance</li>
    </ul>
  </div>
</div>

### Admin Functions

<div class="cirqa-highlight">
  <p>The contract owner has several administrative functions to manage the protocol:</p>
  
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 15px; margin-top: 15px;">
    <div>
      <h4 style="margin-top: 0;">Fee Management</h4>
      <ul>
        <li><code>setProtocolFee(uint256 _protocolFeeBps)</code></li>
        <li><code>setProtocolFeeRecipient(address _protocolFeeRecipient)</code></li>
      </ul>
    </div>
    <div>
      <h4 style="margin-top: 0;">Reward Configuration</h4>
      <ul>
        <li><code>updateCirqaPerSecond(uint256 _cirqaPerSecond)</code></li>
      </ul>
    </div>
    <div>
      <h4 style="margin-top: 0;">Asset Management</h4>
      <ul>
        <li><code>add(uint256 _allocPoint, IERC20 _asset)</code></li>
        <li><code>set(uint256 _pid, uint256 _allocPoint)</code></li>
      </ul>
    </div>
  </div>
</div>

## InterestModel

<div class="cirqa-note">
  <p>The <code>InterestModel</code> contract calculates interest rates for lending and borrowing based on utilization rate.</p>
</div>

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin: 20px 0;">
  <h3 style="margin-top: 0;">Interest Rate Curve</h3>
  
  <div style="display: flex; justify-content: center; margin: 20px 0;">
    <div style="background-color: white; padding: 20px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05); max-width: 500px;">
      <pre style="margin: 0; overflow: auto;">
Interest Rate
    ^
    │                                   /
    │                                  /
    │                                 /
    │                                /
    │                               /
    │                              /
    │                             /
    │                   _________/
    │                  /
    │                 /
    │                /
    │               /
    │              /
    │             /
    │            /
    │___________/
    │
    └─────────────────────────────────────► Utilization
         baseRate    optimalRate    maxRate
      </pre>
    </div>
  </div>
  
  <p>The interest rate model uses the following parameters:</p>
  <ul>
    <li><strong>Base Rate</strong>: Minimum interest rate when utilization is 0%</li>
    <li><strong>Optimal Utilization Rate</strong>: Target utilization for the protocol</li>
    <li><strong>Slope1</strong>: Rate increase below optimal utilization</li>
    <li><strong>Slope2</strong>: Rate increase above optimal utilization (steeper)</li>
  </ul>
  
  <div style="background-color: #e8f4fc; padding: 15px; border-radius: 4px; margin-top: 15px;">
    <p style="margin: 0;"><strong>Formula:</strong></p>
    <p style="margin: 5px 0 0;">If utilization ≤ optimalUtilization:<br>
    rate = baseRate + (utilization / optimalUtilization) * slope1</p>
    <p style="margin: 5px 0 0;">If utilization > optimalUtilization:<br>
    rate = baseRate + slope1 + ((utilization - optimalUtilization) / (1 - optimalUtilization)) * slope2</p>
  </div>
</div>

## CirqaOracle

<div class="cirqa-note">
  <p>The <code>CirqaOracle</code> contract provides price data for assets in the protocol, enabling accurate valuation of collateral and borrowed positions.</p>
</div>

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin: 20px 0;">
  <h3 style="margin-top: 0;">Oracle Features</h3>
  
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 15px;">
    <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <h4 style="margin-top: 0; color: #3498db;">Price Feeds</h4>
      <ul>
        <li>Integration with Chainlink price feeds</li>
        <li>Fallback price sources for redundancy</li>
        <li>Support for multiple base currencies</li>
      </ul>
    </div>
    <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <h4 style="margin-top: 0; color: #3498db;">Admin Controls</h4>
      <ul>
        <li>Add/update price sources for assets</li>
        <li>Set heartbeat thresholds for staleness checks</li>
        <li>Configure price deviation tolerances</li>
      </ul>
    </div>
    <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <h4 style="margin-top: 0; color: #3498db;">Safety Features</h4>
      <ul>
        <li>Staleness checks for price data</li>
        <li>Circuit breakers for extreme price movements</li>
        <li>Governance-controlled emergency functions</li>
      </ul>
    </div>
  </div>
</div>

---

<div style="text-align: center; margin: 30px 0;">
  <a href="https://github.com/cirqa/contracts" style="display: inline-block; background-color: #3498db; color: white; padding: 10px 20px; border-radius: 4px; text-decoration: none; margin-right: 10px;">View on GitHub</a>
  <a href="../contracts/README.html" style="display: inline-block; background-color: #2c3e50; color: white; padding: 10px 20px; border-radius: 4px; text-decoration: none;">Back to Contracts</a>
</div>