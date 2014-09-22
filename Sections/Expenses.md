# Expenses

## Get All Expenses

`GET /api/expense`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/expense
```

HTTP Response: 200 Success

```json
{
  "data" : {
    "totalCount" : "1",
    "expense" : [
      {
        "id" : 1,
        "status" : 1,
        "modified" : "2014-02-08 22:31:18",
        "receipt_url" : "www.google.de",
        "project" : {
          "budget" : "900000.0000",
          "budget_type_index" : 0,
          "id" : 1,
          "code" : "PR1",
          "hourly_rate" : "90.0000",
          "invoice_type_index" : 0,
          "created" : "0000-00-00 00:00:00",
          "modified" : "0000-00-00 00:00:00",
          "comment" : "",
          "client_id" : 1,
          "name" : "Projekt 1"
        },
        "user_id" : 1,
        "type" : {
          "unit_price" : "12.4400",
          "id" : 1,
          "created" : "0000-00-00 00:00:00",
          "label" : "expensetypename",
          "modified" : "0000-00-00 00:00:00",
          "unit_label" : "€"
        },
        "comment" : "dasdasd",
        "price" : "44.3300",
        "date" : "2014-02-08 22:31:18",
        "type_id" : 1,
        "created" : "2014-02-08 22:31:18",
        "project_id" : 1,
        "user" : {
          "id" : 1,
          "type_index" : 0,
          "date_format" : "d.m.Y",
          "beginning_of_week" : 0,
          "modified" : "2014-02-08 17:12:19",
          "lastname" : "nachname",
          "last_active_at" : "0000-00-00 00:00:00",
          "hourly_rate" : "90.9900",
          "image_url" : "",
          "firstname" : "vorname",
          "timeofday_format" : "H:i:s",
          "language" : "de_DE",
          "created" : "2014-02-08 17:12:19",
          "timezone" : "Europe/Berlin",
          "role_index" : 0,
          "last_login_at" : "0000-00-00 00:00:00",
          "email" : "email@provider.com"
        }
      }
    ]
  },
  "success" : true,
  "message" : "Record(s) Found"
}
```


## Get Archived Expenses Only

`GET /api/expense?filter=[{"property": "status", "value" : "0", "operator": "="}]`

HTTP Response: 200 Success

## Get Archived AND Non-Archived Expenses (DEFAULT Behaviour)

`GET /api/expense?filter=[{"property": "status", "value" : "0", "operator": ">="}]`

HTTP Response: 200 Success

## Get Non-Archived Expenses Only

`GET /api/expense?filter=[{"property": "status", "value" : "1", "operator": "="}]`

## Archive A Expense

### TODO: DOKU WHAT WILL BE ARCHIVED ALONG WITH THE ENTRY, IF ANY

`PUT /api/expense/#{expense_id}`

```json
{
    "status": "0"
}
```
HTTP Response: 200 OK


# Expense_Types

## Get All Expense Types

`GET /api/expense_type`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/expense_type
```

HTTP Response: 200 Success

```json
{
  "data" : {
    "totalCount" : "1",
    "expense_type" : [
      {
        "unit_price" : "12.4400",
        "id" : 1,
        "created" : "0000-00-00 00:00:00",
        "label" : "expensetypename",
        "modified" : "0000-00-00 00:00:00",
        "unit_label" : "€"
        "icon" : "icon-search"
      }
    ]
  },
  "success" : true,
  "message" : "Record(s) Found"
}
```


## TBD....
FIND corresponding `PUT` `POST` and `DELETE` Requests in the clients sections
 [Clients API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients.md)
 [Client-Contacts API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients%20Contacts.md)