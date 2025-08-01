# Cirqa Application

<div align="center">
  <img src="../assets/images/icons/rewards.svg" alt="Application Icon" width="80" height="80">
  <p><em>Complete User Guide for the Cirqa DeFi Lending Platform</em></p>
</div>

## Application Overview

<div class="cirqa-highlight">
  <p>The Cirqa application provides a comprehensive interface for interacting with the Cirqa lending protocol. This guide walks through the main features and how to use them effectively.</p>
</div>

## Getting Started

### Connecting Your Wallet

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin: 20px 0;">
  <h3 style="margin-top: 0;">Supported Wallets</h3>
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 15px;">
    <div style="background-color: white; padding: 15px; border-radius: 8px; text-align: center; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <div style="font-weight: bold; margin-bottom: 10px;">MetaMask</div>
      <div style="color: #6c757d; font-size: 0.9em;">Most popular Ethereum wallet</div>
    </div>
    <div style="background-color: white; padding: 15px; border-radius: 8px; text-align: center; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <div style="font-weight: bold; margin-bottom: 10px;">WalletConnect</div>
      <div style="color: #6c757d; font-size: 0.9em;">Connect with mobile wallets</div>
    </div>
    <div style="background-color: white; padding: 15px; border-radius: 8px; text-align: center; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <div style="font-weight: bold; margin-bottom: 10px;">Coinbase Wallet</div>
      <div style="color: #6c757d; font-size: 0.9em;">User-friendly option</div>
    </div>
    <div style="background-color: white; padding: 15px; border-radius: 8px; text-align: center; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <div style="font-weight: bold; margin-bottom: 10px;">Keplr</div>
      <div style="color: #6c757d; font-size: 0.9em;">KiiChain native wallet</div>
    </div>
  </div>
  
  <div style="margin-top: 20px;">
    <p><strong>To connect your wallet:</strong></p>
    <ol>
      <li>Click the "Connect Wallet" button in the top-right corner of the application</li>
      <li>Select your preferred wallet from the available options</li>
      <li>Follow the prompts in your wallet to approve the connection</li>
      <li>Once connected, your wallet address will appear in the header</li>
    </ol>
  </div>
</div>

## Main Features

### Dashboard

<div class="cirqa-note">
  <p>The Dashboard is your central hub for monitoring your positions and overall account health.</p>
</div>

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin: 20px 0;">
  <h3 style="margin-top: 0;">Dashboard Components</h3>
  
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px;">
    <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <h4 style="margin-top: 0; color: #3498db;">Account Summary</h4>
      <ul>
        <li><strong>Net Worth</strong>: Total value of supplied assets minus borrowed assets</li>
        <li><strong>Health Factor</strong>: Indicator of your position's safety</li>
        <li><strong>Available Borrowing Power</strong>: How much more you can borrow</li>
      </ul>
    </div>
    
    <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <h4 style="margin-top: 0; color: #3498db;">Supplied Assets</h4>
      <ul>
        <li>List of all assets you've supplied to the protocol</li>
        <li>Current balance and USD value for each asset</li>
        <li>APY earned on each supplied asset</li>
        <li>Collateral status toggle for each asset</li>
      </ul>
    </div>
    
    <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <h4 style="margin-top: 0; color: #3498db;">Borrowed Assets</h4>
      <ul>
        <li>List of all assets you've borrowed from the protocol</li>
        <li>Current borrowed amount and USD value</li>
        <li>APY paid on each borrowed asset</li>
        <li>Percentage of your total borrow limit used</li>
      </ul>
    </div>
    
    <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <h4 style="margin-top: 0; color: #3498db;">Rewards</h4>
      <ul>
        <li>CIRQA tokens earned from supplying and borrowing</li>
        <li>Claim button for harvesting rewards</li>
        <li>Historical rewards chart</li>
      </ul>
    </div>
  </div>
</div>

### Markets

<div class="cirqa-note">
  <p>The Markets page displays all available assets for lending and borrowing, along with their current rates and market sizes.</p>
