# Introduction to the CoffeeCup API

CoffeeCup provides two API interfaces, serving two distinct roles. If you need to access and manipulate your daily timesheet the [Time Tracking API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Time%20Tracking.md) fits the bill. Notable uses of the [Time Tracking API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Time%20Tracking.md) are the widgets we provide for PC and Mac as well as other third party timesheet software integrations.

If you need to access and edit your projects, clients, users and tasks the extended API is your choice. You can use this to mass import your existing projects setup, add users and generally integrate with your existing back-office setup.

Remember to write your application carefully, caching when possible. In case of abuse you may be blocked, disallowing further API access. As an act of courtesy, please provide User-Agent strings denoting your application.

## Get the Help You Need

Have a question about using the API? Have you noticed an error or omission in the documentation? Feel free to [open an issue](http://github.com/coffeecupapp/api/issues/) with your question. If you're running into problems with a specific implementation, however, it's best to [get in touch with us directly](http://www.coffeecupapp.com/help/contact) in support (that way we can work with you, checking the logs for specific requests and responses).

## Sample Code & Examples

To help you get started with the CoffeeCup API, we have provided sample scripts in several programming languages. These scripts depict authentication and basic API actions. Visit the [CoffeeCup API Samples GitHub project](http://github.com/coffeecupapp/coffeecup_api_samples) to take a look at the scripts.

You may also want to check out the open-source libraries for the CoffeeCup API below.

## Keep up-to-date with changes to the CoffeeCup API

Watch the CoffeeCup API repository to receive email notification of updates to the API documentation. Find out when we've made tweaks to our documentation simply by clicking the eye symbol/watch selection in the upper right of this page.

## Help us towards a better API

The CoffeeCup API has moved to Github so you could actively participate in helping us making the API better. If you have any requests or you found a bug, you can use Github issues to let us know. You can also fork the docs and send a pull request with improvements

## Share Your Creation

If you've built something interesting with the CoffeeCup API or the [CoffeeCup Platform](http://www.coffeecupapp.com/platform), share the love! Created a library or other cool connector another CoffeeCup user might find useful? Add it to our [Community Creations and Hacks page](https://github.com/coffeecupapp/api/wiki/Community-Creations-&-Hacks), and contribute to the solid list of great projects people have made. If it's a connector between another app and ours, ping us at [support@coffeecupapp.com](mailto:support@coffeecupapp.com) — we may be able to list it on our [Add-ons](http://www.coffeecupapp.com/add-ons) page.

## Example requests

The example requests here are done using a command line tool called [cURL](http://en.wikipedia.org/wiki/CURL). If you want to try the requests out yourself, you can download cURL from [here](http://curl.haxx.se/download.html). It is available for all possible operating systems.

Under Ubuntu installing cURL is very easy:

```shell
sudo apt-get install curl
```

## CORS

If you wish to use the API using CORS, we'll need to whitelist you first. Please send us a note at support@coffeecupapp.com to whitelist your domain(s).

## Successful requests

When request is successful (2xx), a nested response object is returned. Fields which value is NULL are not in the response.

Example request

```shell
curl -v -u admin:admin -X GET http://dev.coffeecupapp.com/api/time_entries
```
Response

```json
{
    "success": true,
    "message": "Record(s) Found",
    "data": {
        "meta": {
            "total": 20
        },
        "time_entries": [
            {
                "id": 1,
                "starttime": "2014-02-08 21:55:45",
                "endtime": "2014-02-08 22:55:30",
                ...
            },
            ...
        ]
    }
}
```

##Failed requests

If a create or update action failed, HTTP status code 404 and an array of localized error messages will be returned.

```shell
curl -v -u admin:admin \
	-H 'Content-type: application/json' \
	-d '{"time_entry":{"description":"New time entry","created_with":"API example code"}}' \
	-X POST http://dev.coffeecupapp.com/api/time_entries/1/foo
```

Response

```json
{
    "success": false,
    "message": "Method Not Allowed",
    "data": {
        "errorCode": "405",
        "message": "Method Not Allowed"
    }
}
```

## Authorization

All requests to the CoffeeCup API are made on the behalf of an actual user (see the [HTTP Basic Authentication](https://github.com/coffeecupapp/api/blob/master/Authentication/HTTP%20Basic.md) or [OAuth 2.0 Authentication](https://github.com/coffeecupapp/api/blob/master/Authentication/OAuth%202.0.md) sections for detail on authenticating your requests). You can use a regular account for requests against the [Time Tracking API](https://github.com/coffeecupapp/api/blob/master/Sections/Time%20Tracking.md), but for private integrations accessing the Extended REST API we recommend creating a special admin user.

CoffeeCup will check your role on each request, and actions that are unavailable to you on the UI will be unavailable over the API as well. Administrators can generally access all API resources, and regular users are limited to their own timesheets. Project Managers can access projects they manage in addition to their own timesheets.

## Supported Data Formats

The API accepts only JSON requests. Please make sure you're setting Content-type: `application/json` in your request header. Each request returns a JSON-encoded body.

The result of each action is communicated via standard HTTP response codes.

## Throttle Limit - HTTP 503

We have an API throttle that blocks accounts emitting more than 100 calls per 15 seconds. We reserve the right to tune the limitations, but they are always set high enough to allow a well-behaving interactive program to do its job.

For batch processes and API developers who still need to perfect their code, this throttle may be an inadvertent blocker. Just wait and make no API calls (the throttle is reset with each call). The throttle will lift itself in few minutes and API calls may resume.

When the rate limit is exceeded CoffeeCup will send an HTTP 503 status code. The number of seconds until the throttle is lifted is sent via the `Retry-After` HTTP header, as specified in [RFC 2616](http://tools.ietf.org/html/rfc2616#section-14.37). You can use `GET /account/rate_limit_status` to programmatically query your current throttle status.

## Notational Conventions

Throughout our documentation you'll find the following set of notational conventions:

* `#{expression}`: Should be substituted with the value of the expression. For example, `/#{project_id}` should be replaced with `/12345` (assuming your `project_id` is 12345)

* `...`: For brevity, we have skipped repetitive parts of the response.

* `<!-- Comment -->`: Optional comment in the response added for clarity. The actual response will not contain comments.

## CoffeeCup API Libraries

A few of our users have implemented their own CoffeeCup API wrappers. If you plan on writing a CoffeeCup API client, you may want to check out some of these excellent projects:

* Ruby: [CoffeeCuped](https://github.com/lorem/coffeecuped), by Lorem Ipsum
* Python: [CoffeeCup Time Tracking API Client](https://github.com/lorem/python-coffeecup), by Lorem Ipsum, LLC
* Python: [CoffeeCup API Wrapper in Python](http://github.com/lorem/CoffeeCup), by Lorem Ipsum and Lorem Ipsum
* Java: [CoffeeCup-client](http://github.com/lorem/coffeecup-client),  by Lorem Ipsum
* PHP: [HaPi - PHP CoffeeCup API](http://labs.lorem.com/coffeecup-api/),  by Lorem Ipsum
* Node.js: [node-coffeecup](https://github.com/lorem/node-coffeecup),  by Lorem Ipsum
* Drupal: [CoffeeCup Module for Drupal](http://lorem.org/project/coffeecup),  by Lorem Ipsum

We also have sample scripts in several languages. These scripts depict authentication and basic API actions. Visit the [CoffeeCup API Samples GitHub project](http://github.com/coffeecupapp/coffeecup_api_samples) to take a look at the scripts.

## Have More Questions?

Please email us at [support@coffeecupapp.com](mailto:support@coffeecupapp.com).
