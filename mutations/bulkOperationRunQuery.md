### Get all orders with line items
```gql
mutation {
  bulkOperationRunQuery(
   query: """
    {
      orders(query: "processed_at:>='2023-11-07T04:00:00Z'", sortKey: PROCESSED_AT) {
        edges {
          node {
						id
						name
            totalPriceSet{
              shopMoney {
                amount
                currencyCode
              }
            }
            lineItems {
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
    """
  ) {
    bulkOperation {
      id
      status
    }
    userErrors {
      field
      message
    }
  }
}
```
