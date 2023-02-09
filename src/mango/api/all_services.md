# Get all services

This endpoint allows you to get all services with no authentication.

## Endpoint

`GET /api/services/all`

## Respose

Json of all services. E.g.:

```json
{
    "web": 1,
    "survival": 1,
    "identita": 0,
    "skyblock": 2
}
```

## Statuses

| Code | Status      |
|------|-------------|
| 0    | offline     |
| 1    | online      |
| 2    | maintenance |

