### Register webhook
```gql
mutation webhookSubscriptionCreate(
	$topic: WebhookSubscriptionTopic!
	$webhookSubscription: WebhookSubscriptionInput!
) {
	webhookSubscriptionCreate(
		topic: $topic
		webhookSubscription: $webhookSubscription
	) {
		webhookSubscription {
			id
			topic
			format
			endpoint {
				__typename
				... on WebhookHttpEndpoint {
					callbackUrl
				}
			}
		}
		userErrors {
			field
			message
		}
	}
}
```

```json
{
  "topic":"ORDERS_CREATE",
  "webhookSubscription": {
    "callbackUrl": "https://your-app.com/webhooks/orders_create",
    "format":"JSON"
  }
}
```