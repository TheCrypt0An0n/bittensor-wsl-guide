# Bittensor Wallet Setup Guide for Windows WSL

This guide walks through the process of setting up a Bittensor wallet using Windows Subsystem for Linux (WSL).

## Prerequisites

- Windows 10 or 11
- WSL installed and running
- Ubuntu on WSL
- Python 3.x installed

## Step 1: Set Up Python Virtual Environment

First, open your WSL terminal and create a virtual environment:

```bash
# Create a new virtual environment
python3 -m venv ~/bittensor-venv

# Activate the virtual environment
source ~/bittensor-venv/bin/activate
```

## Step 2: Install Bittensor

Install Bittensor using pip:

```bash
# Install Bittensor
pip install bittensor
```

Verify the installation:
```bash
btcli --version
```

## Step 3: Directory Structure and Configuration

IMPORTANT NOTE: When using the default wallet location (`~/.bittensor/wallets`), you don't need a config.yml file. Only create a config.yml if you're using a non-standard wallet location.

```bash
# Create the bittensor directory (if it doesn't exist)
mkdir -p ~/.bittensor/wallets
```

If you need a custom wallet location (NOT RECOMMENDED for beginners), you would need to create a config.yml:
```bash
# ONLY if using non-standard paths
echo "wallet_path: /your/custom/path/to/wallets" > ~/.bittensor/config.yml
```

As learned from Bittensor CM in Discord:
> If you're using `.bittensor/wallets` for your wallets (the default), you don't need to set a path in config.yml. Only set the wallet path if you're storing wallets in a non-standard location.

## Step 4: Create Your Wallet

```bash
# Create a new wallet
btcli wallet create --wallet.name yourwalletname
```

During wallet creation:
1. Press Enter to accept default wallet path
2. Press Enter for default hotkey name
3. Choose 24 words for maximum security
4. Set a strong password
5. IMPORTANT: Save both coldkey and hotkey mnemonics securely offline

## Step 5: Verify Wallet Setup

Check your wallet:
```bash
# List all wallets
btcli w list

# Check wallet balance
btcli wallet balance --wallet.name yourwalletname
```

## Important Notes

1. **Backup Your Mnemonics**: Store both coldkey and hotkey mnemonics securely offline. They are crucial for wallet recovery.
2. **Password Security**: Use strong passwords and store them safely.
3. **Environment Activation**: Every time you restart WSL, activate the environment with:
   ```bash
   source ~/bittensor-venv/bin/activate
   ```

## Troubleshooting

If you encounter wallet access issues:
1. Ensure you're in the virtual environment
2. Check directory permissions
3. Verify wallet name is correct
4. Make sure you're using the default wallet path

## Common Commands

```bash
# List wallets
btcli w list

# Check balance
btcli w balance --wallet.name yourwalletname

# Wallet overview
btcli w overview --wallet.name yourwalletname

# Inspect wallet
btcli w inspect --wallet.name yourwalletname
```

## Security Recommendations

1. Never share your mnemonic phrases
2. Keep your coldkey secure - it controls your funds
3. Use strong, unique passwords
4. Regularly backup your wallet information
5. Don't store mnemonics digitally

## Additional Resources

- [Official Bittensor Documentation](https://docs.bittensor.com/)
- [Bittensor GitHub Repository](https://github.com/opentensor/bittensor)