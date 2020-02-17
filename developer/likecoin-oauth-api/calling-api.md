# Calling API

There are two kinds of API endpoint, public API and authenticated API.  Public APIs can be called directly. Authenticated API requires additional OAuth 2.0 permission grant. For how to authenticate via OAuth 2.0 flow, please refer to `Authetication` session.  

Unless otherwise specified, all LikeCoin APIs accept and reply`application/json` as request and response body. Authenticated API takes an extra `Authorization` header with payload `Bearer {{token}}`.

Please refer to `Reference` session for a list of available API.



