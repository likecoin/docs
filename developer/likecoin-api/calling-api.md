# Calling API

### Introduction

There are two kinds of API endpoint, public API and authenticated API.  Public APIs can be called directly. Authenticated API requires additional OAuth 2.0 permission grant. For how to authenticate via OAuth 2.0 flow, please refer to `Authetication` session.  

Unless otherwise specified, all LikeCoin APIs accept and reply`application/json` as request and response body. Authenticated API takes an extra `Authorization` header with payload `Bearer {{token}}`.

### Endpoints

Production endpoint: `https://api.like.co` 

Development endpoint: `https://api.rinkeby.like.co`\
\
Please refer to `Reference` session for a list of available API.\


### Obtaining OAuth client ID and secret for authenticated API

Please contact `team@like.co` for obtaining OAuth client id/secret, and scope/redirect_uri whitelist.

