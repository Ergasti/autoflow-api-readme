# AutoFlow API

## POST /api/v1/message_queue_trigger

This endpoint is used to trigger a message queue in the AutoFlow system.

### Parameters

| Parameter          | Type   | Description                                                         |
| ------------------ | ------ | ------------------------------------------------------------------- |
| user_info          | object | An object containing user information.                              |
| signup_timestamp   | string | The signup timestamp of the user.                                   |
| flow_id            | string | The ID of the flow that needs to be triggered.                       |

#### user_info object

| Parameter   | Type   | Description                   |
| ----------- | ------ | ----------------------------- |
| order_id    | int    | The order ID.                 |
| customer_id | int    | The customer ID.              |
| number      | string | The message number.           |
| text        | string | The text of the message.      |

### Example Request

```bash
curl -X POST \
  https://your-domain.com/wp-json/api/v1/message_queue_trigger \
  -H 'Content-Type: application/json' \
  -H 'api_key: your_api_key' \
  -d '{
        "user_info": {
            "order_id": 123,
            "customer_id": 456,
            "number": "0123456789",
            "text": "Hello, World!"
        },
        "signup_timestamp": "2023-06-25T12:00:00Z",
        "flow_id": "789"
    }'
##Example Response
{
    "message_id": 1,
    "message": "The message was added to the database successfully.",
    "status": 200
}
```
##Status Codes
| Status | Code | Description
-----------------------------
200 | OK  | The message was added to the database successfully.
400 | Bad Request | Required parameters are missing.
401 | Unauthorized | Invalid API key.
500 | Internal Server Error | Database query error.
