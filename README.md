# 🔐 VPN CLI - Multi-Provider VPN Manager

A powerful command-line VPN manager supporting multiple providers including **ProtonVPN** and **Free VPN** (no account required!). Simplified, efficient, and easy to use.

## Features

🆓 **Multi-Provider Support**
- **Free VPN** via VPNGate public servers (no account needed!)
- **ProtonVPN** integration (requires account)
- Easy provider switching
- Interactive setup menu

🌍 **Flexible Connections**
- Connect to fastest/nearest server automatically
- Country-specific connections (US, UK, JP, DE, FR, CA, AU, NL, KR, etc.)
- Simple reconnect functionality
- Support for specific server selection (ProtonVPN)

📊 **Monitoring & History**
- Real-time VPN status
- Connection history tracking (last 10 connections)
- Activity logs
- Public IP and location information

🎨 **User-Friendly Interface**
- Colorful CLI output with emojis
- Clear status indicators
- Interactive provider setup
- Comprehensive help system

⚡ **Lightweight & Efficient**
- Pure Bash implementation
- 42% smaller codebase than v1.0.0 (241 lines)
- Fast startup and execution
- Minimal dependencies

## Prerequisites

### Core Requirements
- **bash** - Shell interpreter (usually pre-installed)
- **jq** - JSON processor for configuration management
- **curl** - For IP information and Free VPN server fetching

### Provider-Specific Requirements
- **OpenVPN** - Required for Free VPN connections (auto-installed if missing)
- **ProtonVPN CLI** (`protonvpn-cli`) - Optional, only needed if using ProtonVPN

### Installing Dependencies

#### Debian/Ubuntu/Kali Linux:
```bash
# Install core dependencies
sudo apt-get update
sudo apt-get install -y jq curl

# For Free VPN (installed automatically during setup)
sudo apt-get install -y openvpn

# For ProtonVPN (OPTIONAL - only if you want to use ProtonVPN)
# Add Proton's repository
curl -fsSL https://repo.protonvpn.com/debian/public_key.asc | gpg --dearmor | sudo tee /usr/share/keyrings/protonvpn-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/protonvpn-archive-keyring.gpg] https://repo.protonvpn.com/debian stable main" | sudo tee /etc/apt/sources.list.d/protonvpn-stable.list
sudo apt-get update
sudo apt-get install -y protonvpn-cli

# Then login to ProtonVPN
protonvpn-cli login
```

## Installation

### Quick Install (Recommended)
```bash
cd ~/labs
git clone https://github.com/alexcolls/vpn-cli.git
cd vpn-cli
./install.sh
```

The installer will:
- Check and install dependencies
- Create symlink in `~/.local/bin/vpn`
- Add to PATH if needed

### Manual Installation
```bash
chmod +x vpn
mkdir -p ~/.local/bin
ln -s $(pwd)/vpn ~/.local/bin/vpn

# Add to PATH (if not already)
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

### First-Time Setup
After installation, run the setup to choose your VPN provider:
```bash
vpn setup
```

You'll be presented with an interactive menu to choose:
1. **ProtonVPN** (requires account from protonvpn.com)
2. **Free VPN** (no account needed! ⭐)

## Usage

### First-Time Setup
Before connecting, choose your VPN provider:
```bash
vpn setup
```

Select from the interactive menu:
- **Option 1**: ProtonVPN (requires account)
- **Option 2**: Free VPN (no account needed! ⭐)

### Basic Commands

#### Connect to VPN
```bash
vpn connect              # Connect to fastest/default server
vpn c                    # Short alias

# With country code (for Free VPN or ProtonVPN)
vpn connect US           # Connect to US server
vpn connect JP           # Connect to Japan server
vpn connect UK           # Connect to UK server

# Specific server (ProtonVPN only)
vpn connect US-NY#42     # Connect to specific ProtonVPN server
```

#### Disconnect from VPN
```bash
vpn disconnect           # Disconnect from VPN
vpn d                    # Short alias
```

#### Check Status
```bash
vpn status               # Show connection status, provider, and IP info
vpn s                    # Short alias
```

#### Connection History
```bash
vpn history              # Show last 10 connections
vpn h                    # Short alias
```

#### Switch Provider
```bash
vpn switch               # Switch between ProtonVPN and Free VPN
```

#### Get Help
```bash
vpn help                 # Show help message with all commands
vpn --help               # Alternative
vpn -h                   # Alternative
```

## Command Reference

| Command | Alias | Description |
|---------|-------|-------------|
| `setup` | - | Interactive provider setup (first-time configuration) |
| `connect [country]` | `c` | Connect to VPN (optional country code) |
| `disconnect` | `d` | Disconnect from VPN |
| `status` | `s` | Show connection status, provider, and IP info |
| `history` | `h` | Show connection history (last 10) |
| `switch` | - | Switch between ProtonVPN and Free VPN |
| `help` | `--help`, `-h` | Show help message |

## Configuration

VPN CLI stores its data in `~/.config/vpn-cli/`:
- `config.json` - Provider configuration
- `history.json` - Connection history (last 10)
- `vpn.log` - Activity logs
- `free-vpn/` - Free VPN configuration files
- `openvpn.log` - OpenVPN daemon logs (Free VPN only)

## Examples

### Quick Start (Free VPN - No Account!)
```bash
# First-time setup
vpn setup
# Select option 2 (Free VPN)

