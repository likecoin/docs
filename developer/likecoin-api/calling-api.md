# Calling API

For chain API. please refer to [chain API section](../likecoin-chain-api/rpc-api/).

### Introduction

There are two kinds of API endpoint, public API and authenticated API.  Public APIs can be called directly. Authenticated API requires additional OAuth 2.0 permission grant. For how to authenticate via OAuth 2.0 flow, please refer to `Authetication` session. &#x20;

Unless otherwise specified, all LikeCoin APIs accept and reply`application/json` as request and response body. Authenticated API takes an extra `Authorization` header with payload `Bearer {{token}}`.

### API Endpoints

Production endpoint: `https://api.like.co`&#x20;

Development endpoint: `https://api.testnet.like.co`\
\
Please refer to `Reference` session for a list of available API.\


### Obtaining OAuth client ID and secret for authenticated API

Please contact `team@like.co` for obtaining OAuth client id/secret, and scope/redirect\_uri whitelist.