</div>

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin: 20px 0;">
  <h3 style="margin-top: 0;">Market Information</h3>
  
  <div style="overflow-x: auto; margin-top: 20px;">
    <table style="width: 100%; border-collapse: collapse; background-color: white; border-radius: 8px; overflow: hidden;">
      <thead>
        <tr style="background-color: #f1f3f5;">
          <th style="padding: 12px 15px; text-align: left;">Asset</th>
          <th style="padding: 12px 15px; text-align: right;">Supply APY</th>
          <th style="padding: 12px 15px; text-align: right;">Borrow APY</th>
          <th style="padding: 12px 15px; text-align: right;">Total Supply</th>
          <th style="padding: 12px 15px; text-align: right;">Total Borrow</th>
          <th style="padding: 12px 15px; text-align: right;">Utilization</th>
        </tr>
      </thead>
      <tbody>
        <tr style="border-top: 1px solid #e9ecef;">
          <td style="padding: 12px 15px;">USDC</td>
          <td style="padding: 12px 15px; text-align: right; color: #27ae60;">4.5%</td>
          <td style="padding: 12px 15px; text-align: right; color: #e74c3c;">6.2%</td>
          <td style="padding: 12px 15px; text-align: right;">$10.5M</td>
          <td style="padding: 12px 15px; text-align: right;">$7.2M</td>
          <td style="padding: 12px 15px; text-align: right;">68%</td>
        </tr>
        <tr style="border-top: 1px solid #e9ecef;">
          <td style="padding: 12px 15px;">ETH</td>
          <td style="padding: 12px 15px; text-align: right; color: #27ae60;">3.2%</td>
          <td style="padding: 12px 15px; text-align: right; color: #e74c3c;">4.8%</td>
          <td style="padding: 12px 15px; text-align: right;">$15.3M</td>
          <td style="padding: 12px 15px; text-align: right;">$9.1M</td>
          <td style="padding: 12px 15px; text-align: right;">59%</td>
        </tr>
        <tr style="border-top: 1px solid #e9ecef;">
          <td style="padding: 12px 15px;">BTC</td>
          <td style="padding: 12px 15px; text-align: right; color: #27ae60;">2.8%</td>
          <td style="padding: 12px 15px; text-align: right; color: #e74c3c;">4.1%</td>
          <td style="padding: 12px 15px; text-align: right;">$22.7M</td>
          <td style="padding: 12px 15px; text-align: right;">$12.5M</td>
          <td style="padding: 12px 15px; text-align: right;">55%</td>
        </tr>
      </tbody>
    </table>
  </div>
  
  <div style="margin-top: 20px;">
    <p><strong>Actions available from the Markets page:</strong></p>
    <ul>
      <li>Click on any asset to view detailed market information</li>
      <li>Use the "Supply" button to lend your assets to the protocol</li>
      <li>Use the "Borrow" button to take out a loan against your collateral</li>
    </ul>
  </div>
</div>

## Core Operations

### Supplying Assets

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin: 20px 0;">
  <div style="background-color: #e8f6f3; padding: 20px; border-radius: 8px;">
    <h3 style="margin-top: 0; color: #16a085;">How to Supply</h3>
    <ol>
      <li>Navigate to the Markets page or Dashboard</li>
      <li>Find the asset you want to supply and click "Supply"</li>
      <li>Enter the amount you wish to supply</li>
      <li>Review the transaction details</li>
      <li>Confirm the transaction in your wallet</li>
      <li>Once confirmed, your supplied assets will appear in your Dashboard</li>
    </ol>
  </div>
  
  <div style="background-color: #e8f6f3; padding: 20px; border-radius: 8px;">
    <h3 style="margin-top: 0; color: #16a085;">Benefits of Supplying</h3>
    <ul>
      <li><strong>Earn Interest</strong>: Receive APY on your supplied assets</li>
      <li><strong>Earn CIRQA</strong>: Get additional rewards in CIRQA tokens</li>
      <li><strong>Borrowing Power</strong>: Use your supplied assets as collateral for loans</li>
      <li><strong>Liquidity</strong>: Withdraw your assets at any time (subject to availability)</li>
    </ul>
  </div>
</div>

