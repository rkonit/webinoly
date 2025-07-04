# Webinoly Command Reference - Complete Arguments Guide

## webinoly Command

### Syntax
```bash
sudo webinoly [option] [argument]
```

### Complete Options List

#### Server Management
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-update` | none | Update Webinoly to latest version | `sudo webinoly -update` |
| `-server-reset` | `all`, `os`, `nginx`, `php`, `mysql`, `permissions` | Reset server configurations | `sudo webinoly -server-reset=nginx` |
| `-verify` | `critical`, `all`, none | Verify installation integrity | `sudo webinoly -verify=critical` |
| `-uninstall` | none | Remove Webinoly completely | `sudo webinoly -uninstall` |
| `-info` | none | Display server information | `sudo webinoly -info` |
| `-version` | none | Show Webinoly version | `sudo webinoly -version` |

#### Database Management
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-dbpass` | none | Show database credentials | `sudo webinoly -dbpass` |
| `-mysql-password` | `[oldpass,newpass]` | Change MySQL root password | `sudo webinoly -mysql-password=[old,new]` |
| `-mysql-public-access` | `on`, `off` | Enable/disable MySQL public access | `sudo webinoly -mysql-public-access=on` |
| `-db-import` | `-file=path`, `-dbname=name`, `-overwrite` | Import database from file | `sudo webinoly -db-import -file=/path/db.sql` |

#### Cache Management
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-clear-cache` | `all`, `redis`, `memcache`, `memcached`, `opcache`, `fastcgi`, `[domain]` | Clear various caches | `sudo webinoly -clear-cache=redis` |
| `-cache-valid` | `1m`, `5m`, `1h`, `1d`, `1w`, `1M`, `1y` | Set FastCGI cache validity | `sudo webinoly -cache-valid=1h` |

#### Tools & Ports
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-tools-port` | `1-65535` | Change admin tools port | `sudo webinoly -tools-port=8080` |
| `-tools-site` | `domain` | Set tools site domain | `sudo webinoly -tools-site=admin.example.com` |
| `-default-site` | `domain` | Set default site | `sudo webinoly -default-site=example.com` |

#### Security & Access
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-sftp` | `on`, `off` | Configure SFTP access for www-data | `sudo webinoly -sftp=on` |
| `-login-www-data` | `on`, `off` | Same as -sftp | `sudo webinoly -login-www-data=on` |
| `-blockip` | `IP`, `IP/CIDR`, `-delete=IP` | Block/unblock IP addresses | `sudo webinoly -blockip=1.2.3.4` |

#### Backup & Migration
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-backup` | See backup arguments below | Create backups | `sudo webinoly -backup=all` |
| `-send-to-s3` | `-bucket=name` | Send backup to S3 | `sudo webinoly -send-to-s3 -bucket=mybucket` |
| `-aws-s3-credentials` | `[key,secret,region]` | Configure AWS S3 | `sudo webinoly -aws-s3-credentials=[key,secret,us-east-1]` |
| `-export` | `-file=path` | Export configuration | `sudo webinoly -export -file=/path/config.tar` |
| `-import` | `-file=path` | Import configuration | `sudo webinoly -import -file=/path/config.tar` |

#### Content & Headers
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-custom-headers` | `security`, `cors`, `cache` | Add custom headers | `sudo webinoly -custom-headers=security` |
| `-skip-cache` | `[paths]` | Configure cache skip paths | `sudo webinoly -skip-cache=[/admin,/api]` |
| `-skip-cookie-cache` | `[cookies]` | Skip cache for cookies | `sudo webinoly -skip-cookie-cache=[auth,session]` |
| `-query-string-cache` | `[params]` | Cache with query strings | `sudo webinoly -query-string-cache=[page,id]` |
| `-query-string-never-cache` | `[params]` | Never cache query strings | `sudo webinoly -query-string-never-cache=[debug,test]` |

#### Communication
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-smtp` | `[host,port,user,pass,encryption]` | Configure SMTP | `sudo webinoly -smtp=[smtp.gmail.com,587,user,pass,tls]` |
| `-email` | `email@domain.com` | Set admin email | `sudo webinoly -email=admin@example.com` |

