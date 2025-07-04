# Webinoly - Comprehensive Documentation

## Table of Contents

1. [Overview](#overview)
2. [Installation](#installation)
3. [Core Commands](#core-commands)
4. [Command Reference](#command-reference)
   - [webinoly](#webinoly-command)
   - [stack](#stack-command)
   - [site](#site-command)
   - [httpauth](#httpauth-command)
   - [log](#log-command)
5. [Configuration](#configuration)
6. [Advanced Usage](#advanced-usage)
7. [Examples](#examples)
8. [Troubleshooting](#troubleshooting)

## Overview

Webinoly is a powerful set of bash scripts designed to simplify the installation and management of LEMP stack (Linux, Nginx, MySQL/MariaDB, PHP) servers on Ubuntu. It provides an optimized Nginx web server configuration with modern features including HTTP/3, FastCGI caching, SSL certificates, and comprehensive site management.

### Key Features

- **Complete LEMP Stack**: Linux Ubuntu + Nginx + MariaDB/MySQL + PHP
- **SSL Certificates**: Free Let's Encrypt certificates with automatic renewal
- **HTTP/3 Support**: Latest protocol for enhanced performance
- **PHP Support**: PHP 8.3, 8.2, 8.1, 8.0, 7.4, and 8.4
- **WordPress Optimization**: FastCGI Cache and Redis Object Cache
- **Reverse Proxy**: Support for modern applications (React, Node, Angular, Vue)
- **Backup Solutions**: Complete backup and migration tools
- **Security Features**: HTTP Authentication and advanced protection
- **Monitoring**: Datadog integration for analytics
- **Real-time Logs**: Live log viewing capabilities

### System Requirements

- **Operating System**: Ubuntu 24.04 (Noble) or 22.04 (Jammy)
- **Privileges**: Root or sudo access required
- **Network**: Internet connection for package downloads

## Installation

### Quick Installation

```bash
# Download and install Webinoly with LEMP stack
wget -qO weby qrok.es/wy && sudo bash weby
```

### Installation Options

#### 1. LEMP Stack (Default)
```bash
wget -qO weby qrok.es/wy && sudo bash weby 3
# OR
wget -qO weby qrok.es/wy && sudo bash weby -lemp
```

#### 2. HTML Server Only
```bash
wget -qO weby qrok.es/wy && sudo bash weby 1
# OR
wget -qO weby qrok.es/wy && sudo bash weby -nginx
```

#### 3. PHP Server (Nginx + PHP)
```bash
wget -qO weby qrok.es/wy && sudo bash weby 2
# OR
wget -qO weby qrok.es/wy && sudo bash weby -php
```

#### 4. App Only (No Stack)
```bash
wget -qO weby qrok.es/wy && sudo bash weby 0
# OR
wget -qO weby qrok.es/wy && sudo bash weby -clean
```

#### 5. Custom Version Installation
```bash
wget -qO weby qrok.es/wy && sudo bash weby -ver=1.19.0
```

## Core Commands

Webinoly provides five main commands for server management:

1. **`webinoly`** - Server management and configuration
2. **`stack`** - Stack component installation and management
3. **`site`** - Website creation and management
4. **`httpauth`** - HTTP authentication management
5. **`log`** - Log file viewing and management

## Command Reference

### webinoly Command

The main command for server management, updates, and configuration.

#### Syntax
```bash
sudo webinoly [option] [argument]
```

#### Options

##### Server Management
- **`-update`** - Update Webinoly to the latest version
- **`-server-reset`** - Reset server configuration
- **`-verify`** - Verify installation and configuration
- **`-uninstall`** - Remove Webinoly from server
- **`-info`** - Display server information

##### Database Management
- **`-dbpass`** - Show database credentials
- **`-mysql-password`** - Manage MySQL root password
- **`-mysql-public-access`** - Configure MySQL public access
- **`-db-import`** - Import database

##### Cache Management
- **`-clear-cache`** - Clear various caches
- **`-cache-valid`** - Configure FastCGI cache validity

##### Security & Access
- **`-tools-port`** - Change tools port
- **`-tools-site`** - Configure tools site
- **`-sftp`** - Configure SFTP access
- **`-blockip`** - Block IP addresses

##### Backup & Migration
- **`-backup`** - Create backups
- **`-send-to-s3`** - Send backups to S3
- **`-aws-s3-credentials`** - Configure AWS S3
- **`-export`** - Export configuration
- **`-import`** - Import configuration

##### Advanced Configuration
- **`-default-site`** - Set default site
- **`-external-sources-update`** - Update external sources
- **`-dynvar`** - Manage dynamic variables
- **`-custom-headers`** - Configure custom headers
- **`-skip-cache`** - Configure cache skipping
- **`-smtp`** - Configure SMTP
- **`-email`** - Configure email settings

#### Arguments

##### Server Reset Options
```bash
sudo webinoly -server-reset=all          # Reset all configurations
sudo webinoly -server-reset=nginx        # Reset Nginx configuration
sudo webinoly -server-reset=php          # Reset PHP configuration
sudo webinoly -server-reset=mysql        # Reset MySQL configuration
sudo webinoly -server-reset=os           # Reset OS configuration
sudo webinoly -server-reset=permissions  # Reset file permissions
```

##### Verification Levels
```bash
sudo webinoly -verify                    # Standard verification
sudo webinoly -verify=critical           # Critical components only
sudo webinoly -verify=all               # Complete verification
```

##### Cache Management
```bash
sudo webinoly -clear-cache=all           # Clear all caches
sudo webinoly -clear-cache=redis         # Clear Redis cache
sudo webinoly -clear-cache=memcache      # Clear Memcache
sudo webinoly -clear-cache=opcache       # Clear OPcache
sudo webinoly -clear-cache=fastcgi       # Clear FastCGI cache
sudo webinoly -clear-cache=example.com   # Clear specific site cache
```

##### Backup Options
```bash
sudo webinoly -backup=site               # Backup sites
sudo webinoly -backup=db                 # Backup databases
sudo webinoly -backup=all                # Backup everything
```

#### Examples

```bash
# Update Webinoly
sudo webinoly -update

# Verify installation
sudo webinoly -verify

# Show database passwords
sudo webinoly -dbpass

# Clear all caches
sudo webinoly -clear-cache=all

# Reset server configuration
sudo webinoly -server-reset=all

# Create backup
sudo webinoly -backup=all
```

### stack Command

Manages installation and removal of stack components.

#### Syntax
```bash
sudo stack [option] [argument]
```

#### Options

##### Stack Installation
- **`-nginx`** - Install Nginx web server
- **`-php`** - Install PHP with Nginx
- **`-mysql`** - Install MySQL/MariaDB
- **`-lemp`** - Install complete LEMP stack
- **`-html`** - Install HTML server (Nginx only)

##### Additional Tools
- **`-letsencrypt`** - Install Let's Encrypt SSL
- **`-backups`** - Install backup tools
- **`-postfix`** - Install Postfix mail server
- **`-redis`** - Install Redis cache
- **`-memcached`** - Install Memcached
- **`-pma`** - Install phpMyAdmin

##### Information & Management
- **`-info`** - Display stack information
- **`-php-ver`** - Show/change PHP version
- **`-mysql-ver`** - Show/change MySQL version
- **`-purge-server-all`** - Remove all stack components

#### Arguments

##### Purge Options
```bash
sudo stack -nginx -purge                 # Remove Nginx
sudo stack -php -purge                   # Remove PHP
sudo stack -mysql -purge                 # Remove MySQL
sudo stack -mysql -purge=keep-data       # Remove MySQL but keep data
sudo stack -purge-server-all             # Remove everything
sudo stack -purge-server-all=force       # Force removal without confirmation
```

##### Build Variations
```bash
sudo stack -lemp -build=light            # Light LEMP build
sudo stack -lemp -build=basic            # Basic LEMP build
```

##### Version Management
```bash
sudo stack -php-ver=8.3                  # Switch to PHP 8.3
sudo stack -php-ver=8.2                  # Switch to PHP 8.2
sudo stack -mysql-ver=10.6               # Set MariaDB 10.6
sudo stack -mysql-ver=8.0                # Set MySQL 8.0
```

#### Examples

```bash
# Install complete LEMP stack
sudo stack -lemp

# Install only Nginx
sudo stack -nginx

# Install PHP with existing Nginx
sudo stack -php

# Install Redis cache
sudo stack -redis

# Install Let's Encrypt
sudo stack -letsencrypt

# Remove MySQL but keep data
sudo stack -mysql -purge=keep-data

# Switch PHP version
sudo stack -php-ver=8.3

# Show stack information
sudo stack -info
```

### site Command

Creates, manages, and configures websites.

#### Syntax
```bash
sudo site [domain] [option] [argument]
```

#### Options

##### Site Types
- **`-html`** - Create HTML site
- **`-php`** - Create PHP site
- **`-mysql`** - Create MySQL site
- **`-wp`** - Create WordPress site
- **`-proxy`** - Create reverse proxy site
- **`-parked`** - Create parked domain
- **`-empty`** - Create empty site

##### Site Management
- **`-on`** - Enable site
- **`-off`** - Disable site
- **`-delete`** - Delete site
- **`-delete-all`** - Delete all sites
- **`-list`** - List all sites
- **`-info`** - Show site information

##### SSL & Security
- **`-ssl`** - Configure SSL certificate
- **`-force-redirect`** - Force HTTPS redirect
- **`-ssl-crt`** - Custom SSL certificate
- **`-ssl-key`** - Custom SSL key

##### Cache & Performance
- **`-cache`** - Configure FastCGI cache
- **`-cache-valid`** - Set cache validity
- **`-skip-cache`** - Configure cache skipping

##### WordPress Specific
- **`-multisite-convert`** - Convert to multisite
- **`-wp-cache-plugins`** - Configure WP cache plugins

##### Advanced Features
- **`-clone-from`** - Clone from another site
- **`-replace-content`** - Replace site content
- **`-redirection`** - Configure redirections
- **`-forward`** - Configure forwarding
- **`-env`** - Manage environment variables

#### Arguments

##### WordPress Configuration
```bash
# Simple WordPress installation
sudo site example.com -wp

# WordPress with custom database
sudo site example.com -wp=[setupmysql,setupwp,dbhost,dbname,dbuser,dbpass,dbpref,extdbuser,extdbpass]

# WordPress with external database
sudo site example.com -wp -external-db
```

##### MySQL Configuration
```bash
# Simple MySQL site
sudo site example.com -mysql

# MySQL with custom configuration
sudo site example.com -mysql=[dbhost,dbname,dbuser,dbpass,extdbuser,extdbpass]
```

##### SSL Configuration
```bash
sudo site example.com -ssl                    # Let's Encrypt SSL
sudo site example.com -ssl=custom             # Custom SSL
sudo site example.com -ssl -wildcard          # Wildcard certificate
sudo site example.com -ssl -test-cert         # Test certificate
```

##### Cache Configuration
```bash
sudo site example.com -cache=on               # Enable FastCGI cache
sudo site example.com -cache=off              # Disable FastCGI cache
sudo site example.com -cache-valid=1h         # Set cache validity to 1 hour
```

##### Proxy Configuration
```bash
sudo site example.com -proxy=http://localhost:3000    # Simple proxy
sudo site example.com -proxy=[http://localhost:3000,dedicated-reverse-proxy]
```

##### Subfolder Operations
```bash
sudo site example.com/blog -wp                # WordPress in subfolder
sudo site example.com/api -php                # PHP in subfolder
sudo site example.com/app -proxy=http://localhost:8080
```

##### Redirection & Forwarding
```bash
sudo site example.com -redirection=example.org           # Simple redirect
sudo site example.com -redirection=[example.org,301]     # With HTTP code
sudo site example.com -forward=example.org               # Forward traffic
```

#### Examples

```bash
# Create WordPress site
sudo site example.com -wp

# Create PHP site with SSL
sudo site example.com -php -ssl

# Create reverse proxy for Node.js app
sudo site example.com -proxy=http://localhost:3000

# Enable cache for existing site
sudo site example.com -cache=on

# Clone site
sudo site newsite.com -clone-from=example.com

# Delete site
sudo site example.com -delete

# List all sites
sudo site -list

# WordPress multisite conversion
sudo site example.com -multisite-convert

# Create HTML site in subfolder
sudo site example.com/docs -html
```

### httpauth Command

Manages HTTP Basic Authentication for sites and directories.

#### Syntax
```bash
sudo httpauth [domain] [option] [argument]
```

#### Options

##### User Management
- **`-add`** - Add authentication user
- **`-delete`** - Delete authentication user
- **`-list`** - List authentication users

##### WordPress Admin Protection
- **`-wp-admin`** - Protect WordPress admin area

##### Path Protection
- **`-path`** - Protect specific path

##### Whitelist Management
- **`-whitelist`** - Manage IP whitelist

#### Arguments

##### User Addition
```bash
sudo httpauth -add                        # Interactive user addition
sudo httpauth -add=[username,password]    # Non-interactive addition
sudo httpauth example.com -add            # Add user for specific domain
```

##### User Deletion
```bash
sudo httpauth -delete=username             # Delete specific user
sudo httpauth -delete-all                 # Delete all users
sudo httpauth example.com -delete=username
```

##### WordPress Admin Protection
```bash
sudo httpauth example.com -wp-admin=on     # Enable protection
sudo httpauth example.com -wp-admin=off    # Disable protection
```

##### Path Protection
```bash
sudo httpauth example.com -path=/admin     # Protect admin path
sudo httpauth example.com -path=/api -add=[user,pass]
```

##### Whitelist Management
```bash
sudo httpauth example.com -whitelist=add:1.2.3.4
sudo httpauth example.com -whitelist=delete:1.2.3.4
sudo httpauth example.com -whitelist=list
```

#### Examples

```bash
# Add global authentication user
sudo httpauth -add

# Add user for specific site
sudo httpauth example.com -add=[admin,secret123]

# Protect WordPress admin
sudo httpauth example.com -wp-admin=on

# Protect specific path
sudo httpauth example.com -path=/admin -add

# List all users
sudo httpauth -list

# Delete user
sudo httpauth -delete=olduser

# Whitelist IP for authenticated site
sudo httpauth example.com -whitelist=add:192.168.1.100
```

### log Command

Views and manages log files in real-time.

#### Syntax
```bash
sudo log [domain] [option] [argument]
```

#### Options

##### Log Types
- **`-access-log`** - View access logs (default)
- **`-error`** - View error logs
- **`-wp`** - View WordPress logs
- **`-php`** - View PHP-FPM logs
- **`-mysql`** - View MySQL logs
- **`-mail`** - View mail logs
- **`-ssh`** - View SSH logs
- **`-syslog`** - View system logs
- **`-le`** - View Let's Encrypt logs

##### Log Management
- **`-purge`** - Remove old log files
- **`-lines`** - Specify number of lines to display
- **`-enable`** - Enable logging
- **`-disable`** - Disable logging

#### Arguments

##### Line Control
```bash
sudo log -lines=50                        # Show last 50 lines
sudo log example.com -lines=100           # Show last 100 lines for domain
```

##### Purge Options
```bash
sudo log -purge=all                       # Remove all old logs
sudo log -purge=nginx                     # Remove Nginx logs
sudo log -purge=mysql                     # Remove MySQL logs
sudo log -purge=letsencrypt               # Remove Let's Encrypt logs
sudo log -purge=force                     # Force removal without confirmation
```

##### Enable/Disable Logging
```bash
sudo log example.com -enable              # Enable logging for domain
sudo log example.com -disable             # Disable logging for domain
```

#### Examples

```bash
# View real-time access logs
sudo log

# View error logs for specific domain
sudo log example.com -error

# View WordPress logs
sudo log example.com -wp

# View PHP-FPM logs
sudo log -php

# View last 100 lines of access logs
sudo log example.com -lines=100

# View MySQL logs
sudo log -mysql

# Remove old log files
sudo log -purge=all

# View Let's Encrypt logs
sudo log -le

# View mail logs
sudo log -mail
```

## Configuration

### Configuration File Location
```bash
/opt/webinoly/webinoly.conf
```

### Environment Variables

Webinoly supports various environment variables that can be set in the configuration file:

#### Database Configuration
- `mysql-root` - MySQL root password
- `mysql-admin` - MySQL admin user password
- `external-dbh` - External database host
- `external-dbu` - External database user
- `external-dbp` - External database password

#### Server Configuration
- `nginx-tool` - Nginx tool configuration
- `php-tool` - PHP tool configuration
- `tools-port` - Port for admin tools
- `login-www-data` - SFTP access for www-data user

#### Cache Configuration
- `fastcgi-cache` - FastCGI cache settings
- `redis-cache` - Redis cache configuration
- `memcached` - Memcached settings

### SSL Configuration

#### Let's Encrypt
```bash
# Automatic SSL certificate
sudo site example.com -ssl

# Wildcard certificate
sudo site example.com -ssl -wildcard

# Test certificate
sudo site example.com -ssl -test-cert
```

#### Custom SSL
```bash
# Custom certificate files
sudo site example.com -ssl=custom -ssl-crt=/path/to/cert.crt -ssl-key=/path/to/key.key
```

### Cache Configuration

#### FastCGI Cache
```bash
# Enable cache
sudo site example.com -cache=on

# Disable cache
sudo site example.com -cache=off

# Set cache validity
sudo site example.com -cache-valid=1h
```

#### Redis Cache
```bash
# Install Redis
sudo stack -redis

# Configure for WordPress
sudo site example.com -wp-cache-plugins=redis
```

## Advanced Usage

### WordPress Multisite

#### Convert to Multisite
```bash
sudo site example.com -multisite-convert
```

#### Domain Mapping
```bash
sudo site example.com -multisite-convert -domain-mapping-wp-id=2
```

### Reverse Proxy Configuration

#### Simple Proxy
```bash
sudo site example.com -proxy=http://localhost:3000
```

#### Advanced Proxy with Custom Headers
```bash
sudo site example.com -proxy=[http://localhost:3000,dedicated-reverse-proxy]
```

### Backup and Migration

#### Create Backup
```bash
# Backup specific site
sudo webinoly -backup=site -domain=example.com

# Backup database
sudo webinoly -backup=db -dbname=mydb

# Full server backup
sudo webinoly -backup=all
```

#### Restore from Backup
```bash
sudo webinoly -backup=restore -file=/path/to/backup.tar
```

#### S3 Integration
```bash
# Configure AWS credentials
sudo webinoly -aws-s3-credentials

# Send backup to S3
sudo webinoly -send-to-s3 -bucket=mybucket
```

### Custom Headers

```bash
# Add security headers
sudo webinoly -custom-headers=security

# Add CORS headers
sudo webinoly -custom-headers=cors
```

### IP Blocking

```bash
# Block specific IP
sudo webinoly -blockip=1.2.3.4

# Block IP range
sudo webinoly -blockip=192.168.1.0/24
```

## Examples

### Complete WordPress Setup

```bash
# Install LEMP stack
sudo stack -lemp

# Create WordPress site with SSL
sudo site example.com -wp -ssl

# Enable cache
sudo site example.com -cache=on

# Protect admin area
sudo httpauth example.com -wp-admin=on

# Install Redis for object caching
sudo stack -redis
sudo site example.com -wp-cache-plugins=redis
```

### Node.js Application Deployment

```bash
# Install Nginx only
sudo stack -nginx

# Create reverse proxy
sudo site api.example.com -proxy=http://localhost:3000

# Add SSL certificate
sudo site api.example.com -ssl

# Configure custom headers
sudo webinoly -custom-headers=cors
```

### Development Environment

```bash
# Install PHP development stack
sudo stack -php

# Create development sites
sudo site dev.local -php
sudo site api.dev.local -proxy=http://localhost:8080

# Enable detailed error logging
sudo log dev.local -enable
```

### Production Server Setup

```bash
# Install complete LEMP with additional tools
sudo stack -lemp
sudo stack -redis
sudo stack -letsencrypt
sudo stack -backups

# Create production site
sudo site example.com -wp -ssl

# Configure caching
sudo site example.com -cache=on
sudo site example.com -wp-cache-plugins=redis

# Set up authentication
sudo httpauth example.com -wp-admin=on

# Configure backups
sudo webinoly -aws-s3-credentials
sudo webinoly -backup=all
```

## Troubleshooting

### Common Issues

#### Installation Problems

1. **Ubuntu Version Not Supported**
   ```bash
   # Check Ubuntu version
   lsb_release -a
   
   # Supported: 22.04 (Jammy), 24.04 (Noble)
   ```

2. **Permission Denied**
   ```bash
   # Ensure running with sudo
   sudo webinoly -verify
   ```

3. **Network Issues**
   ```bash
   # Check internet connection
   ping -c 4 8.8.8.8
   
   # Update package sources
   sudo apt update
   ```

#### Site Issues

1. **Site Not Loading**
   ```bash
   # Check Nginx status
   sudo systemctl status nginx
   
   # Verify site configuration
   sudo nginx -t
   
   # Check site is enabled
   sudo site -list
   ```

2. **SSL Certificate Problems**
   ```bash
   # Check Let's Encrypt logs
   sudo log -le
   
   # Verify certificate
   sudo site example.com -ssl -info
   ```

3. **Database Connection Issues**
   ```bash
   # Check MySQL status
   sudo systemctl status mysql
   
   # Verify database credentials
   sudo webinoly -dbpass
   ```

#### Performance Issues

1. **Slow Site Loading**
   ```bash
   # Enable caching
   sudo site example.com -cache=on
   
   # Install Redis
   sudo stack -redis
   
   # Check error logs
   sudo log example.com -error
   ```

2. **High Memory Usage**
   ```bash
   # Monitor processes
   htop
   
   # Clear caches
   sudo webinoly -clear-cache=all
   ```

### Log Analysis

#### Check Error Logs
```bash
# Nginx error logs
sudo log example.com -error

# PHP error logs
sudo log -php

# System logs
sudo log -syslog
```

#### Monitor Access Logs
```bash
# Real-time access logs
sudo log example.com

# Last 100 entries
sudo log example.com -lines=100
```

### Recovery Procedures

#### Reset Configuration
```bash
# Reset all configurations
sudo webinoly -server-reset=all

# Reset specific components
sudo webinoly -server-reset=nginx
sudo webinoly -server-reset=php
sudo webinoly -server-reset=mysql
```

#### Reinstall Components
```bash
# Reinstall Nginx
sudo stack -nginx -purge
sudo stack -nginx

# Reinstall PHP
sudo stack -php -purge
sudo stack -php
```

#### Restore from Backup
```bash
# List available backups
sudo webinoly -backup -list

# Restore specific backup
sudo webinoly -backup=restore -file=/path/to/backup.tar
```

### Getting Help

1. **Official Documentation**: https://webinoly.com/documentation/
2. **Community Support**: https://webinoly.com/premium/
3. **GitHub Issues**: https://github.com/QROkes/webinoly/issues
4. **Twitter**: [@Webinoly](https://x.com/Webinoly)

### Verification Commands

```bash
# Verify installation
sudo webinoly -verify

# Check all components
sudo webinoly -verify=all

# Critical verification only
sudo webinoly -verify=critical

# Show system information
sudo webinoly -info
sudo stack -info
```

---

*This documentation covers Webinoly v1.19+ features. For the latest updates, visit [webinoly.com](https://webinoly.com/)*
