# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.0.0] - 2025-10-01

### 🎉 Major Release - Multi-Provider Support

This is a major update that fundamentally changes how VPN-CLI works by adding support for multiple VPN providers, eliminating the requirement for a ProtonVPN account.

### Added
- **Free VPN support** using VPNGate public servers
  - No account registration required
  - Completely free to use
  - Multiple country support (US, UK, JP, DE, FR, CA, AU, NL, KR, etc.)
  - Automatic OpenVPN installation
- **Interactive setup menu** for provider selection
  - User-friendly console interface
  - Clear provider comparison and selection
  - Real-time provider status display
- **Provider switching functionality**
  - Easy switching between ProtonVPN and Free VPN
  - `vpn switch` command
  - Persistent provider configuration
- **Enhanced connection management**
  - Country-specific connections for free VPN
  - Automatic server selection
  - VPNGate API integration
- **Improved logging system**
  - Separate log files for each provider
  - OpenVPN daemon logs
  - Connection history tracking

### Changed
- **Simplified command structure**
  - Reduced from 418 lines to 241 lines of code (42% reduction)
  - More maintainable and readable codebase
  - Optimized for performance
- **Updated setup process**
  - Interactive menu-based configuration
  - No longer requires ProtonVPN by default
  - Automatic dependency detection and installation
- **Enhanced status command**
  - Shows current provider
  - Displays connection state
  - Real-time IP and country information
- **Improved error handling**
  - Better error messages
  - Graceful fallbacks
  - User-friendly troubleshooting hints

### Fixed
- Resolved issue where users needed ProtonVPN account to use the tool
- Fixed dependency checking logic
- Improved process detection for connection status
- Better handling of API failures

### Removed
- Removed ProtonVPN-specific advanced features (will be added back in future versions):
  - NetShield configuration
  - Kill Switch controls
  - Secure Core connections
  - P2P server selection
  - Tor server connections

### Security
- Free VPN connections use OpenVPN with standard security
- No user data collection
- No account credentials stored for free VPN

### Performance
- 42% reduction in code size (418→241 lines)
- Faster startup time
- Reduced memory footprint
- Optimized API calls

## [1.0.0] - 2025-10-01

### 🚀 Initial Release

First public release of VPN-CLI with ProtonVPN integration.

### Added
- **ProtonVPN integration**
  - Full ProtonVPN CLI wrapper functionality
  - Automatic fastest server connection
  - Manual server selection
- **Connection management**
  - Connect, disconnect, reconnect commands
  - Real-time connection status
  - Connection history tracking (last 10 connections)
- **Advanced ProtonVPN features**
  - Kill Switch control (enable/disable)
  - NetShield configuration (malware and ad blocking)
  - Secure Core server connections
  - P2P-optimized server connections
  - Tor over VPN server connections
- **Quick connect options**
  - Connect to fastest server
  - Connect to random server
  - Country-specific connections
  - Feature-specific servers (P2P, Secure Core, Tor)
- **Monitoring and diagnostics**
  - IP leak testing
  - Public IP and location display
  - Connection logs
  - Activity history
- **User interface**
  - Colorful CLI output with emojis
  - Clear status indicators
  - Comprehensive help system
  - Command aliases for convenience
- **Documentation**
  - Detailed README with examples
  - Installation instructions
  - Troubleshooting guide
  - Professional installer script

### Technical Details
- Written in pure Bash
- Compatible with Linux and macOS
- Requires: ProtonVPN CLI, curl, jq
- Data stored in: `~/.config/vpn-cli/`

### Known Limitations
- Requires ProtonVPN account (free or paid)
- Manual account creation needed
- ProtonVPN CLI must be installed separately

---

## Version History Summary

| Version | Date       | Key Features                                    |
|---------|------------|-------------------------------------------------|
| 2.0.0   | 2025-10-01 | Multi-provider support, Free VPN, No account   |
| 1.0.0   | 2025-10-01 | Initial release with ProtonVPN integration     |

---

## Upgrade Guide

### Upgrading from 1.0.0 to 2.0.0

**Breaking Changes:**
- First run requires `vpn setup` to choose provider
- Some ProtonVPN-specific features temporarily removed
- Config file format changed (automatically migrated)

**Migration Steps:**

1. Pull the latest version:
   ```bash
   cd ~/labs/vpn-cli
   git pull
   ```

2. Run setup to choose your provider:
   ```bash
   ./vpn setup
   ```

3. Choose your provider:
   - Option 1: ProtonVPN (if you have an account)
   - Option 2: Free VPN (no account needed!)

4. Connect as usual:
   ```bash
   ./vpn connect
   ```

**What's Preserved:**
- Connection history
- Log files
- Configuration directory structure

**What Changes:**
- Provider selection required on first run
- New config file format with provider field
- Simplified command options

---

## Future Roadmap

### Planned for v2.1.0
- [ ] Add back NetShield support for ProtonVPN
- [ ] Add back Kill Switch support for ProtonVPN
- [ ] Free VPN server quality ratings
- [ ] Connection speed testing
- [ ] Auto-reconnect on disconnect

### Planned for v2.2.0
- [ ] Additional free VPN providers (VPNBook, Hide.me)
- [ ] WireGuard protocol support
- [ ] Split tunneling configuration
- [ ] GUI version using dialog/whiptail

### Planned for v3.0.0
- [ ] Custom VPN provider support
- [ ] Multi-hop VPN connections
- [ ] VPN kill switch for all providers
- [ ] Bandwidth monitoring
- [ ] Connection profiles and favorites

---

## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### How to Report Issues

1. Check if the issue already exists
2. Provide VPN-CLI version: `vpn help | head -1`
3. Include your OS and distribution
4. Provide relevant log files from `~/.config/vpn-cli/`
5. Describe steps to reproduce

### Development

To contribute code:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

---

## Credits

- **VPNGate** - For providing free public VPN servers
- **ProtonVPN** - For their excellent VPN service
- **OpenVPN** - For the VPN protocol implementation
- All contributors and users of VPN-CLI

---

## License

Free to use and modify.

---

**Note**: This changelog follows semantic versioning. See [semver.org](https://semver.org/) for details.
