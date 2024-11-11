# Deploy Jellyfin

Part of the [*Komodo Hub* collection.](https://github.com/komodo-hub/komodo-hub)

Runs Jellyfin media server.

https://jellyfin.org/docs/general/installation/container#using-docker-compose

## Komodo Resource TOML

```toml
[[stack]]
name = "jellyfin"
[stack.config]
repo = "komodo-hub/deploy-jellyfin"
file_paths = [
  "compose.yaml",
  # "caddy.compose.yaml" # Deploy https proxy
]
environment = """
  ## Required
  MEDIA_PATH = /path/to/media

  ## Optional
  # CONFIG_PATH = /path/to/config
  # CACHE_PATH = /path/to/cache
  # JELLYFIN_PublishedServerUrl = https://jellyfin.example.com

  JELLYFIN_PORT = 8096
  JELLYFIN_TAG = latest
  RESTART = unless-stopped
  NETWORK_MODE = bridge
  LOGGING_DRIVER = local
  UID = 0
  GID = 0
"""
```