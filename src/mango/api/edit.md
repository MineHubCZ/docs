# Edit service

You can edit service via this endpoint, you must be authorized using token.

## Endpoint

`POST /api/services/{service}/edit`

## Request

Request must contain token and new status in json like this:

```json
{
    "token": "secret_token",
    "status": 0
}
```

where status can be 0, 1 or 2 as seen in table on upper table.

## Response

If the token is not valid you get 401. If the status is not valid number, you get 400. If the service does not exist, you get 404. Otherwise 200.
