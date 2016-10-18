---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python

toc_footers:
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

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

```ruby
require 'littleBits'

api = littleBits::APIClient.authorize!('meowmeowmeow')
```

```python
import littleBits

api = littleBits.authorize('meowmeowmeow')
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

# Devices

## Get All Your Devices

```ruby
require 'littleBits'

api = littleBits::APIClient.authorize!('meowmeowmeow')
api.devices.get
```

```python
import littleBits

api = littleBits.authorize('meowmeowmeow')
api.devices.get()
```

```shell
curl "https://api-http.littlebitscloud.cc/v2/devices" \
  -H "Authorization: Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
	{
		"label": "my cloudbit 1",
		"id": "00e040000001",
		"user_id": 1,
		"is_connected": false,
		"subscriptions":[
			{
				"publisher_id": "00e040000002",
				"subscriber_id": "00e040000001",
				"publisher_events":[
					{
						"name": "amplitude"
					}
				]
			},
		{
				"publisher_id": "00e040000001",
				"subscriber_id": "https://yourserver.com/endpoint",
				"publisher_events":[
					{
						"name": "amplitude:delta:ignite"
					}
				]
			}
		],
		"subscribers": [
		],
		"input_interval_ms": 750
	},
	{
		"label": "my cloudbit 2",
		"id": "00e040000002",
		"user_id": 1,
		"is_connected": false,
		"subscriptions": [
		],
		"subscribers":[
			{
				"publisher_id": "00e040000002",
				"subscriber_id": "00e040000001",
				"publisher_events": [
					{
						"name": "amplitude"
					}
				]
			}
		],
		"input_interval_ms":750
	}
]
```

## Get a Specific Device

```ruby
require 'littleBits'

api = littleBit::APIClient.authorize!('meowmeowmeow')
api.device.get("00e040000001")
```

```python
import littleBits

api = littleBits.authorize('meowmeowmeow')
api.device.get("00e040000001")
```

```shell
curl "http://api-http.littlebitscloud.cc/v2/devices/00e040000001" \
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
		"label": "my cloudbit 1",
		"id": "00e040000001",
		"user_id": 1,
		"is_connected": false,
		"subscriptions":[
			{
				"publisher_id": "00e040000002",
				"subscriber_id": "00e040000001",
				"publisher_events":[
					{
						"name": "amplitude"
					}
				]
			},
		{
				"publisher_id": "00e040000001",
				"subscriber_id": "https://yourserver.com/endpoint",
				"publisher_events":[
					{
						"name": "amplitude:delta:ignite"
					}
				]
			}
		],
		"subscribers": [
		],
		"input_interval_ms": 750
}
```

This endpoint retrieves a specific device.

### HTTP Request

`GET https://api-http.littlebitscloud.cc/v2/devices/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the device to retrieve
