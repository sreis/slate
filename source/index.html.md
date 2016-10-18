---
title: API Reference

language_tabs:
  - shell
  - javascript

toc_footers:
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - devices
  - subscriptions
  - errors

search: true
---

# Introduction

```javascript

// More information available on our github page at
// https://github.com/littlebits/cloud-client-api-http

npm install --save @littlebits/cloud-http
```

Welcome to the litteBits Cloud API! You can use our API to access
litteBits Cloud API endpoints to manage your cloudbits.

We have language bindings in Shell, Ruby, and Python! You can view
code examples in the dark area to the right, and you can switch the
programming language of the examples with the tabs in the top right.

This example API documentation page was created with
[Slate](https://github.com/tripit/slate). Feel free to edit it and use
it as a base for your own API's documentation.


# Rate limiting

The littleBits Cloud API is rate limited to prevent abuse that would
degrade our ability to maintain consistent API performance for all
users. By default, each API key or app is rate limited at 1800
requests per hour. If your requests are being rate limited, HTTP
response code 429 will be returned with an rate_limit_exceeded error.

# Authentication

> To authorize, use this code:

```javascript
var api = require('littlebits-cloud-http')
	  .defaults({ access_token: 'meowmeowmeow' })
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api-http.littlebitscloud.cc" \
  -H "Authorization: Bearer meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

litteBits uses API keys to allow access to the API. You get you API
key at our [cloud control](https://control.littlebitscloud.cc).

littleBits expects for the API key to be included in all API requests
to the server in a header that looks like the following:

`Authorization: Bearer meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>
