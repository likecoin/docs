---
description: Software Changes that you are expected to see in the new upgrade to FoTan
---

# Software Changes Overview

### liked & likecli

* `liked` and `likecli` commands are combined into one single command \(`liked`\).
* Key storage format changed, so storage moved into `.liked` and any access \(including listing keys\) needs to provide the password .
  * Multiple keyring backends are supported from `--keyring-backend` parameter, however if using under Docker then only traditional file storage will be supported. You may compile standalone `liked` executable for other backends if needed.
* As `likecli` is gone, lite client does not go with standalone process anymore, the API server need to be enabled in `app.toml` from the chain node instead.

### transactions & queries

* Balance is moved into the `bank` module, so you may need `liked query bank balances` instead of `likecli query account`.
* Many old APIs are deprecated. See [https://v1.cosmos.network/rpc/v0.41.4](https://v1.cosmos.network/rpc/v0.41.4) for details.

### Docker setup

* In sheungwan, we used separate Docker images for root and non-root. Turns out it is not necessary as Docker and Docker-Compose can specify the runtime user, so in fotan the images are unified. As consequence `LIKECOIN_UID` is introduced in `.env`.
* Variables \(seed nodes, users\) are specified in the `.env` file.
* Commands are now running by `docker-compose run` so configs in `docker-compose.yml` \(e.g. volumes, users\) could be reused and no need to re-type every time.

### scripts

* Scripts are rewritten and combined with Docker Compose profiles \(which is why we now require Docker Compose ≥1.28\).

