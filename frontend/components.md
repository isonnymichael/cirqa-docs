# Frontend Components

<div align="center">
  <img src="../assets/images/icons/borrowing.svg" alt="Borrowing Icon" width="80" height="80">
  <p><em>Reusable UI Components Powering the Cirqa Interface</em></p>
</div>

## Overview

The Cirqa frontend is built with React, TypeScript, and Material-UI. This page provides a detailed overview of the main components used throughout the application. These components are designed to be reusable, accessible, and consistent with the Cirqa design system.

## Core Components

<div class="cirqa-highlight">
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px;">
    <div>
      <h3>🧭 Navigation</h3>
      <ul>
        <li><code>Header</code> - Main navigation bar with wallet connection</li>
        <li><code>Sidebar</code> - Collapsible side navigation with main sections</li>
        <li><code>Footer</code> - Contains links to resources and social media</li>
        <li><code>Breadcrumbs</code> - Shows current location in the app</li>
      </ul>
    </div>
    <div>
      <h3>📊 Data Display</h3>
      <ul>
        <li><code>AssetCard</code> - Displays asset information and actions</li>
        <li><code>MarketTable</code> - Shows available markets and rates</li>
        <li><code>PositionSummary</code> - Overview of user's positions</li>
        <li><code>TransactionHistory</code> - List of user transactions</li>
      </ul>
    </div>
    <div>
      <h3>🔄 Interactions</h3>
      <ul>
        <li><code>SupplyModal</code> - Interface for supplying assets</li>
        <li><code>BorrowModal</code> - Interface for borrowing assets</li>
        <li><code>RepayModal</code> - Interface for repaying loans</li>
        <li><code>WithdrawModal</code> - Interface for withdrawing assets</li>
      </ul>
    </div>
  </div>
</div>

## Component Showcase

### Header Component

```jsx
<Header>
  <Logo />
  <Navigation>
    <NavItem to="/markets">Markets</NavItem>
    <NavItem to="/dashboard">Dashboard</NavItem>
    <NavItem to="/rewards">Rewards</NavItem>
  </Navigation>
  <WalletConnect />
</Header>
```

<div style="background-color: #f8f9fa; padding: 15px; border-radius: 5px; margin: 20px 0;">
  <div style="display: flex; justify-content: space-between; align-items: center;">
    <div style="font-weight: bold; color: #2c3e50;">CIRQA</div>
    <div style="display: flex; gap: 20px;">
      <span>Markets</span>
      <span>Dashboard</span>
      <span>Rewards</span>
    </div>
    <div style="background-color: #3498db; color: white; padding: 8px 16px; border-radius: 4px;">Connect Wallet</div>
  </div>
</div>

### AssetCard Component

```jsx
<AssetCard
  asset="USDC"
  icon="/assets/usdc.png"
  balance="1,000.00"
  value="$1,000.00"
  apy="4.5%"
  onSupply={() => openSupplyModal('USDC')}
  onBorrow={() => openBorrowModal('USDC')}
/>
```

<div style="background-color: white; border-radius: 8px; padding: 20px; box-shadow: 0 2px 10px rgba(0,0,0,0.05); margin: 20px 0;">
  <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px;">
    <div style="display: flex; align-items: center; gap: 10px;">
      <div style="background-color: #2775ca; color: white; width: 40px; height: 40px; border-radius: 50%; display: flex; justify-content: center; align-items: center;">USDC</div>
      <div>
        <div style="font-weight: bold;">USD Coin</div>
        <div style="color: #6c757d; font-size: 0.9em;">USDC</div>
      </div>
    </div>
    <div>
      <div style="font-weight: bold;">1,000.00</div>
      <div style="color: #6c757d; font-size: 0.9em;">$1,000.00</div>
    </div>
  </div>
  <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px;">
    <div>APY</div>
    <div style="font-weight: bold; color: #27ae60;">4.5%</div>
  </div>
  <div style="display: flex; gap: 10px;">
    <div style="background-color: #3498db; color: white; padding: 8px 16px; border-radius: 4px; flex: 1; text-align: center;">Supply</div>
    <div style="background-color: #2c3e50; color: white; padding: 8px 16px; border-radius: 4px; flex: 1; text-align: center;">Borrow</div>
  </div>
