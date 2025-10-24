# Jaztech WordPress

High-performance WordPress + MariaDB template for Coolify. Fixes 413 upload errors and adds WP-CLI.

![WordPress](https://img.shields.io/badge/WordPress-latest-blue)
![MariaDB](https://img.shields.io/badge/MariaDB-11-blue)

![Coolify](https://img.shields.io/badge/Coolify-Ready-green)
![Production](https://img.shields.io/badge/Production-Ready-orange)
![Live Example](https://img.shields.io/badge/Live%20Example-jasonrouet.com-blue)

## Features

- **512M uploads** (vs 2M default) - No more 413 errors
- **600s execution** (vs 30s default) - Large imports/exports  
- **512M memory** (vs 128M default) - Better performance
- **10,000 variables** (vs 1000 default) - Large forms support
- **OPCache enabled** - Production performance
- **WP-CLI included** - Command line interface
- **Native php.ini** - More robust than .htaccess

## Quick Deploy

1. **Create resource in Coolify**
   ```
   Dashboard → Projects → + Add New Resource → Public Repository
   ```

2. **Repository configuration**
   - Repository URL: `https://github.com/jaz-on/jaztech-wordpress`
   - Build Pack: `Docker Compose`
   - Click Deploy

3. **Configure PHP (one time)**
   - Go to **Persistent Storages** → Find `wordpress.ini`
   - **Convert to file** → Confirm with filepath
   - **Edit** → Paste content from `wordpress.ini` in this repo
   - **Save & Restart**

Done. Your WordPress is ready with optimized limits.

## 🚀 Live Example

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

## Troubleshooting

**uploads.ini not applied?**
- Ensure file is converted to "file" (not directory)
- Content pasted correctly
- Service restarted after modification

**413 error persists?**
- Check PHP config with `phpinfo()`
- Restart service completely

## License

MIT License - see [LICENSE](LICENSE)

## Author & support

Jason Rouet - [jasonrouet.com](https://jasonrouet.com)

If this template helps you, consider supporting my work:

[![Ko-fi](https://img.shields.io/badge/Ko--fi-Support%20me-red?logo=ko-fi&style=for-the-badge)](https://ko-fi.com/jasonrouet)