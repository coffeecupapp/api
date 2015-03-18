# Expenses

## Get All Expenses

`GET /v1/expenses`

Example request

```shell
curl \
  -H "Authorization: Bearer 14df41535ce02fd3f69a53ab80184a691337f80a" \
  -X GET https://company.coffeecupapp.com/v1/expenses
```

HTTP Response: 200 Success

```json
{
  "expenses": [
    {
      "expenseType": 1,
      "project": 1,
      "user": 1,
      "status": 1,
      "price": 44.33,
      "receiptUrl": "",
      "comment": "",
      "date": "2014-02-07T23:00:00.000Z",
      "id": 1
    },
    {
      "expenseType": null,
      "project": null,
      "user": null,
      "status": 1,
      "price": null,
      "receiptUrl": null,
      "comment": null,
      "date": null,
      "id": 2
    }
  ],
  "meta": {
    "skip": 0,
    "limit": 30,
    "total": 2,
    "criteria": {}
  }
}
```



## Get Archived Expenses Only

`GET /v1/expenses?status[]=0`

HTTP Response: 200 Success

## Get Archived AND Non-Archived Expenses (DEFAULT Behaviour)

`GET /v1/expenses?status[]=0&status[]=1`

HTTP Response: 200 Success

## Get Non-Archived Expenses Only

`GET /v1/expenses?status[]=1`

HTTP Response: 200 Success

## Archive A Client

### TODO: DOKU WHAT WILL BE ARCHIVED ALONG WITH THE EXPENSE

`PUT /v1/expenses/#{client_id}`

```json
{
  "expense": {
    "status": 0
  }
}
```
HTTP Response: 200 OK


# TODODODODODODO

# Expense_Types

## Get All Expense Types

`GET /v1/expenseTypes`

Example request

```shell
curl \
  -H "Authorization: Bearer 14df41535ce02fd3f69a53ab80184a691337f80a" \
  -X GET https://company.coffeecupapp.com/v1/expenseTypes
```

HTTP Response: 200 Success

```json
{
  "expenseTypes": [
    {
      "status": 1,
      "label": "Reisekosten",
      "unitPrice": 12.44,
      "unitLabel": "Kilometer",
      "comment": "Kommentar",
      "icon": "home",
      "id": 1
    }
  ],
  "meta": {
    "skip": 0,
    "limit": 30,
    "total": 1,
    "criteria": {}
  }
}
```


## TBD....
FIND corresponding `PUT` `POST` and `DELETE` Requests in the clients sections
 [Clients API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients.md)
 [Client-Contacts API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients%20Contacts.md)