# RugProofAI Security Snap for MetaMask

This MetaMask Snap provides token security analysis and protection features to help users avoid scams, honeypots, and risky transactions. By integrating RugProofAI's security analysis directly into the MetaMask wallet experience, users can make more informed decisions before approving transactions.

The RugProofAI Security Snap runs in an isolated environment within MetaMask and analyzes token-related transactions in real-time, offering security insights before users confirm potentially risky actions.

## Key Security Features

### 1. Pre-Transaction Analysis

The Snap intercepts token-related transactions and analyzes them before the user confirms, providing security insights directly within the MetaMask interface.

### 2. Token Security Checks

- **Honeypot Detection**: Identifies tokens that users can't sell after purchasing
- **Spam Token Detection**: Leverages RugProofAI's database to identify known spam tokens
- **Contract Risk Assessment**: Analyzes token contracts for common vulnerabilities and risks

### 3. Alert System

- **High-Risk Transactions**: Display prominent warnings with detailed risk information
- **Medium-Risk Transactions**: Show caution notices with specific concerns
- **Low-Risk Transactions**: Provide brief verification reminders

### 4. On-Demand Analysis

Users can manually analyze any token address for comprehensive security insights

### 5. Multi-Chain Support

Works across all major EVM-compatible blockchains

## Getting Started

To use the RugProofAI Security Snap, you'll need [MetaMask Flask](https://metamask.io/flask/),
which is the developer version of MetaMask that supports Snaps.

```shell
# Install dependencies and start the development environment
yarn install && yarn start
```

## Implementation Details

### Snap Implementation

The RugProofAI Security Snap is built using the MetaMask Snaps SDK and implements the following key components:

1. **Transaction Interception**: The Snap uses the appropriate MetaMask Snap APIs to monitor and analyze token transactions.

2. **Security Analysis**: We integrate with RugProofAI's security algorithms to detect potential scams, honeypots, and risky tokens.

3. **User Interface**: Custom alerts and dialogs provide clear security information to users directly within their MetaMask wallet.

### Integration

To integrate the RugProofAI Security Snap into your dApp or website:

```javascript
// Connect to MetaMask
await window.ethereum.request({ method: 'eth_requestAccounts' });

// Connect to RugProofAI Snap
await window.ethereum.request({
  method: 'wallet_requestSnaps',
  params: {
    'npm:rugproof-security-snap': {},
  },
});

// Analyze a token address
const analysis = await window.ethereum.request({
  method: 'wallet_invokeSnap',
  params: {
    snapId: 'npm:rugproof-security-snap',
    request: {
      method: 'analyzeToken',
      params: {
        tokenAddress: '0x...',
        chainId: 1, // Ethereum mainnet
      },
    },
  },
});
```

## Usage Workflow

The RugProofAI Security Snap is designed to integrate seamlessly into the user's MetaMask experience:

1. **Installation**: User installs the RugProofAI Security Snap from the MetaMask Snap directory.

2. **Automatic Analysis**: When the user interacts with a token contract (swap, approve, transfer), the Snap automatically analyzes the token:

   - Checks for honeypot characteristics
   - Verifies against known scam/spam token database
   - Analyzes contract code for common vulnerabilities

3. **Security Alerts**: Based on risk level, the Snap displays appropriate alerts:

   - 🚨 **High Risk**: Prominent warning with detailed explanation
   - ⚠️ **Medium Risk**: Caution notice with specific concerns
   - ✓ **Low Risk**: Brief verification reminder

4. **On-Demand Analysis**: Users can manually analyze any token address by using the "Check Token Security" feature in their MetaMask wallet.

5. **Transaction Decision**: Armed with security insights, users can make informed decisions to proceed with or cancel transactions.

## Contributing

We welcome contributions to the RugProofAI Security Snap! Here's how to get started:

### Development Setup

1. Clone this repository
2. Run `yarn install` to install dependencies
3. Run `yarn start` to start the development environment

### Testing and Linting

Run `yarn test` to run the tests once.

Run `yarn lint` to run the linter, or run `yarn lint:fix` to run the linter and fix any automatically fixable issues.

### Feature Requests and Bug Reports

Please submit feature requests and bug reports through GitHub issues.

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.