#### Advanced
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-dynvar` | `-value=val`, `-bind=var` | Manage dynamic variables | `sudo webinoly -dynvar=myvar -value=123` |
| `-external-sources-update` | none | Update external sources | `sudo webinoly -external-sources-update` |
| `-timezone` | `timezone` | Set system timezone | `sudo webinoly -timezone=America/New_York` |

### Backup Arguments Detail

| Argument | Values | Description | Example |
|----------|--------|-------------|---------|
| `-backup` | `all`, `site`, `db`, `restore` | Backup type | `sudo webinoly -backup=all` |
| `-profile` | `profile_name` | Backup profile | `sudo webinoly -backup=all -profile=daily` |
| `-destination` | `/path/to/dest` | Backup destination | `sudo webinoly -backup=all -destination=/backups` |
| `-source` | `/path/to/source` | Restore source | `sudo webinoly -backup=restore -source=/backups/backup.tar` |
| `-delete` | none | Delete after backup | `sudo webinoly -backup=all -delete` |
| `-delete-all` | none | Delete all old backups | `sudo webinoly -backup=all -delete-all` |
| `-run` | `profile_name` | Run backup profile | `sudo webinoly -backup -run=daily` |
| `-wp` | none | WordPress specific backup | `sudo webinoly -backup=site -wp` |
| `-date` | `YYYY-MM-DD` | Backup date filter | `sudo webinoly -backup=restore -date=2024-01-01` |
| `-s3-european-buckets` | none | Use EU S3 buckets | `sudo webinoly -backup=all -s3-european-buckets` |
| `-filename` | `name` | Custom backup filename | `sudo webinoly -backup=all -filename=mybackup` |
| `-overwrite` | none | Overwrite existing backup | `sudo webinoly -backup=all -overwrite` |
| `-no-recovery` | none | No recovery info | `sudo webinoly -backup=all -no-recovery` |
| `-recalculate` | none | Recalculate backup sizes | `sudo webinoly -backup -recalculate` |
| `-skip-db` | none | Skip database backup | `sudo webinoly -backup=site -skip-db` |

---

## stack Command

### Syntax
```bash
sudo stack [option] [argument]
```

### Complete Options List

#### Stack Components
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-html` | `-purge`, `-build=light/basic` | HTML server (Nginx only) | `sudo stack -html` |
| `-nginx` | `-purge`, `-build=light/basic` | Nginx web server | `sudo stack -nginx` |
| `-php` | `-purge`, `-build=light/basic`, `force` | PHP with Nginx | `sudo stack -php` |
| `-mysql` | `-purge`, `-purge=keep-data` | MySQL/MariaDB database | `sudo stack -mysql` |
| `-lemp` | `-purge`, `-build=light/basic` | Complete LEMP stack | `sudo stack -lemp` |

#### Additional Tools
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-letsencrypt` | `-purge`, `-purge=force` | Let's Encrypt SSL | `sudo stack -letsencrypt` |
| `-backups` | `-purge`, `-purge=force` | Backup tools | `sudo stack -backups` |
| `-postfix` | `-purge` | Postfix mail server | `sudo stack -postfix` |
| `-redis` | `-purge` | Redis cache server | `sudo stack -redis` |
| `-memcached` | `-purge` | Memcached server | `sudo stack -memcached` |
| `-pma` | `-purge` | phpMyAdmin | `sudo stack -pma` |

#### Information & Management
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-info` | none | Show stack information | `sudo stack -info` |
| `-purge-server-all` | `force` | Remove all components | `sudo stack -purge-server-all` |

