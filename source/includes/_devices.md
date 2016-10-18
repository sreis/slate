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
