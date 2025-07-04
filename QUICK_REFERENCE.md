# Webinoly Quick Reference Guide

## Installation

```bash
# Quick LEMP installation
wget -qO weby qrok.es/wy && sudo bash weby

# Installation options
wget -qO weby qrok.es/wy && sudo bash weby -nginx    # HTML server
wget -qO weby qrok.es/wy && sudo bash weby -php      # PHP server  
wget -qO weby qrok.es/wy && sudo bash weby -lemp     # Full LEMP
wget -qO weby qrok.es/wy && sudo bash weby -clean    # App only
```

## Essential Commands

### Server Management
```bash
sudo webinoly -update                    # Update Webinoly
sudo webinoly -verify                    # Verify installation
sudo webinoly -info                      # Show server info
sudo webinoly -dbpass                    # Show DB credentials
sudo webinoly -clear-cache=all           # Clear all caches
```

### Stack Management
```bash
sudo stack -info                         # Show stack info
sudo stack -nginx                        # Install Nginx
sudo stack -php                          # Install PHP
sudo stack -mysql                        # Install MySQL
sudo stack -lemp                         # Install full LEMP
sudo stack -redis                        # Install Redis
sudo stack -letsencrypt                  # Install Let's Encrypt
```

### Site Management
```bash
sudo site example.com -wp                # WordPress site
sudo site example.com -php               # PHP site
sudo site example.com -html              # HTML site
sudo site example.com -ssl               # Add SSL certificate
sudo site example.com -cache=on          # Enable cache
sudo site example.com -delete            # Delete site
sudo site -list                          # List all sites
```

### HTTP Authentication
```bash
sudo httpauth -add                       # Add global user
sudo httpauth example.com -add           # Add user for site
sudo httpauth example.com -wp-admin=on   # Protect WP admin
sudo httpauth -list                      # List users
```

### Log Viewing
```bash
sudo log                                 # View access logs
sudo log example.com -error              # View error logs
sudo log -php                           # View PHP logs
sudo log -mysql                         # View MySQL logs
```

## Quick Workflows

### WordPress Site Setup
```bash
sudo stack -lemp                         # Install LEMP
sudo site example.com -wp -ssl           # Create WP site with SSL
sudo site example.com -cache=on          # Enable cache
sudo httpauth example.com -wp-admin=on   # Protect admin
```

### Node.js App Deployment
```bash
sudo stack -nginx                        # Install Nginx
sudo site api.example.com -proxy=http://localhost:3000 -ssl
```

### Development Environment
```bash
sudo stack -php                          # Install PHP stack
sudo site dev.local -php                 # Create dev site
sudo log dev.local -enable               # Enable logging
```

## Common Parameters

### SSL Options
- `-ssl` - Let's Encrypt certificate
- `-ssl -wildcard` - Wildcard certificate  
- `-ssl=custom -ssl-crt=path -ssl-key=path` - Custom certificate

### Cache Options
- `-cache=on` - Enable FastCGI cache
- `-cache=off` - Disable cache
- `-cache-valid=1h` - Set cache validity

### WordPress Options
- `-wp` - Simple WordPress
- `-wp=[true,true,host,db,user,pass,prefix]` - Custom WP setup
- `-multisite-convert` - Convert to multisite

### Backup Options
- `-backup=all` - Full backup
- `-backup=site` - Site backup
- `-backup=db` - Database backup

## Configuration Files

```bash
/opt/webinoly/webinoly.conf              # Main configuration
/etc/nginx/sites-available/              # Site configurations
/var/www/                                # Website files
/var/log/nginx/                          # Nginx logs
```

## Troubleshooting

```bash
sudo webinoly -verify                    # Check installation
sudo nginx -t                           # Test Nginx config
sudo systemctl status nginx             # Check Nginx status
sudo systemctl status mysql             # Check MySQL status
sudo log example.com -error              # Check error logs
```

## File Locations

```bash
# Webinoly
/opt/webinoly/                           # Main installation
/usr/bin/webinoly                        # Main command
/usr/bin/site                           # Site command
/usr/bin/stack                          # Stack command

# Web Files  
/var/www/example.com/                    # Site root
/var/www/example.com/htdocs/             # Web files
/var/www/example.com/conf/               # Site configs

# Logs
/var/log/nginx/example.com.access.log    # Access logs
/var/log/nginx/example.com.error.log     # Error logs
/var/log/nginx/error.log                 # Global error log
```

## Environment Variables

Set in `/opt/webinoly/webinoly.conf`:

```bash
mysql-root=password                      # MySQL root password
tools-port=22222                         # Admin tools port
fastcgi-cache=on                         # FastCGI cache status
login-www-data=true                      # SFTP access
```

## Quick Tips

- Use `sudo` for all commands
- Check logs when troubleshooting: `sudo log example.com -error`
- Verify after changes: `sudo webinoly -verify`
- Backup before major changes: `sudo webinoly -backup=all`
- Clear cache after config changes: `sudo webinoly -clear-cache=all`
- Test Nginx config: `sudo nginx -t`
- Restart services: `sudo systemctl restart nginx`