#### Version Management
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-php-ver` | `8.4`, `8.3`, `8.2`, `8.1`, `8.0`, `7.4` | PHP version management | `sudo stack -php-ver=8.3` |
| `-mysql-ver` | `10.6`, `10.5`, `10.4`, `8.0`, `5.7` | MySQL version management | `sudo stack -mysql-ver=10.6` |

### Build Arguments
| Argument | Values | Description | Example |
|----------|--------|-------------|---------|
| `-build` | `light`, `basic` | Installation build type | `sudo stack -lemp -build=light` |
| `-purge` | none, `force`, `keep-data` | Removal options | `sudo stack -mysql -purge=keep-data` |

---

## site Command

### Syntax
```bash
sudo site [domain] [option] [argument]
```

### Complete Options List

#### Site Creation Types
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-html` | none | Static HTML site | `sudo site example.com -html` |
| `-php` | none | PHP site | `sudo site example.com -php` |
| `-mysql` | Custom DB config | MySQL site | `sudo site example.com -mysql` |
| `-wp` | WordPress config | WordPress site | `sudo site example.com -wp` |
| `-proxy` | `http://host:port` | Reverse proxy site | `sudo site example.com -proxy=http://localhost:3000` |
| `-parked` | none | Parked domain | `sudo site example.com -parked` |
| `-empty` | `blank` | Empty site template | `sudo site example.com -empty` |

#### Site Management
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-on` | none | Enable site | `sudo site example.com -on` |
| `-off` | none | Disable site | `sudo site example.com -off` |
| `-delete` | none | Delete site | `sudo site example.com -delete` |
| `-delete-all` | none | Delete all sites | `sudo site -delete-all` |
| `-list` | none | List all sites | `sudo site -list` |
| `-info` | none | Show site information | `sudo site example.com -info` |

#### SSL Configuration
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-ssl` | `custom`, none | SSL certificate | `sudo site example.com -ssl` |
| `-ssl-crt` | `/path/to/cert.crt` | Custom SSL certificate | `sudo site example.com -ssl=custom -ssl-crt=/path/cert.crt` |
| `-ssl-key` | `/path/to/key.key` | Custom SSL key | `sudo site example.com -ssl=custom -ssl-key=/path/key.key` |
| `-force-redirect` | none | Force HTTPS redirect | `sudo site example.com -force-redirect` |

#### Cache & Performance
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-cache` | `on`, `off` | FastCGI cache control | `sudo site example.com -cache=on` |
| `-cache-valid` | `1m`, `5m`, `1h`, `1d`, `1w`, `1M`, `1y` | Cache validity period | `sudo site example.com -cache-valid=1h` |
| `-skip-cache` | `[paths]` | Paths to skip cache | `sudo site example.com -skip-cache=[/admin,/api]` |
| `-skip-cookie-cache` | `[cookies]` | Cookies to skip cache | `sudo site example.com -skip-cookie-cache=[auth,session]` |
| `-query-string-cache` | `[params]` | Query strings for cache | `sudo site example.com -query-string-cache=[page,id]` |
| `-query-string-never-cache` | `[params]` | Query strings never cache | `sudo site example.com -query-string-never-cache=[debug]` |
| `-query-string-cache-default` | none | Reset to default cache rules | `sudo site example.com -query-string-cache-default` |

#### WordPress Specific
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-multisite-convert` | none | Convert to multisite | `sudo site example.com -multisite-convert` |
| `-wp-cache-plugins` | `redis`, `memcached` | WP cache plugins | `sudo site example.com -wp-cache-plugins=redis` |
| `-domain-mapping-wp-id` | `ID` | Domain mapping WP ID | `sudo site example.com -domain-mapping-wp-id=2` |

