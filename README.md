# Introduction to the CoffeeCup API

CoffeeCup provides two API interfaces, serving two distinct roles. If you need to access and manipulate your daily timesheet the [Time Tracking API](Sections/Time%20Tracking.md) fits the bill. Notable uses of the [Time Tracking API](Sections/Time%20Tracking.md) are the widgets we provide for PC and Mac as well as other third party timesheet software integrations.

If you need to access and edit your projects, clients, users and tasks the extended API is your choice. You can use this to mass import your existing projects setup, add users and generally integrate with your existing back-office setup.

Remember to write your application carefully, caching when possible. In case of abuse you may be blocked, disallowing further API access. As an act of courtesy, please provide User-Agent strings denoting your application.

## Get the Help You Need

Have a question about using the API? Have you noticed an error or omission in the documentation? If you're running into problems with a specific implementation, however, it's best to [get in touch with us directly](http://support.coffeecupapp.com) in support (that way we can work with you, checking the logs for specific requests and responses).

## Authorization

All requests to the CoffeeCup API are made on the behalf of an actual user (see the [OAuth 2.0 Authentication](Authentication/OAuth2.md) section for detail on authenticating your requests). You can use a regular user for requests against the [Time Tracking API](Sections/Time%20Tracking.md), but for private integrations accessing the Extended REST API we recommend creating a special admin user.

CoffeeCup will check your role on each request, and actions that are unavailable to you on the UI will be unavailable over the API as well. Administrators can generally access all API resources, and regular users are limited to their own timesheets and data.

## Supported Data Formats

The API accepts only JSON requests. Please make sure you're setting Content-type: `application/json` in your request header. Each request returns a JSON-encoded body.

The result of each action is communicated via standard HTTP response codes.

## Throttle Limit - HTTP 503

We have an API throttle that blocks accounts emitting more than 100 calls per 15 seconds. We reserve the right to tune the limitations, but they are always set high enough to allow a well-behaving interactive program to do its job.

For batch processes and API developers who still need to perfect their code, this throttle may be an inadvertent blocker. Just wait and make no API calls (the throttle is reset with each call). The throttle will lift itself in few minutes and API calls may resume.

When the rate limit is exceeded CoffeeCup will send an HTTP 503 status code. The number of seconds until the throttle is lifted is sent via the `Retry-After` HTTP header, as specified in [RFC 2616](http://tools.ietf.org/html/rfc2616#section-14.37). You can use `GET /account/rate_limit_status` to programmatically query your current throttle status.

## Notational Conventions

Throughout our documentation you'll find the following set of notational conventions:

* `{expression}`: Should be substituted with the value of the expression. For example, `/{project_id}` should be replaced with `/12345` (assuming your `project_id` is 12345)

* `...`: For brevity, we have skipped repetitive parts of the response.

* `<!-- Comment -->`: Optional comment in the response added for clarity. The actual response will not contain comments.

## Have More Questions?

Please get in touch with our support at [http://support.coffeecupapp.com](http://support.coffeecupapp.com).
