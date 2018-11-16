---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript
  - shell

toc_footers:
  - <a href='https://sharespost.com'>Sign Up at SharesPost.com</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the SharesPost Marketplace API! You can use our API to information about our cryptocurrency markets, place orders, and see your trading history.

We have language bindings in Curl and JavaScript right now (with more to come). You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```javascript
const AgoraBot = require("agora-bot");
const bot = new AgoraBot();

bot.ready.then(() => {
  // Post-authentication code here
});
```

```shell
# Get a cookie into Curl
curl --cookie-jar /tmp/agora \
  https://app.sp-acceptance.net/oauth/token \
  -X POST \
  --header "Content-Type: application/json" \
  --data '{"username": "USERNAME", "password": "PASSWORD", "grant_type": "password"}'

# Refresh a cookie
curl --cookie-jar /tmp/agora -b /tmp/agora \
  https://app.sp-acceptance.net/agora/auth \
  --header "Content-Type: application/json" \
  --user BASIC_AUTH_USERNAME:BASIC_AUTH_PASSWORD
```

> Cookies expire every three minutes. The SDK will handle refresh for you. Otherwise you'll have to make sure to refresh before the cookie expires.
> Make sure to replace `USERNAME`, `PASSWORD`, `BASIC_USERNAME` and `BASIC_PASSWORD` with your credentials.

SharesPost Marketplace uses cookies from our main site to allow access to the API. You can request a cookie with your username and password. Afterwards, you may refresh that cookie periodically to keep it valid.

<aside class="notice">
You must signup for a SharesPost account at <a href="https://app.sharespost.com/signup">SharesPost.com</a> to use the API.
</aside>

# Market Data

## Get Market Ticker

```javascript
const AgoraBot = require("agora-bot");
const bot = new AgoraBot();

bot.ready.then(() => {
  const market = bot.getMarketTicker();
});
```

```shell
curl -b /tmp/agora-cookies \
  https://app.sp-acceptance.net/market-api/api/v0/markets/ticker \
  --user BASIC_AUTH_USERNAME:BASIC_AUTH_PASSWORD
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

| Parameter    | Default | Description                                                                      |
| ------------ | ------- | -------------------------------------------------------------------------------- |
| include_cats | false   | If set to true, the result will also include cats.                               |
| available    | true    | If set to false, the result will include kittens that have already been adopted. |

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require("kittn");

let api = kittn.authorize("meowmeowmeow");
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

| Parameter | Description                      |
| --------- | -------------------------------- |
| ID        | The ID of the kitten to retrieve |

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require("kittn");

let api = kittn.authorize("meowmeowmeow");
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted": ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| ID        | The ID of the kitten to delete |