#### Advanced Features
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-clone-from` | `source_domain` | Clone from existing site | `sudo site new.com -clone-from=old.com` |
| `-replace-content` | `[old,new]` | Replace content in site | `sudo site example.com -replace-content=[old.com,new.com]` |
| `-redirection` | `target`, `[target,code]` | Setup redirections | `sudo site example.com -redirection=new.com` |
| `-forward` | `target_domain` | Forward traffic | `sudo site example.com -forward=new.com` |
| `-env` | `[var=value]` | Environment variables | `sudo site example.com -env=[DB_HOST=localhost]` |

### WordPress Configuration Arguments

#### Simple WordPress
```bash
sudo site example.com -wp
```

#### Custom WordPress Configuration
```bash
sudo site example.com -wp=[setupmysql,setupwp,dbhost,dbname,dbuser,dbpass,dbpref,extdbuser,extdbpass]
```

| Parameter | Values | Description |
|-----------|--------|-------------|
| `setupmysql` | `true`, `false` | Create MySQL database |
| `setupwp` | `true`, `false` | Install WordPress |
| `dbhost` | `hostname:port` | Database host |
| `dbname` | `database_name` | Database name |
| `dbuser` | `username` | Database user |
| `dbpass` | `password`, `random` | Database password |
| `dbpref` | `wp_`, `custom_` | Table prefix |
| `extdbuser` | `username` | External DB user |
| `extdbpass` | `password` | External DB password |

### MySQL Site Configuration
```bash
sudo site example.com -mysql=[dbhost,dbname,dbuser,dbpass,extdbuser,extdbpass]
```

### Proxy Configuration Arguments

#### Simple Proxy
```bash
sudo site example.com -proxy=http://localhost:3000
```

#### Advanced Proxy
```bash
sudo site example.com -proxy=[http://localhost:3000,dedicated-reverse-proxy]
```

### SSL Arguments

| Argument | Values | Description | Example |
|----------|--------|-------------|---------|
| `-wildcard` | none | Wildcard certificate | `sudo site example.com -ssl -wildcard` |
| `-test-cert` | none | Test certificate | `sudo site example.com -ssl -test-cert` |
| `-revoke` | none | Revoke certificate | `sudo site example.com -ssl -revoke` |
| `-ignore-ssl` | none | Ignore SSL in operations | `sudo site example.com -clone-from=other.com -ignore-ssl` |

### Advanced Arguments

| Argument | Values | Description | Example |
|----------|--------|-------------|---------|
| `-root` | `/custom/path` | Custom document root | `sudo site example.com -php -root=/app/public` |
| `-root-path` | `/custom/path` | Same as -root | `sudo site example.com -php -root-path=/app/public` |
| `-subfolder` | `/path` | Subfolder installation | `sudo site example.com/blog -wp` |
| `-subdomain` | none | Force subdomain | `sudo site sub.example.com -subdomain` |
| `-external-db` | none | Use external database | `sudo site example.com -wp -external-db` |
| `-manual` | none | Manual configuration | `sudo site example.com -ssl -manual` |
| `-overwrite` | none | Overwrite existing | `sudo site example.com -wp -overwrite` |
| `-dedicated-reverse-proxy` | none | Dedicated proxy config | `sudo site example.com -proxy=http://localhost:3000 -dedicated-reverse-proxy` |
| `-reset` | none | Reset configuration | `sudo site example.com -cache -reset` |
| `-db-role` | `admin`, `user` | Database role | `sudo site example.com -mysql -db-role=admin` |

### Redirection Arguments

| Argument | Values | Description | Example |
|----------|--------|-------------|---------|
| `-from` | `source_path` | Redirect from path | `sudo site example.com -redirection=/old -from=/old -to=/new` |
| `-to` | `target_path` | Redirect to path | `sudo site example.com -redirection=/old -to=/new` |
| `-http-code` | `301`, `302`, `303`, `307`, `308` | HTTP redirect code | `sudo site example.com -redirection=new.com -http-code=301` |
| `-regex` | none | Use regex in redirect | `sudo site example.com -redirection -regex` |

---

## httpauth Command

### Syntax
```bash
sudo httpauth [domain] [option] [argument]
```

### Complete Options List

#### User Management
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-add` | `[username,password]`, none | Add authentication user | `sudo httpauth -add=[user,pass]` |
| `-delete` | `username`, `-delete-all` | Delete user(s) | `sudo httpauth -delete=user` |
| `-list` | none | List all users | `sudo httpauth -list` |

#### WordPress Protection
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-wp-admin` | `on`, `off` | Protect WordPress admin | `sudo httpauth example.com -wp-admin=on` |

#### Path Protection
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-path` | `/path` | Protect specific path | `sudo httpauth example.com -path=/admin` |

#### Whitelist Management
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-whitelist` | `add:IP`, `delete:IP`, `list` | Manage IP whitelist | `sudo httpauth example.com -whitelist=add:1.2.3.4` |

### User Addition Arguments
```bash
# Interactive
sudo httpauth -add

# Non-interactive
sudo httpauth -add=[username,password]

# For specific domain
sudo httpauth example.com -add=[username,password]
```

### Whitelist Arguments
| Format | Description | Example |
|--------|-------------|---------|
| `add:IP` | Add IP to whitelist | `sudo httpauth example.com -whitelist=add:192.168.1.100` |
| `delete:IP` | Remove IP from whitelist | `sudo httpauth example.com -whitelist=delete:192.168.1.100` |
| `list` | List whitelisted IPs | `sudo httpauth example.com -whitelist=list` |

---

## log Command

### Syntax
```bash
sudo log [domain] [option] [argument]
```

### Complete Options List

#### Log Types
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| none | none | Access logs (default) | `sudo log example.com` |
| `-access-log` | none | Access logs | `sudo log example.com -access-log` |
| `-error` | none | Error logs | `sudo log example.com -error` |
| `-wp` | none | WordPress logs | `sudo log example.com -wp` |
| `-php` | none | PHP-FPM logs | `sudo log -php` |
| `-fpm` | none | Same as -php | `sudo log -fpm` |
| `-mysql` | none | MySQL logs | `sudo log -mysql` |
| `-mail` | none | Mail logs | `sudo log -mail` |
| `-email` | none | Same as -mail | `sudo log -email` |
| `-ssh` | none | SSH logs | `sudo log -ssh` |
| `-syslog` | none | System logs | `sudo log -syslog` |
| `-le` | none | Let's Encrypt logs | `sudo log -le` |

#### Log Management
| Option | Arguments | Description | Example |
|--------|-----------|-------------|---------|
| `-purge` | See purge arguments | Remove old logs | `sudo log -purge=all` |
| `-lines` | `number` | Lines to display | `sudo log example.com -lines=100` |
| `-enable` | none | Enable logging | `sudo log example.com -enable` |
| `-disable` | none | Disable logging | `sudo log example.com -disable` |
| `-display` | none | Display log info | `sudo log example.com -display` |

### Purge Arguments
| Value | Description | Example |
|-------|-------------|---------|
| `all` | Remove all old logs | `sudo log -purge=all` |
| `nginx` | Remove Nginx logs | `sudo log -purge=nginx` |
| `letsencrypt` | Remove Let's Encrypt logs | `sudo log -purge=letsencrypt` |
| `mysql` | Remove MySQL logs | `sudo log -purge=mysql` |
| `redis` | Remove Redis logs | `sudo log -purge=redis` |
| `force` | Force removal without confirmation | `sudo log -purge=force` |

### Lines Argument
```bash
sudo log example.com -lines=50          # Show last 50 lines
sudo log -php -lines=200                # Show last 200 PHP log lines
```

---

## Common Argument Patterns

### Time/Duration Values
Used in cache validity, backup retention, etc.:
- `1m` - 1 minute
- `5m` - 5 minutes  
- `1h` - 1 hour
- `6h` - 6 hours
- `1d` - 1 day
- `1w` - 1 week
- `1M` - 1 month
- `1y` - 1 year

### Boolean Values
- `true` - Enable/Yes
- `false` - Disable/No
- `on` - Enable
- `off` - Disable

### IP Address Formats
- Single IP: `192.168.1.100`
- CIDR notation: `192.168.1.0/24`
- IPv6: `2001:db8::1`

### Array Formats
Used for multiple values:
- `[value1,value2,value3]` - Comma-separated in brackets
- Example: `[/admin,/api,/private]`

### Path Formats
- Absolute paths: `/var/www/html`
- Relative paths: `./files`
- URL paths: `/admin/login`

## Global Arguments

These arguments can be used with multiple commands:

| Argument | Commands | Description |
|----------|----------|-------------|
| `-subfolder` | `site`, `httpauth` | Work with subfolders |
| `-force` | Various | Force operation without confirmation |
| `-overwrite` | Various | Overwrite existing files/configs |
| `-list` | Various | List items |
| `-info` | Various | Show information |
| `-help` | All | Show help information |
