# Calendar Feeds

The `token` in Calendar Feed models can be used to construct a URL for an iCalendar (ics) feed.

## Get all calendar feeds

`GET /v1/calendarfeeds`

Example request

```shell
curl \
  -X GET https://api.coffeecupapp.com/v1/calendarfeeds
```

HTTP Response: 200 Success

```json
{
  "calendarFeeds": [
    {
      "user": 17,
      "token": "bJ408BPFoXXI6ucbohh90tIgFfqxVWaMsjIMBUJl6aRfE1ql6sx0vpgj-dPz-yec",
      "id": 5,
      "createdAt": "2017-05-29T14:34:44.000Z",
      "updatedAt": "2017-05-29T14:34:44.000Z"
    },
    {
      "user": 17,
      "token": "r8FZnW4z1brxLzM17555nje4CLhGXaSSHLOLBCtPQ0US5h0JFBuVw7YEGrKHF2Cu",
      "id": 6,
      "createdAt": "2017-05-29T15:31:01.000Z",
      "updatedAt": "2017-05-29T15:31:01.000Z"
    }
  ],
  "meta": {
    "skip": 0,
    "limit": 1000,
    "total": 2,
    "criteria": {}
  }
}
```

iCalender feed url

```
 https://api.coffeecupapp.com/v1/calendarfeeds/private/bJ408BPFoXXI6ucbohh90tIgFfqxVWaMsjIMBUJl6aRfE1ql6sx0vpgj-dPz-yec/feed.ics
```

## Create new absence calendar feed

Example request

```shell
curl \
  -X POST https://api.coffeecupapp.com/v1/calendarfeeds
```

HTTP Response: 200 Success

```json
{
  "calendarFeed": {
    "user": 17,
    "token": "bJ408BPFoWWI6ucbohh90tIgFfqxVWaMsjIMBUJl6aRfE1ql6sx0vpgj-dPz-yec",
    "id": 5,
    "createdAt": "2017-05-29T14:34:44.000Z",
    "updatedAt": "2017-05-29T14:34:44.000Z"
  }
}
```

## Revoke calendar feed

Example request

```shell
curl \
  -X DELETE https://api.coffeecupapp.com/v1/calendarfeeds/5
```

HTTP Response: 200 Success

