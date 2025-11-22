# etherfi-vault-ltv-n8n-workflow

> n8n Workflow for DeFi users to monitor Ether.fi Vault assets, borrow/debt status (via official DebtManager contract), custom LTV risk lines, and receive instant alerts via Telegram or Email.  
> **Note: The workflow for automated DebtManager integration and custom user settings is under active development and not yet fully finished.**

## Features

- Connect your Ether.fi Vault address for real-time asset/debt monitoring
- Automated queries to official DebtManager smart contract on Scroll chain:
  - Fetch real-time vault debt, borrow limits, liquidation thresholds
  - No wallet signature required—read-only public data
- Set custom Loan-to-Value (LTV) risk thresholds and asset safety criteria per user
- Dynamic push notifications through Telegram or Email upon reaching personalized safety limits
- Web form or spreadsheet support for custom settings input (planned)
- Workflow suitable for personal n8n instance or low-cost cloud deployments (e.g., Zeabur) for 24/7 privacy-safe operation
- No centralized backend; user vault/config is strictly local

## Getting Started

### Prerequisites

- n8n instance (recommended self-hosted or Zeabur-based deployment)
- Your Ether.fi Vault address (see Cash/Portfolio page on Ether.fi)
- API keys for relevant blockchain RPC (Infura/Alchemy for Scroll)
- DebtManager smart contract ABI (see Ether.fi official GitHub/Open Source)
- Telegram Bot token + Chat ID (for Telegram alerts, optional)
- Valid email credentials for SMTP (for Email alerts, optional)

### Installation

1. Clone this repository:

```bash
git clone https://github.com/your-org/etherfi-vault-ltv-n8n-workflow.git
```

2. Import `vault-monitor-workflow.json` into your n8n workspace or Zeabur environment.

### Configuration

- Edit the workflow `Configuration` node:
- `vaultAddress` - Paste your personal Ether.fi vault contract address (e.g., `0xYourVaultAddress`)
- `safeLTVPercent` - Set custom risk thresholds by asset (JSON object)
- `warningThreshold` - Notification trigger percentage (e.g., 0.05)
- Push notification preferences (Telegram/Email)
- In workflow nodes, set up:
- DebtManager contract address on Scroll: `0x8f9d2Cd33551CE06dD0564Ba147513F715c2F4a0`
- Paste ABI or reference to ABI file for contract queries
- Input external RPC/price API keys as needed

### Usage

- Activate the workflow
- The schedule node runs monitoring & queries 24/7
- Alert triggers are personalized according to your vault state and your safety settings
- Automated messages delivered to your configured channels whenever thresholds are breached

## Contributing

- Fork this repo and make a feature branch for changes
- Create Pull Requests and use GitHub Issues for collaborative discussion
- Follow Airbnb JS and Markdown style guidelines

## Development Status

- DebtManager contract querying logic not yet fully implemented
- Web form/spreadsheet integration for dynamic user settings is in development
- Workflow and configuration node templates may change in future versions

## License

MIT

## References

- [n8n Documentation](https://docs.n8n.io)
- [Ether.fi Vault Docs](https://etherfi.gitbook.io/etherfi/cash/vault)
- [Ether.fi Contracts + ABI](https://github.com/etherfi-protocol/cash-contracts)
- [CoinGecko API](https://www.coingecko.com/en/api)
- [Zeabur Deployment Guide](https://zeabur.com/templates/JP88UN)
