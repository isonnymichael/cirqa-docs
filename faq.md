# Frequently Asked Questions

<div align="center">
  <img src="./assets/images/icons/rewards.svg" alt="FAQ Icon" width="80" height="80">
  <p><em>Answers to Common Questions About the Cirqa Protocol</em></p>
</div>

## General Questions

<div class="cirqa-highlight">
  <h3>What is Cirqa?</h3>
  <p>Cirqa is a decentralized borrowing and lending protocol built on the KiiChain blockchain. It allows users to supply assets to earn interest, borrow against their collateral, and participate in protocol governance through the CIRQA token.</p>
</div>

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin: 20px 0;">
  <h3 style="margin-top: 0;">Frequently Asked Questions</h3>
  
  <div style="margin-top: 20px;">
    <h4 style="color: #3498db;">How does Cirqa differ from other lending protocols?</h4>
    <p>Cirqa is specifically designed for the KiiChain ecosystem, focusing on tokenized real-world assets (RWAs) as collateral. It features a unique interest rate model optimized for stability and predictability, along with a governance system that gives CIRQA token holders significant control over protocol parameters.</p>
  </div>
  
  <div style="margin-top: 20px;">
    <h4 style="color: #3498db;">Is Cirqa secure?</h4>
    <p>Yes, security is our top priority. The Cirqa protocol has undergone multiple independent security audits, implements formal verification for critical components, and maintains an active bug bounty program. All smart contracts are open-source and have been thoroughly tested.</p>
  </div>
  
  <div style="margin-top: 20px;">
    <h4 style="color: #3498db;">What blockchain does Cirqa run on?</h4>
    <p>Cirqa is built on the KiiChain blockchain, which provides fast transaction speeds, low fees, and native support for tokenized real-world assets.</p>
  </div>
</div>

## Using Cirqa

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin: 20px 0;">
  <div style="margin-top: 0px;">
    <h4 style="color: #3498db;">How do I get started with Cirqa?</h4>
    <p>To get started:</p>
    <ol>
      <li>Visit <a href="https://app.cirqa.io">app.cirqa.io</a></li>
      <li>Connect your wallet (MetaMask, WalletConnect, or Keplr)</li>
      <li>Ensure you have KiiChain tokens for transaction fees</li>
      <li>Supply assets to start earning interest</li>
      <li>Optionally enable your supplied assets as collateral to borrow</li>
    </ol>
  </div>
  
  <div style="margin-top: 20px;">
    <h4 style="color: #3498db;">What assets can I supply and borrow?</h4>
    <p>Cirqa supports a variety of assets including:</p>
    <ul>
      <li>Major cryptocurrencies (BTC, ETH)</li>
      <li>Stablecoins (USDC, USDT, DAI)</li>
      <li>Tokenized real-world assets (RWAs)</li>
      <li>KiiChain native tokens</li>
    </ul>
    <p>The available assets are displayed on the Markets page of the application.</p>
  </div>
  
  <div style="margin-top: 20px;">
    <h4 style="color: #3498db;">How are interest rates determined?</h4>
    <p>Interest rates in Cirqa are determined algorithmically based on the utilization rate of each asset pool. The utilization rate is the ratio of borrowed assets to supplied assets. As utilization increases, both supply and borrow interest rates increase. This dynamic adjustment helps maintain liquidity in the protocol.</p>
  </div>
</div>

## Collateral and Borrowing

<div class="cirqa-note">
  <h3>Understanding Collateral</h3>
  <p>Cirqa uses an overcollateralized lending model, meaning you must supply more value than you borrow. This protects the protocol and other users from default risk.</p>
</div>

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin: 20px 0;">
  <div style="margin-top: 0px;">
    <h4 style="color: #3498db;">What is a collateral factor?</h4>
    <p>The collateral factor determines how much you can borrow against a particular asset. For example, if an asset has a collateral factor of 75%, you can borrow up to 75% of its value. Different assets have different collateral factors based on their risk profile, with stablecoins typically having higher factors than volatile cryptocurrencies.</p>
  </div>
  
  <div style="margin-top: 20px;">
    <h4 style="color: #3498db;">What is the health factor?</h4>
    <p>The health factor is a numerical representation of the safety of your borrowed position relative to your collateral. It's calculated as:</p>
    <div style="background-color: #e8f4fc; padding: 15px; border-radius: 4px; margin-top: 10px;">
      <p style="margin: 0; text-align: center;"><strong>Health Factor = (Collateral Value × Collateral Factor) ÷ Borrowed Value</strong></p>
    </div>
    <p style="margin-top: 10px;">A health factor below 1 triggers liquidation. It's recommended to maintain a health factor of at least 1.5 to provide a safety buffer against market volatility.</p>
  </div>
  
  <div style="margin-top: 20px;">
    <h4 style="color: #3498db;">What happens if I get liquidated?</h4>
    <p>If your health factor drops below 1 due to collateral value decreasing or borrowed value increasing, your position becomes eligible for liquidation. During liquidation:</p>
    <ul>
      <li>Liquidators repay a portion of your borrowed amount</li>
      <li>In return, they receive an equivalent amount of your collateral plus a liquidation penalty</li>
      <li>The liquidation continues until your health factor returns above 1</li>
    </ul>
    <p>To avoid liquidation, monitor your health factor regularly and maintain a safe buffer by either supplying more collateral or repaying part of your borrowed amount.</p>
  </div>
