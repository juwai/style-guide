# JavaScript Object Notation

AJAX response have to follow [RPC convention](http://docs.juwai.io/rpc/property.html#module-jw.property.views.rpc).

| Type    | Description                                                               | Required Keys   |
|---------|---------------------------------------------------------------------------|-----------------|
| Success | All went well, and (usually) some content was returned.                   | status, content |
| Error   | An error occurred in processing the request, i.e. an exception was thrown | status, content |

## Success response examples

### Example 1:

```json
{
    "status": "OK",
    "content": [
        {
            "id": 1,
            "user": "Juwai",
            "location": "Shanghai"
        },
        {
            "id": 2,
            "user": "Juwai",
            "location": "Shanghai"
        }
    ]
}
```
### Example 2:

```json
{
    "status": "OK",
    "content": "Account created!"
}
```

## Error response examples

### Example 1:

```json
{
    "status": "ERROR",
    "content": "Property was not found"
}
```
