---
description: Software Changes that you are expected to see in the new upgrade to FoTan
---

# Software Changes Overview

### liked & likecli

* `liked` and `likecli` commands are combined into one single command \(`liked`\).
* Key storage format changed,  storage is moved into `.liked`, any access \(including listing keys\) would require user  to provide the key vault password .
  * Multiple keyring backends are supported from `--keyring-backend` parameter, however when using Docker, only traditional file storage will be supported. You may compile standalone `liked` executable for other backends if needed.
* As `likecli` is gone, lite client does not have a standalone process anymore. API server would need to be manually enabled in `app.toml` from the chain node.

### Transactions & Queries

* Balance is moved into the `bank` module, so you may need  to run`liked query bank balances` instead of `likecli query account`.
* Many old APIs are deprecated. See [https://v1.cosmos.network/rpc/v0.41.4](https://v1.cosmos.network/rpc/v0.41.4) for details.

### Docker setup

* In SheungWan, we used separate Docker images for root and non-root. Turns out it is not necessary, as Docker and Docker-Compose can specify the runtime user. So in FoTan the images are unified, and `LIKECOIN_UID` is introduced in `.env`.
* Variables \(`seed nodes`, `users`\) are specified in the `.env` file.
* Commands are now run by `docker-compose run` , so configs in `docker-compose.yml` \(e.g. `volumes`, `users`\) could be reused. no need to re-type every time.

### Scripts

* Scripts are rewritten and combined with Docker Compose profiles \(We now require Docker Compose ≥1.28\).

