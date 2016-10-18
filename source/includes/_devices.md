# Devices

## Get All Your Devices

```ruby
require 'littleBits'

api = littleBits::APIClient.authorize!('meowmeowmeow')
api.devices.get
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
import littleBits

api = littleBits.authorize('meowmeowmeow')
api.device.get("00e040000001")
```

```shell
curl "https://api-http.littlebitscloud.cc/v2/devices/00e040000001" \
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

## Update Device Settings

```shell
curl "https://api-http.littlebitscloud.cc/v2/devices/00e040000001" \
  -X PUT \
  -H "Authorization: meowmeowmeow" \
  -H "Content-type: application/json" \
  -d '{ "update": { "label": "cloudbit", "input_interval_ms": 250 } }'
```

This endpoint updates a specific device.

### HTTP Request

`PUT https://api-http.littlebitscloud.cc/v2/devices/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
  ID | The ID of the device to update

### JSON Payload

Parameter | Description
--------- | -----------
  label | The new label for this device. Default is "cloudbit"
  input_interval_ms | Interval in milliseconds when input is read and broadcast. Default is 250 and the minimum is 200.

## Output voltage on device

```shell
curl "https://api-http.littlebitscloud.cc/v2/devices/00e040000001/output" \
  -X POST \
  -H "Authorization: meowmeowmeow" \
  -H "Content-type: application/json" \
  -d '{ "percent": 100, "duration_ms": 3000 }'
```

This endpoint outputs voltage on a device.

### HTTP Request

`POST https://api-http.littlebitscloud.cc/v2/devices/<ID>/output`

### URL Parameters

Parameter | Description
--------- | -----------
  ID | The ID of the device to send output to

### JSON Payload

Parameter | Description
--------- | -----------
  percent | A percent of the maximum current output between 0 and 100. Default is 100.
  duration_ms | Output will be sustained for the given milliseconds. If duration_ms is -1 it will last forever or until another ouput is received by device. Maximum is 32000 and default is 3000 (3 seconds).

