# Whoogle Search 🔍

A self-hosted, ad-free, privacy-respecting metasearch engine that acts as a Google search proxy.

## Overview

Whoogle Search provides Google search results without ads, JavaScript, AMP links, cookies, or IP address tracking. It's a lightweight solution for privacy-conscious users who want clean search results.

## Features

- 🚫 **No Ads** - Clean search results without advertisements
- 🔒 **Privacy First** - No tracking, cookies, or IP logging
- ⚡ **Fast & Lightweight** - Minimal resource usage
- 🌐 **Self-Hosted** - Complete control over your search experience
- 🎨 **Customizable** - Multiple themes and configuration options
- 🔍 **Google Results** - Powered by Google's search index
- 🖼️ **Image Search** - Full Google Images support with privacy protection
- 🛡️ **Security** - Built-in CSP and secure configuration
- 🧅 **Tor Ready** - Pre-configured for enhanced anonymity

## Quick Start

1. **Start the service:**
   ```bash
   docker-compose up -d
   ```

2. **Access Whoogle:**
   - Open your browser to: `http://172.17.0.1:61004`

3. **Stop the service:**
   ```bash
   docker-compose down
   ```

## Configuration

The service is pre-configured with optimal privacy settings:

- **Theme:** Dark mode enabled
- **Results:** 20 results per page
- **Country:** United States
- **Language:** English
- **Image Search:** Fully enabled with alternative image sources
- **Privacy Features:** Ad blocking, safe browsing enabled
- **Security:** CSP headers and content filtering active
- **Tor Support:** Ready for enhanced anonymity (tmpfs configured)

## Health Monitoring

The container includes built-in health checks that monitor service availability every 30 seconds.

## Data Persistence

Configuration data is stored in `./rootfs/config/whoogle` and will persist between container restarts.

## Author

🤖 **casjay** - [GitHub](https://github.com/casjay) 🤖

## License

See [LICENSE.md](LICENSE.md) for licensing information.
