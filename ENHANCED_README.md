# Webinoly - Enhanced Documentation Package

This repository now includes comprehensive documentation for Webinoly, the optimized NGINX web server management tool.

## 📚 Documentation Files

### 1. [DOCUMENTATION.md](./DOCUMENTATION.md)
**Complete comprehensive guide covering:**
- Overview and installation
- Detailed command explanations
- Configuration management
- Advanced usage scenarios
- Troubleshooting guides
- Real-world examples

### 2. [QUICK_REFERENCE.md](./QUICK_REFERENCE.md) 
**Quick lookup guide featuring:**
- Essential commands at a glance
- Common workflows
- File locations
- Configuration tips
- Troubleshooting shortcuts

### 3. [COMMAND_REFERENCE.md](./COMMAND_REFERENCE.md)
**Complete command reference with:**
- All available options for each command
- Valid argument values
- Detailed parameter explanations
- Usage examples for every option
- Argument format specifications

## 🚀 Quick Start

### Installation
```bash
# Install complete LEMP stack
wget -qO weby qrok.es/wy && sudo bash weby
```

### Create Your First Site
```bash
# WordPress site with SSL
sudo site example.com -wp -ssl

# Enable caching
sudo site example.com -cache=on
```

## 📖 How to Use This Documentation

1. **New to Webinoly?** Start with [DOCUMENTATION.md](./DOCUMENTATION.md) for complete understanding
2. **Need quick commands?** Use [QUICK_REFERENCE.md](./QUICK_REFERENCE.md) for instant lookup
3. **Looking for specific arguments?** Check [COMMAND_REFERENCE.md](./COMMAND_REFERENCE.md) for detailed options

## 🔧 Core Commands Overview

| Command | Purpose | Example |
|---------|---------|---------|
| `webinoly` | Server management | `sudo webinoly -update` |
| `stack` | Install/manage components | `sudo stack -lemp` |
| `site` | Website management | `sudo site example.com -wp` |
| `httpauth` | Authentication | `sudo httpauth -add` |
| `log` | Log viewing | `sudo log example.com -error` |

## 📋 System Requirements

- **OS**: Ubuntu 24.04 (Noble) or 22.04 (Jammy)
- **Access**: Root or sudo privileges required
- **Network**: Internet connection for downloads

## 🔗 Official Resources

- **Website**: [webinoly.com](https://webinoly.com/)
- **Documentation**: [webinoly.com/documentation](https://webinoly.com/documentation/)
- **GitHub**: [github.com/QROkes/webinoly](https://github.com/QROkes/webinoly)
- **Community**: [webinoly.com/premium](https://webinoly.com/premium/)

## 💡 Key Features Covered

- ✅ Complete LEMP stack installation
- ✅ WordPress optimization with caching
- ✅ SSL certificates (Let's Encrypt)
- ✅ HTTP/3 support
- ✅ Reverse proxy configuration
- ✅ Backup and migration tools
- ✅ Security features
- ✅ Real-time log monitoring
- ✅ Database management
- ✅ Multi-PHP version support

## 🤝 Contributing

This documentation enhancement aims to make Webinoly more accessible. For:
- **Webinoly issues**: Visit the [official repository](https://github.com/QROkes/webinoly)
- **Documentation improvements**: Create issues or pull requests
- **Community support**: Join the [Premium Community](https://webinoly.com/premium/)

## 📄 License

This documentation follows the same license as the Webinoly project. See [LICENSE](./LICENSE) for details.

---

*These documentation files provide comprehensive coverage of Webinoly v1.19+ features and are designed to help both beginners and advanced users effectively manage their web servers.*