</div>

## Page Components

<div class="cirqa-note">
  <h3>Main Application Pages</h3>
  <p>The Cirqa application consists of several key pages, each built from the core components:</p>
</div>

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin: 20px 0;">
  <div style="background-color: #e6f7ff; padding: 20px; border-radius: 5px;">
    <h3>Dashboard Page</h3>
    <p>Provides an overview of the user's positions, including supplied assets, borrowed assets, and available rewards.</p>
    <p><strong>Key Components:</strong></p>
    <ul>
      <li><code>PositionSummary</code></li>
      <li><code>AssetList</code></li>
      <li><code>RewardsPanel</code></li>
    </ul>
  </div>
  <div style="background-color: #e6f7ff; padding: 20px; border-radius: 5px;">
    <h3>Markets Page</h3>
    <p>Displays all available markets with current interest rates, total supply, and total borrow amounts.</p>
    <p><strong>Key Components:</strong></p>
    <ul>
      <li><code>MarketTable</code></li>
      <li><code>MarketStats</code></li>
      <li><code>FilterControls</code></li>
    </ul>
  </div>
  <div style="background-color: #e6f7ff; padding: 20px; border-radius: 5px;">
    <h3>Asset Details Page</h3>
    <p>Shows detailed information about a specific asset, including historical data and current market conditions.</p>
    <p><strong>Key Components:</strong></p>
    <ul>
      <li><code>AssetHeader</code></li>
      <li><code>InterestChart</code></li>
      <li><code>MarketActions</code></li>
    </ul>
  </div>
</div>

## Design System

The Cirqa frontend uses a consistent design system with the following key elements:

<div style="display: flex; flex-wrap: wrap; gap: 20px; margin: 20px 0;">
  <div style="flex: 1; min-width: 200px;">
    <h3>Colors</h3>
    <div style="display: flex; flex-direction: column; gap: 10px;">
      <div style="background-color: #2c3e50; color: white; padding: 10px; border-radius: 4px;">Primary: #2c3e50</div>
      <div style="background-color: #3498db; color: white; padding: 10px; border-radius: 4px;">Secondary: #3498db</div>
      <div style="background-color: #27ae60; color: white; padding: 10px; border-radius: 4px;">Success: #27ae60</div>
      <div style="background-color: #e74c3c; color: white; padding: 10px; border-radius: 4px;">Error: #e74c3c</div>
      <div style="background-color: #f39c12; color: white; padding: 10px; border-radius: 4px;">Warning: #f39c12</div>
    </div>
  </div>
  <div style="flex: 1; min-width: 200px;">
    <h3>Typography</h3>
    <div style="display: flex; flex-direction: column; gap: 10px;">
      <div style="font-size: 2em; font-weight: bold;">Heading 1</div>
      <div style="font-size: 1.5em; font-weight: bold;">Heading 2</div>
      <div style="font-size: 1.17em; font-weight: bold;">Heading 3</div>
      <div style="font-size: 1em;">Body Text</div>
      <div style="font-size: 0.9em; color: #6c757d;">Caption Text</div>
    </div>
  </div>
  <div style="flex: 1; min-width: 200px;">
    <h3>Spacing</h3>
    <div style="display: flex; flex-direction: column; gap: 10px;">
      <div style="height: 4px; background-color: #e9ecef; border-radius: 4px;">XS: 4px</div>
      <div style="height: 8px; background-color: #e9ecef; border-radius: 4px;">SM: 8px</div>
      <div style="height: 16px; background-color: #e9ecef; border-radius: 4px;">MD: 16px</div>
      <div style="height: 24px; background-color: #e9ecef; border-radius: 4px;">LG: 24px</div>
      <div style="height: 32px; background-color: #e9ecef; border-radius: 4px;">XL: 32px</div>
    </div>
  </div>
</div>

---

For more information on how to use these components in your own applications, please refer to our [GitHub repository](https://github.com/cirqa/frontend).