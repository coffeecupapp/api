# Users

## Get all colors

`GET /v1/colors`

Example request

```shell
curl \
  -X GET https://company.coffeecupapp.com/v1/colors
```

HTTP Response: 200 Success

```json
{
  "colors": [
    {
      "status": 1,
      "label": "lila",
      "hex": "103F8C",
      "id": 1
    },
    {
      "status": 1,
      "label": "graublau",
      "hex": "02A4A4",
      "id": 2
    },
    {
      "status": 1,
      "label": "blau",
      "hex": "02A1CB",
      "id": 3
    },
    /* ... */
  ],
  "meta": {
    "skip": 0,
    "limit": 30,
    "total": 23,
    "criteria": {}
  }
}
```


```shell
curl \
  -X GET http://localhost:1337/v1/colors
```