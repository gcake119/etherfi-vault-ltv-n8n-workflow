# etherfi-vault-ltv-n8n-workflow

> n8n Workflow for DeFi users to monitor Ether.fi Vault assets, custom LTV risk lines, and receive instant alerts via Telegram or Email.

## Features

- Connect your Ether.fi Vault address for real-time monitoring
- Set custom Loan-to-Value (LTV) risk thresholds per asset
- Automated asset fetch and price updates via APIs (Etherscan, CoinGecko, etc.)
- Instant risk alerts via Telegram and Email upon reaching configurable safety limits
- Workflows suitable for personal n8n instance — no centralized backend

## Getting Started

### Prerequisites

- n8n instance (self-hosted or Cloud)
- Your Ether.fi Vault address
- API keys for blockchain (Etherscan/Alchemy/Infura) and market data (CoinGecko)
- Telegram Bot token and Chat ID (if using Telegram alerts)
- Valid email credentials for SMTP (if using email alerts)

### Installation

1. Clone this repository:

```bash
git clone https://github.com/your-org/etherfi-vault-ltv-n8n-workflow.git
```

2. Import `vault-monitor-workflow.json` into your n8n workspace.

### Configuration

- Edit the workflow `Configuration` node:
- `vaultAddress` - Replace with your vault address (e.g., `0xYourVaultAddress`)
- `borrowedAmount` - Your current loan value
- `safeLTVPercent` - Set custom LTV thresholds by asset (JSON object)
- `warningThreshold` - Notification trigger percentage
- Update HTTP Request node for correct API endpoints and keys
- Configure Telegram/Email nodes with your credentials

### Usage

- Activate the workflow
- The workflow will run periodically based on the schedule node
- When your safety line gets close to or below your loan, alerts will be sent automatically

## Contributing

- Fork the repository and create your feature branch
- Submit pull requests and discuss via GitHub Issues
- Please follow Airbnb JavaScript and Markdown style guides for PRs

## License

MIT

## References

- [n8n Documentation](https://docs.n8n.io)
- [Ether.fi Vault Docs](https://etherfi.gitbook.io/etherfi/cash/vault)
- [CoinGecko API](https://www.coingecko.com/en/api)
