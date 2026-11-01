## 👋 Welcome to whoogle 🚀

Self-hosted Google search front end with Tor support

## 📋 Description

Whoogle is a self-hostable Google search front end that returns results
without tracking, ads, or Google cookies. This stack runs the official
Whoogle container, including its bundled Tor support, behind the host
nginx proxy.

## 🚀 Services

- **app**: benbusby/whoogle-search:latest

## 📦 Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/whoogle/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/whoogle" ~/.local/srv/docker/whoogle
cd ~/.local/srv/docker/whoogle
cp default.env .env
docker compose --env-file .env up -d
```

### Option 3: Using composemgr
```bash
composemgr install whoogle
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=America/New_York
APP_SECRET_KEY=replace-with-a-random-32-byte-hex-string
WHOOGLE_CONFIG_COUNTRY=US
WHOOGLE_CONFIG_THEME=dark
WHOOGLE_PROXY_TYPE=
```

See `docker-compose.yaml` for complete list of configurable options.

### Environment Files

`default.env.sample` holds the full set of variables and is copied to `.env`
before starting the stack:

```bash
cp default.env .env
docker compose --env-file .env up -d
```

`app.env.sample` holds the app-specific overrides and is copied to `app.env`:

```bash
cp app.env.sample app.env
```

`composemgr up` applies `app.env` and `default.env` automatically. Raw
`docker compose` commands need `--env-file .env` to pick up the same values.

### Reverse Proxy

Three standalone compose files ship in this repo:

| File | Use |
|------|-----|
| `docker-compose.yaml` | Default, published on `172.17.0.1:64387` |
| `docker-compose.traefik.yaml` | Behind an existing external `traefik` network |
| `docker-compose.tunnel.yaml` | Behind an existing external `cloudflare` tunnel network |

```bash
docker compose -f docker-compose.traefik.yaml --env-file .env up -d
```

## 🌐 Access

- **Web Interface**: http://172.17.0.1:64387

## 📂 Volumes

- `./volumes/config/whoogle` - Whoogle configuration directory

## 🔐 Security

- Set `APP_SECRET_KEY` to a random 32 character or longer value, it encrypts
  saved search preferences
- `HTTPS_ONLY` and `WHOOGLE_CSP` are enabled by default, keep them that way
  behind a reverse proxy
- Use HTTPS via the reverse proxy in production
- Regularly update Docker images for security patches

## 🔍 Logging

```shell
docker compose --env-file .env logs -f app
```

## 🛠️ Management

```bash
# Start services
docker compose --env-file .env up -d

# Stop services
docker compose --env-file .env down

# Update to latest images
docker compose --env-file .env pull && docker compose --env-file .env up -d

# View logs
docker compose --env-file .env logs -f

# Restart services
docker compose --env-file .env restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+
- Enough memory for the bundled Tor process

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