# Connect to default server
vpn connect

# Check your status
vpn status

# View connection history
vpn history

# Disconnect when done
vpn disconnect
```

### Country-Specific Connections (Free VPN)
```bash
vpn connect US           # United States
vpn connect UK           # United Kingdom
vpn connect JP           # Japan
vpn connect DE           # Germany
vpn connect FR           # France
vpn connect CA           # Canada
vpn connect AU           # Australia
vpn connect NL           # Netherlands
vpn connect KR           # South Korea
```

### Using ProtonVPN
```bash
# First-time setup
vpn setup
# Select option 1 (ProtonVPN)
# Login when prompted

# Connect to fastest server
vpn connect

# Connect to specific server
vpn connect US-NY#42

# Check status
vpn status
```

### Switching Providers
```bash
# Switch from Free VPN to ProtonVPN (or vice versa)
vpn switch

# Then connect with the new provider
vpn connect
```

## Troubleshooting

### No provider configured
```bash
# Run setup to choose a provider
vpn setup
```

### Free VPN connection fails
```bash
# Check if OpenVPN is installed
which openvpn

# Install OpenVPN if missing
sudo apt-get install -y openvpn

# Check OpenVPN logs
tail -f ~/.config/vpn-cli/openvpn.log
```

### ProtonVPN not working
```bash
# Verify ProtonVPN CLI is installed
which protonvpn-cli

# Check if you've logged in
protonvpn-cli login

# Check ProtonVPN status
protonvpn-cli status
```

### Permission denied
```bash
# Make script executable
chmod +x vpn

# Or reinstall with install.sh
./install.sh
```

### Missing dependencies
```bash
# Install all dependencies
sudo apt-get install -y jq curl openvpn
```

### Command not found
```bash
# Add ~/.local/bin to PATH
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

## Security Notes

### Free VPN
- Free VPN uses public VPNGate servers - good for privacy but not for sensitive operations
- No logs are stored locally beyond connection history
- Use for general browsing, bypassing geo-restrictions

### ProtonVPN
- More secure and reliable than free options
- Trusted VPN provider with strong privacy policies
- Better for sensitive operations and business use

### General Tips
- Always verify your IP after connecting: `vpn status`
- Check connection logs for anomalies: `~/.config/vpn-cli/vpn.log`
- Keep VPN CLI and dependencies updated
- Disconnect when not needed to avoid unnecessary traffic routing

## Requirements

- **Operating System**: Linux (Ubuntu, Debian, Kali, etc.), macOS
- **Shell**: bash (zsh compatible)
- **Dependencies**: jq, curl
- **VPN Backends**:
  - OpenVPN (for Free VPN)
  - ProtonVPN CLI 3.x+ (for ProtonVPN, optional)

## Version

Current version: **2.0.0**

See [CHANGELOG.md](CHANGELOG.md) for version history and upgrade notes.

## License

Free to use and modify.

## What's New in v2.0.0

🎉 **Major Update!**

- ✅ **Free VPN support** - No account required!
- ✅ **Multi-provider** - Choose between ProtonVPN and Free VPN
- ✅ **42% smaller** - Reduced from 418 to 241 lines of code
- ✅ **Interactive setup** - Easy provider configuration
- ✅ **Provider switching** - Change providers on the fly

See [CHANGELOG.md](CHANGELOG.md) for complete details.

## Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Test your changes thoroughly
4. Submit a pull request

Report issues at: https://github.com/alexcolls/vpn-cli/issues

## Author

Created with ❤️ for secure and private internet browsing

## Related Projects

- [ProtonVPN](https://protonvpn.com/) - The VPN service provider
- [ProtonVPN CLI](https://github.com/ProtonVPN/linux-cli) - Official Linux CLI

---

**Disclaimer**: This is an independent wrapper tool and is not officially affiliated with or endorsed by Proton AG or ProtonVPN.
