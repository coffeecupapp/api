# CAUTION: MIGHT BE OUT OF DATE

# Time Entry Analytics


`GET /v1/analytics/time-entries`

<code>
GET /v1/analytics/time-entries?start_date=<b>START_DATE</b>&end_date=<b>END_DATE</b>
</code>

Optional (Users, Projects, Tasks, Project Clients):

<pre>
GET /v1/analytics/time-entries?start_date=<b>START_DATE</b>&end_date=<b>END_DATE</b>
  &user[]=<b>USER_1</b>&user[]=<b>USER_2</b>
  &project[]=<b>PROJECT_1</b>&project[]=<b>PROJECT_2</b>
  &task[]=<b>TASK_1</b>&task[]=<b>TASK_2</b>
  &project.client[]=<b>PROJECT_CLIENT_1</b>&project.client[]=<b>PROJECT_CLIENT_2</b>
</pre>

HTTP Response: 200 Success

```json
{
  "analyticsTimeEntries": {
    "startTimestamp": 1411855200000,
    "endTimestamp": 1475618399000,
    "hours": {
      "total": 80247.29250000003,
      "spent": 67683.49055555557,
      "nonBillable": 12563.801944444444,
      "budget": 132,
      "outOfBudget": 24554.65027777778
    },
    "amount": {
      "spent": 2512692.1472000005,
      "budget": 700,
      "outOfBudget": 2438980.1522
    }
  }
}
```