</div>

## CIRQA Token and Governance

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin: 20px 0;">
  <div style="margin-top: 0px;">
    <h4 style="color: #3498db;">What is the CIRQA token used for?</h4>
    <p>The CIRQA token serves multiple purposes in the ecosystem:</p>
    <ul>
      <li><strong>Governance</strong>: Vote on protocol proposals and parameter changes</li>
      <li><strong>Rewards</strong>: Earned by users who supply and borrow assets</li>
      <li><strong>Staking</strong>: Stake CIRQA to earn additional rewards and boost voting power</li>
      <li><strong>Protocol Fee Discounts</strong>: CIRQA holders may receive discounts on protocol fees</li>
    </ul>
  </div>
  
  <div style="margin-top: 20px;">
    <h4 style="color: #3498db;">How do I participate in governance?</h4>
    <p>To participate in Cirqa governance:</p>
    <ol>
      <li>Hold CIRQA tokens in your wallet</li>
      <li>Visit the Governance section of the application</li>
      <li>Browse active proposals</li>
      <li>Cast your vote by signing a transaction with your wallet</li>
      <li>Optionally, create new proposals if you meet the minimum token requirement</li>
    </ol>
  </div>
  
  <div style="margin-top: 20px;">
    <h4 style="color: #3498db;">How are CIRQA rewards distributed?</h4>
    <p>CIRQA rewards are distributed continuously based on your activity in the protocol:</p>
    <ul>
      <li>Suppliers earn rewards proportional to their supplied amount and the asset's allocation points</li>
      <li>Borrowers also earn rewards proportional to their borrowed amount</li>
      <li>Rewards accumulate in real-time and can be claimed at any time</li>
      <li>The reward rate (CIRQA per second) and allocation points are adjustable through governance</li>
    </ul>
  </div>
</div>

## Technical Questions

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin: 20px 0;">
  <div style="margin-top: 0px;">
    <h4 style="color: #3498db;">How does Cirqa determine asset prices?</h4>
    <p>Cirqa uses a robust oracle system to determine asset prices:</p>
    <ul>
      <li>Primary price feeds come from Chainlink oracles</li>
      <li>Backup price sources provide redundancy</li>
      <li>Time-weighted average prices (TWAP) help prevent manipulation</li>
      <li>Circuit breakers protect against extreme price movements</li>
    </ul>
  </div>
  
  <div style="margin-top: 20px;">
    <h4 style="color: #3498db;">What are the protocol fees?</h4>
    <p>Cirqa charges a small protocol fee on borrowed amounts. This fee:</p>
    <ul>
      <li>Is currently set at 10% of the interest paid by borrowers</li>
      <li>Goes to the protocol treasury, which is controlled by governance</li>
      <li>Can be adjusted through governance proposals</li>
      <li>Helps fund protocol development, security audits, and insurance reserves</li>
    </ul>
  </div>
  
  <div style="margin-top: 20px;">
    <h4 style="color: #3498db;">Can I integrate Cirqa into my application?</h4>
    <p>Yes, Cirqa is designed to be easily integrated into other applications. We provide:</p>
    <ul>
      <li>Comprehensive API documentation</li>
      <li>JavaScript SDK for frontend integration</li>
      <li>Solidity interfaces for smart contract integration</li>
      <li>GraphQL endpoints for data queries</li>
    </ul>
    <p>Visit our <a href="https://docs.cirqa.io/developers">Developer Documentation</a> for more information.</p>
  </div>
</div>

## Support and Community

<div class="cirqa-highlight">
  <h3>Getting Help</h3>
  <p>If you have questions or need assistance, there are several ways to get help:</p>
  <ul>
    <li><strong>Discord Community</strong>: Join our <a href="https://discord.gg/cirqa">Discord server</a> for real-time support</li>
    <li><strong>Forum</strong>: Post questions on our <a href="https://community.cirqa.io">Community Forum</a></li>
    <li><strong>Twitter</strong>: Follow us <a href="https://twitter.com/cirqaprotocol">@cirqaprotocol</a> for updates</li>
    <li><strong>Email Support</strong>: Contact <a href="mailto:support@cirqa.io">support@cirqa.io</a> for private inquiries</li>
  </ul>
</div>

---

<div style="text-align: center; margin: 30px 0;">
  <p>Didn't find what you're looking for? Ask in our community channels!</p>
  <a href="https://discord.gg/cirqa" style="display: inline-block; background-color: #3498db; color: white; padding: 10px 20px; border-radius: 4px; text-decoration: none; margin-right: 10px;">Join Discord</a>
  <a href="https://community.cirqa.io" style="display: inline-block; background-color: #2c3e50; color: white; padding: 10px 20px; border-radius: 4px; text-decoration: none;">Visit Forum</a>
</div>