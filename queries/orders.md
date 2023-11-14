### Get the first 10 orders
```gql
query {
	orders(first: 5) {
		edges {
			node {
				id
				name
				totalPriceSet{
          presentmentMoney {
            amount
            currencyCode
          }
          shopMoney {
            amount
            currencyCode
          }
        }
			}
		}
	}
}
```

### Get the first 10 orders updated after December 1, 2019
```gql
query($query: String) {
  orders(first: 10, query: $query, sortKey: PROCESSED_AT) {
    edges {
      node {
        id
        updatedAt
      }
    }
  }
}
```

```json
{
	"query": "updated_at:>2019-12-01"
}
```

### Get the first 10 orders with 5 line items
```gql
query {
	orders(first: 5) {
		edges {
			node {
				id
				name
				totalPriceSet{
          presentmentMoney {
            amount
            currencyCode
          }
          shopMoney {
            amount
            currencyCode
          }
        }
        lineItems(first: 5) {
          edges {
            node {
              customAttributes {
                key
                value
              }
            }
          }
        }
			}
		}
	}
}

```
