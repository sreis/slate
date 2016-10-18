# Subscriptions

## Create subscription

Use this endpoint to create a subscription between devices or to receive events in a HTTP server that you control.

```javascript
api.subscribe({ publisher_id: 00e040000001, subscriber_id: 00e040000002 })

api.subscribe({ publisher_id: 00e040000001, subscriber_id: 00e040000002 })

api.subscribe({
	publisher_id: 00e040000001,
	subscriber_id: 00e040000002,
	publisher_events: ['amplitude']
})
```

```shell
curl "https://api-http.littlebitscloud.cc/v2/subscriptions" \
  -X POST \
  -H "Authorization: meowmeowmeow" \
  -H "Content-type: application/json" \
  -d '{ "publisher_id": "00e040000001" ,"subscriber_id": "00e040000002" }'

curl "https://api-http.littlebitscloud.cc/v2/subscriptions" \
  -X POST \
  -H "Authorization: meowmeowmeow" \
  -H "Content-type: application/json" \
  -d '{ "publisher_id": "00e040000001" ,"subscriber_id": "http://yourserver.com/endpoint" }'

curl "https://api-http.littlebitscloud.cc/v2/subscriptions" \
  -X POST \
  -H "Authorization: meowmeowmeow" \
  -H "Content-type: application/json" \
  -d '{ "publisher_id": "00e040000001" ,"subscriber_id": "00e040000002", "publisher_events: "['amplitude']" }'
```


> The above command returns the JSON that was POSTed.

```json
{
	"publisher_id": "00e040000001",
	"subscriber_id": "00e040000002",
	"publisher_events": ["amplitude"]
}
```

### HTTP Request

`POST https://api-http.littlebitscloud.cc/v2/subscriptions`

### JSON Payload

Parameter | Description
--------- | -----------
publisher_id | Device id of publisher.
subscriber_id | Device id or callback URI. You must ensure that URI is accessible to the Internet.
publisher_events | Events to subscribe to. Defaults to ["amplitude:delta:ignite"]

Available events to subscribe to.

Event | Description
--------- | -----------
amplitude                  | when there is any voltage (catch-all, default)
amplitude:delta:sustain    | when high voltage is constant (eg button being held)
amplitude:delta:ignite     | when there is significant voltage jump (eg button press)
amplitude:delta:release    | when there is significant voltage drop (eg button release)
amplitude:delta:nap        | when low voltage is constant (eg idle bitSnap system)
amplitude:level:active     | generic, when there is high voltage (eg during a sustain or maybe just ignited)
amplitude:level:idle       | generic, when there is low voltage (eg during a long nap or maybe just released)

## List subscriptions

```javascript
api.subscriptions({ publisher_id: "00e040000001" })

api.subscriptions({ subscriber_id: "00e040000002" })

api.subscriptions({ publisher_id: "00e040000001", subscriber_id: "00e040000002" })

```

```shell

curl "https://api-http.littlebitscloud.cc/v2/subscriptions?publisher_id=00e040000001" \
  -H "Authorization: Bearer meowmeowmeow"

curl "https://api-http.littlebitscloud.cc/v2/subscriptions?subscriber_id=00e040000002" \
  -H "Authorization: Bearer meowmeowmeow"

curl "https://api-http.littlebitscloud.cc/v2/subscriptions?publisher_id=00e040000001&subscriber_id=00e040000002" \
  -H "Authorization: Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
	{
		"publisher_id": "00e040000001",
		"subscriber_id":"00e040000002",
		"publisher_events":["amplitude"]
	},
	{
		"publisher_id": "00e040000001",
		"subscriber_id": "https://yourserver.com/endpoint",
		"publisher_events":["amplitude:delta:ignite"]
	}
]
```

### HTTP Request

`GET https://api-http.littlebitscloud.cc/v2/subscriptions?publisher_id=<ID>&subscriber_id=<ID or HTTP endpoint>`

### Request Parameters

Parameter | Description
--------- | -----------
  publisher_id | List subscriptions where given device is a publisher
  subscriber_id | List subscriptions where given device is a subscriber. It can be a device ID or a callback URI.

You can provide publisher_id, subscriber_id or both.

## Delete a Subscription

Remove a subscription between a publisher and a subscriber.

```shell
curl "https://api-http.littlebitscloud.cc/v2/subscriptions" \
  -X DELETE \
  -H "Authorization: meowmeowmeow" \
  -H "Content-type: application/json" \
  -d '{ "publisher_id": "00e040000001" ,"subscriber_id": "http://yourserver.com/endpoint" }'

```

### HTTP Request

`DELETE https://api-http.littlebitscloud.cc/v2/subscriptions`

### JSON Payload

Parameter | Description
--------- | -----------
  subscriber_id | Device id or callback URI.
  publisher_id | Device id of publisher.
