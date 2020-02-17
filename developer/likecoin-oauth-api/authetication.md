---
description: How to obtain access token for authenticated API
---

# Authetication

### Introduction

LikeCoin API uses OAuth2.0 flow for API authorization, through the following steps.

1. Users authorize your app through web UI`https://like.co/in/oauth`. For details and params, please refer to `like.co OAuth page` section below
2. Users are redirected back to a `redirect_uri` you own with a `code`, this `code` is used to exchange for a user `access_token` and `refresh_token`.
3. Call APIs using `access_token` with proper scope. e.g. APIs in `Like->info` sections requires `read:like.info` or `write:like.info` grants.

#### AVAILABLE SCOPES: <a id="available-scopes"></a>

| Scope | Description |
| :--- | :--- |
| profile | Basic user public information |
| email | Access to user's email address |

The following scope should be prepended with `read:` or `write:`

| Scope | Description |
| :--- | :--- |
| \(read\|write\):like | Access to all like related read/write scope |
| read:like.button | Access to read user like history and suggestions |
| write:like.button | Permission to like content for user |
| read:like.info | Access to read user liked authors, content suggestions, etc |

#### TOKEN LIFE TIME <a id="token-life-time"></a>

Access tokens expire in 1 hour. Refresh tokens do not expire, unless:

1. Another new refresh token was issued for the same oauth client & user combination
2. User revoked access
3. OAuth client revoked the token via API

##  1. Format like.co OAuth parameters

`https://like.co/in/oauth/?client_id={{CLIENT_ID}}&scope={{scope}}&redirect_uri={{redirectURI}}&state={{state}}`

User will navigate to this page to authorize oauth, redirects back to `redirect_uri` with query param`auth_code` and `state` if success

| Param | Description |
| :--- | :--- |
| client\_id | OAuth client id |
| scope | list of scope seperated by space, must be whitelisted, e.g. `profile email` |
| redirect\_uri | redirect uri in URI compoenent encoded form, must be whitelisted |
| state | optional state provided by the service, that get passed back after authetication is success. Highly recommended for security reason. |

### 2. Redirect users to the formatted like.co OAuth page

The page will prompt user to either login or register a Liker ID if they are not logged in. Users logged in will then be shown the OAuth client's info and permissions asked. `authorization_code` and other response will be sent in query string to `redirect_uri` should users accept the permission, or error `denied` will be returned instead.  


### 3. Exchange `authorization_code` for `access_token`

{% api-method method="post" host="https://api.like.co" path="/oauth/access\_token" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}
After user oauth login in client, exchange authorization\_code in callback uri for access\_token
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter type="string" name="Content-Type" required=true %}
`application/x-www-form-urlencoded`
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="client\_id" type="string" required=true %}
OAuth client id
{% endapi-method-parameter %}

{% api-method-parameter name="client\_secret" type="string" required=true %}
OAuth client secret
{% endapi-method-parameter %}

{% api-method-parameter name="grant\_type" type="string" required=true %}
`authorization_code`
{% endapi-method-parameter %}

{% api-method-parameter name="code" type="string" required=true %}
The authorization code received in redirect\_uri
{% endapi-method-parameter %}

{% api-method-parameter name="redirect\_uri" type="string" required=true %}
The redirect\_uri param in original request
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
`access_token`, `refresh_token`, and user profile in JSON format
{% endapi-method-response-example-description %}

```
{
  "user": "williamchonggoogle",
  "displayName": "William Chong",
  "avatar": "https://storage.googleapis.com/likecoin-develop.appspot.com/likecoin_store_user_williamchonggoogle_test?GoogleAccessId=firebase-adminsdk-b93f2%40likecoin-develop.iam.gserviceaccount.com&Expires=2430432000&Signature=uJzHlCKDU9azuN5jbHVXToc2OsmPqJ0g4Q%2F3fhgJWBVK2f9brU%2FqYkx9ugVyNARugxxyCsfPX5a4jobhpI7jz%2FCy322RHv1TKPPePpQWstD46EhtFXwb8k2Q0HE65%2FO9yK69qvj08hSSvALFwk3oVObKw9D21mN5NLmar%2B9ZSxgl%2BBL%2BBfHp3cDEThZ%2FzMTHKSdOnrsSaH8Nrg7Y0wqzExzpc%2BaA158GDMAeJJwLWznXdrAI6Sd2CLMLW6ER%2FtdlTKQNbOEhiYElRLCC%2FBlS9jAjov7u%2BsifKEc7mADDum2dabBTBG69WusrgT8IrdBq2Hb6l05HI1AeRrlD8jeR5w%3D%3D",
  "refresh_token": "j31UBpMTdt-zaqVrCUJ0Ap8ulbosoPUGS8rVls_QYBg",
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjoid2lsbGlhbWNob25nZ29vZ2xlIiwic2NvcGUiOlsicHJvZmlsZSIsInJlYWQ6bGlrZSIsIndyaXRlOmxpa2UiXSwiYXpwIjoiMmY1NTFkNWZlMWFkNjU3NzNhMTciLCJpYXQiOjE1NTIwNDE3NDYsImV4cCI6MTU1MjA0NTM0NiwiYXVkIjoicmlua2VieS5saWtlLmNvIiwiaXNzIjoicmlua2VieS5saWtlLmNvIiwianRpIjoiMGJjN2Q1NGYtOWViYS00ODczLWFiYWUtMzc1ZTczYzExZTMwIn0.BPNsiQb0fs2fFjiSQWUq8oeE4FL_PLebdTRDpSh7n9k"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### 4. Call API with `access_token`

  Call authenticated API with header `Authorization` value`Bearer {{access_token}}`