### Borrowing Assets

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin: 20px 0;">
  <div style="background-color: #eaf2f8; padding: 20px; border-radius: 8px;">
    <h3 style="margin-top: 0; color: #2980b9;">How to Borrow</h3>
    <ol>
      <li>First, supply assets and enable them as collateral</li>
      <li>Navigate to the Markets page or Dashboard</li>
      <li>Find the asset you want to borrow and click "Borrow"</li>
      <li>Enter the amount you wish to borrow (up to your borrowing limit)</li>
      <li>Review the transaction details and health factor impact</li>
      <li>Confirm the transaction in your wallet</li>
      <li>Once confirmed, your borrowed assets will appear in your Dashboard</li>
    </ol>
  </div>
  
  <div style="background-color: #eaf2f8; padding: 20px; border-radius: 8px;">
    <h3 style="margin-top: 0; color: #2980b9;">Important Considerations</h3>
    <ul>
      <li><strong>Health Factor</strong>: Keep your health factor above 1 to avoid liquidation</li>
      <li><strong>Variable Interest</strong>: Borrow rates may change based on market conditions</li>
      <li><strong>Collateral Requirements</strong>: Different assets have different collateral factors</li>
      <li><strong>Liquidation Risk</strong>: If your health factor drops below 1, your collateral may be liquidated</li>
    </ul>
  </div>
</div>

## Advanced Features

### Collateral Management

<div class="cirqa-note">
  <p>Effectively managing your collateral is crucial for maintaining a healthy position and maximizing your borrowing power.</p>
</div>

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin: 20px 0;">
  <h3 style="margin-top: 0;">Collateral Strategies</h3>
  
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px;">
    <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <h4 style="margin-top: 0; color: #3498db;">Diversification</h4>
      <p>Spread your collateral across multiple assets to reduce risk from price volatility in any single asset.</p>
    </div>
    
    <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <h4 style="margin-top: 0; color: #3498db;">Stablecoin Focus</h4>
      <p>Use stablecoins as primary collateral to minimize volatility and maintain a more predictable health factor.</p>
    </div>
    
    <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <h4 style="margin-top: 0; color: #3498db;">Safety Buffer</h4>
      <p>Maintain a health factor well above 1 (ideally 1.5 or higher) to provide a buffer against market volatility.</p>
    </div>
  </div>
</div>

### Rewards and Governance

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin: 20px 0;">
  <h3 style="margin-top: 0;">CIRQA Token Utility</h3>
  
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px;">
    <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <h4 style="margin-top: 0; color: #3498db;">Rewards</h4>
      <p>Earn CIRQA tokens for supplying and borrowing assets. Rewards are distributed continuously and can be claimed at any time.</p>
    </div>
    
    <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <h4 style="margin-top: 0; color: #3498db;">Governance</h4>
      <p>CIRQA holders can vote on protocol proposals, including parameter changes, new asset listings, and protocol upgrades.</p>
    </div>
    
    <div style="background-color: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
      <h4 style="margin-top: 0; color: #3498db;">Staking</h4>
      <p>Stake CIRQA tokens to earn additional rewards and boost your voting power in governance decisions.</p>
    </div>
  </div>
</div>

## Security Best Practices

<div class="cirqa-highlight">
  <h3>Protecting Your Assets</h3>
  <ul>
    <li><strong>Never share your private keys or seed phrases</strong> with anyone, including Cirqa team members</li>
    <li><strong>Always verify transaction details</strong> before confirming in your wallet</li>
    <li><strong>Use hardware wallets</strong> for additional security when dealing with large amounts</li>
    <li><strong>Monitor your health factor</strong> regularly to avoid liquidation</li>
    <li><strong>Set up notifications</strong> for important events like health factor warnings</li>
    <li><strong>Diversify your collateral</strong> to reduce risk from price volatility</li>
  </ul>
</div>

---

<div style="text-align: center; margin: 30px 0;">
  <a href="https://app.cirqa.io" style="display: inline-block; background-color: #3498db; color: white; padding: 10px 20px; border-radius: 4px; text-decoration: none; margin-right: 10px;">Launch App</a>
  <a href="./components.md" style="display: inline-block; background-color: #2c3e50; color: white; padding: 10px 20px; border-radius: 4px; text-decoration: none;">View Components</a>
</div>