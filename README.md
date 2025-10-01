# 🔐 VPN CLI - Enhanced ProtonVPN Manager

A powerful command-line wrapper for ProtonVPN CLI with additional features for easier VPN management, connection tracking, and security testing.

## Features

🚀 **Enhanced Connection Management**
- Connect to fastest server automatically
- Quick connect options (fast, random, P2P, Secure Core, Tor)
- Country-specific connections
- Reconnect functionality

🛡️ **Security Features**
- Kill Switch control
- NetShield configuration (malware and ad blocking)
- IP leak testing
- Connection logging

📊 **Monitoring & History**
- Real-time VPN status
- Connection history tracking (last 10 connections)
- Activity logs
- Public IP and location information

🎨 **User-Friendly Interface**
- Colorful CLI output
- Clear status indicators
- Comprehensive help system
- Command aliases for quick access

## Prerequisites

- **ProtonVPN CLI** (`protonvpn-cli`) - Required
- **curl** - Optional, for IP information and leak testing
- **jq** - Required, for history tracking

### Installing ProtonVPN CLI

#### Debian/Ubuntu/Kali Linux:
```bash
# Add Proton's repository
sudo apt-get update
curl -fsSL https://repo.protonvpn.com/debian/public_key.asc | gpg --dearmor | sudo tee /usr/share/keyrings/protonvpn-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/protonvpn-archive-keyring.gpg] https://repo.protonvpn.com/debian stable main" | sudo tee /etc/apt/sources.list.d/protonvpn-stable.list
sudo apt-get update

# Install ProtonVPN CLI
sudo apt-get install -y protonvpn-cli

# Login to ProtonVPN (required before first use)
protonvpn-cli login
```

## Installation

### Quick Install
```bash
cd ~/labs
git clone https://github.com/alexcolls/vpn-cli.git
cd vpn-cli
./install.sh
```

### Manual Installation
```bash
chmod +x vpn
sudo ln -s $(pwd)/vpn /usr/local/bin/vpn
```

## Usage

### Basic Commands

#### Connect to VPN
```bash
vpn connect              # Connect to fastest server
vpn c                    # Short alias
vpn connect US-NY#42     # Connect to specific server
```

#### Disconnect from VPN
```bash
vpn disconnect           # Disconnect from VPN
vpn d                    # Short alias
```

#### Reconnect
```bash
vpn reconnect            # Reconnect to VPN
vpn r                    # Short alias
```

#### Check Status
```bash
vpn status               # Show connection status and IP info
vpn s                    # Short alias
```

### Quick Connect Options

```bash
vpn quick fast           # Connect to fastest server
vpn quick random         # Connect to random server
vpn quick p2p            # Connect to P2P-optimized server
vpn quick secure         # Connect to Secure Core server
vpn quick tor            # Connect to Tor server
vpn quick US             # Connect to US server
vpn quick UK             # Connect to UK server
vpn quick JP             # Connect to Japan server
```

### Security Features

#### Kill Switch
```bash
vpn killswitch on        # Enable kill switch
vpn killswitch off       # Disable kill switch
vpn ks on                # Short alias
```

#### NetShield (Ad & Malware Blocking)
```bash
vpn netshield 0          # Disable NetShield
vpn netshield 1          # Block malware only
vpn netshield 2          # Block malware and ads
vpn ns 2                 # Short alias
```

### Monitoring & Testing

#### Connection History
```bash
vpn history              # Show last 10 connections
```

#### View Logs
```bash
vpn logs                 # Show last 20 log entries
vpn logs 50              # Show last 50 log entries
```

#### IP Leak Test
```bash
vpn leak                 # Run comprehensive IP leak test
vpn test                 # Alias
```

#### List Servers
```bash
vpn list                 # List available servers
vpn servers              # Alias
```

## Command Reference

| Command | Alias | Description |
|---------|-------|-------------|
| `connect [server]` | `c` | Connect to VPN |
| `disconnect` | `d` | Disconnect from VPN |
| `reconnect` | `r` | Reconnect to VPN |
| `status` | `s` | Show connection status |
| `quick <option>` | `q` | Quick connect (fast, random, p2p, secure, tor, country) |
| `killswitch <on\|off>` | `ks` | Control kill switch |
| `netshield <level>` | `ns` | Configure NetShield (0/off, 1/malware, 2/ads) |
| `history` | `h` | Show connection history |
| `logs [lines]` | `log` | Show recent logs |
| `leak` | `test` | Run IP leak test |
| `list` | `ls`, `servers` | List available servers |
| `help` | `--help`, `-h` | Show help message |

## Configuration

VPN CLI stores its data in `~/.config/vpn-cli/`:
- `profiles.json` - Connection history
- `vpn.log` - Activity logs

## Examples

### Quick Start
```bash
# Connect to fastest server
vpn connect

# Check your status
vpn status

# Disconnect when done
vpn disconnect
```

### Advanced Usage
```bash
# Enable kill switch for maximum security
vpn ks on

# Enable full ad and malware blocking
vpn ns 2

# Connect to secure core server
vpn quick secure

# Test for IP leaks
vpn leak

# View connection history
vpn history
```

### Country-Specific Connections
```bash
vpn quick US             # United States
vpn quick UK             # United Kingdom
vpn quick JP             # Japan
vpn quick DE             # Germany
vpn quick FR             # France
vpn quick CH             # Switzerland
vpn quick SE             # Sweden
vpn quick NL             # Netherlands
```

## Troubleshooting

### ProtonVPN CLI not found
```bash
# Verify installation
which protonvpn-cli

# Check if you've logged in
protonvpn-cli login
```

### Permission denied
```bash
# Make script executable
chmod +x vpn

# Or reinstall with install.sh
./install.sh
```

### Connection fails
```bash
# Check ProtonVPN status
protonvpn-cli status

# Try reconnecting
vpn reconnect

# Check logs
vpn logs
```

### Missing dependencies
```bash
# Install curl (for IP info)
sudo apt-get install curl

# Install jq (for history)
sudo apt-get install jq
```

## Security Notes

- Always use Kill Switch when maximum security is needed
- Enable NetShield to block malware and trackers
- Regularly run leak tests to ensure no IP leakage
- Check connection logs for any anomalies
- Keep ProtonVPN CLI updated

## Requirements

- **Operating System**: Linux, macOS
- **Shell**: bash, zsh
- **ProtonVPN**: Active ProtonVPN account
- **ProtonVPN CLI**: Version 3.x or higher

## Version

Current version: **1.0.0**

## License

Free to use and modify.

## Contributing

Feel free to submit issues or pull requests!

## Author

Created with ❤️ for secure and private internet browsing

## Related Projects

- [ProtonVPN](https://protonvpn.com/) - The VPN service provider
- [ProtonVPN CLI](https://github.com/ProtonVPN/linux-cli) - Official Linux CLI

---

**Disclaimer**: This is an independent wrapper tool and is not officially affiliated with or endorsed by Proton AG or ProtonVPN.
