# wp-coolify

High-performance WordPress + MariaDB template for Coolify with security hardening and performance optimizations.

![WordPress](https://img.shields.io/badge/WordPress-latest-blue)
![MariaDB](https://img.shields.io/badge/MariaDB-11-blue)

![Coolify](https://img.shields.io/badge/Coolify-Ready-green)
![Production](https://img.shields.io/badge/Production-Ready-orange)
![Live Example](https://img.shields.io/badge/Live%20Example-jasonrouet.com-blue)

## Features

- **256M uploads** (vs 2M default) - No more 413 errors
- **300s execution** (vs 30s default) - Large imports/exports
- **256M memory** (vs 128M default) - Better performance
- **5,000 variables** (vs 1000 default) - Large forms support
- **OPCache enabled** - Production performance
- **WP-CLI included** - Command line interface
- **Security hardened** - File editing disabled, secure sessions
- **Version pinned** - Reproducible deployments
- **Resource limits** - Prevents resource exhaustion

## Quick Deploy

1. **Create resource in Coolify**
   ```
   Dashboard → Projects → + Add New Resource → Public Repository
   ```

2. **Repository configuration**
   - Repository URL: `https://github.com/jaz-on/wp-coolify`
   - Build Pack: `Docker Compose`
   - Click Deploy

3. **Configure PHP (one time)**
   - Go to **Persistent Storages** → Find `uploads.ini`
   - **Convert to file** → Confirm with filepath
   - **Edit** → Paste content from `uploads.ini` in this repo
   - **Save & Restart**

Done. Your secure WordPress is ready.

## Live Example

This template powers:
- **[jasonrouet.com](https://jasonrouet.com)** - Personal site running on Coolify
- Deployed with this exact template
- Monitored with Prometheus + Grafana stack

## WP-CLI Usage

Access via Coolify Terminal:
```bash
docker exec -it [container-id] wp --info
wp core update
wp plugin list
wp search-replace old-domain.com new-domain.com
```

## vs Official Template

| Setting | Official | This Template |
|---|---|---|
| **Upload max** | 2M (413 errors) | **256M** |
| **Execution time** | 30s | **300s** |
| **Memory limit** | 128M | **256M** |
| **File editing** | Enabled (risk) | **Disabled** |
| **Auto updates** | Enabled (risk) | **Disabled** |
| **Version** | `latest` (unstable) | **Pinned** |
| **Resource limits** | None | **Configured** |

## Security Features

- File editing disabled via wp-config
- Automatic updates disabled (manual control)
- Secure session configuration
- PHP functions blacklisted
- Resource limits prevent DoS
- Version pinning prevents supply chain attacks

## Advanced Configuration

### Persistent volumes
- `wordpress-files` - WordPress files (/var/www/html)
- `mariadb-data` - Database (/var/lib/mysql)
- `uploads.ini` - PHP config (after conversion)

### Available environment variables
Coolify auto-generates:
- `$SERVICE_USER_WORDPRESS` - MySQL user
- `$SERVICE_PASSWORD_WORDPRESS` - MySQL password
- `$SERVICE_PASSWORD_ROOT` - MySQL root password
- `$SERVICE_FQDN_WORDPRESS` - WordPress domain

## Troubleshooting

**uploads.ini not applied?**
- Ensure file is converted to "file" (not directory)
- Content pasted correctly
- Service restarted after modification

**413 error persists?**
- Check PHP config with phpinfo()
- Restart service completely

**Performance issues?**
- Monitor resources via Coolify
- Check OPCache status in WordPress admin

## License

MIT License - see [LICENSE](LICENSE)

## Author & Support

Jason Rouet - [jasonrouet.com](https://jasonrouet.com)

If this template helps you, consider supporting my work:

[![Ko-fi](https://img.shields.io/badge/Ko--fi-Support%20me-red?logo=ko-fi&style=for-the-badge)](https://ko-fi.com/jasonrouet)
