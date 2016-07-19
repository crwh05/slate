---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the LetsDB API! You can use our API to access LetsDB API endpoints, which can get information on various properties, landlords, and tenants in our database.

We have language bindings in Shell. You can view code examples in the dark area to the right.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Accept: application/json"
  -H "Authorization: Bearer api_key/auth_token"
```

> Make sure to replace `api_key/auth_token` with your API key or auth token.

LetsDB uses API keys to allow applications access to the API. You can register a new LetsDB API key at our [developer portal](http://letsdb.dev).

LetsDB uses API auth tokens to authenticate users. An auth token can be requested by an application with the users credentials.

LetsDB expects for the API key to be included in all API application requests to the server in a header that looks like the following:

`Authorization: Bearer api_key`

<aside class="notice">
You must replace <code>api_key</code> with your application API key.
</aside>

LetsDB expects for the users auth token to be included in all API user requests to the server in a header that looks like the following:

`Authorization: Bearer auth_token`

<aside class="notice">
You must replace <code>auth_token</code> with your user API auth token.
</aside>

<!----------------------------------------------------------------------------->
<!----------------------------------------------------------------------------->

# Auth Tokens

<!----------------------------------------------------------------------------->

## Create an Auth Token


```shell
curl "http://api.letsdb.dev/v1/authtokens"
  -H "Accept: application/json"
  -H "Authorization: Bearer api_key"
  -d "email=john@example.com"
  -d "password=Pass1234"
```

> The above command returns JSON structured like this:

```json
{
  "auth_token":"aB1t"
}
```

This endpoint creates an auth token.

### HTTP Request

`POST http://api.letsdb.dev/v1/authtokens`

### Query Parameters

Parameter | Required/Optional | Description
--------- | ------- | -----------
email | required | User Email address.
password | required | User Password.

<!----------------------------------------------------------------------------->
<!----------------------------------------------------------------------------->

# Users

<!----------------------------------------------------------------------------->

## Create a User

```shell
curl "http://api.letsdb.dev/v1/users"
  -H "Accept: application/json"
  -H "Authorization: Bearer api_key"
  -d "email=john@example.com"
  -d "password=Pass1234"
  -d "password_confirmation=Pass1234"
```

> The above command returns JSON structured like this:

```json
{}
```

This endpoint creates a user.

### HTTP Request

`POST http://api.letsdb.dev/v1/users`

### Query Parameters

Parameter | Required/Optional | Description
--------- | ------- | -----------
email | required | User Email address.
password | required | User Password.
password_confirmation | required | User Password confirmation.

<!----------------------------------------------------------------------------->

## Get a User

```shell
curl "http://api.letsdb.dev/v1/users/2"
    -H "Accept: application/json"
    -H "Authorization: Bearer auth_token"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "email": "john@example.com",
  "validated": true,
  "disabled": false,
  "last_logged_in_date": "2016-07-19T11:33:18+0000",
  "created_at": "2016-07-19T11:23:22+0000",
  "updated_at": "2016-07-19T11:23:22+0000"
}
```

This endpoint retrieves a specific user.


### HTTP Request

`GET http://api.letsdb.dev/v1/users/<id>`

### URL Parameters

Parameter | Description
--------- | -----------
id | The id of the user to retrieve

<!----------------------------------------------------------------------------->

## Update a User

```shell
curl "http://api.letsdb.dev/v1/users/2"
  -X PUT
  -H "Accept: application/json"
  -H "Authorization: Bearer auth_token"
  -d "email=john@example.com"
  -d "password=Pass1234"
  -d "password_confirmation=Pass1234"
```

> The above command returns JSON structured like this:

```json
```

This endpoint updates a user.

### HTTP Request

`PUT http://api.letsdb.dev/v1/users/<id>`

### Query Parameters

Parameter | Description
--------- | -----------
id | The id of the user to delete

<!----------------------------------------------------------------------------->

## Delete a User

```shell
curl "http://api.letsdb.dev/v1/users/2"
  -X DELETE
  -H "Accept: application/json"
  -H "Authorization: Bearer auth_token"
```

> The above command returns JSON structured like this:

```json
```

This endpoint deletes a user.

### HTTP Request

`DELETE http://api.letsdb.dev/v1/users/<id>`

### Query Parameters

Parameter | Description
--------- | -----------
id | The id of the user to delete

<!----------------------------------------------------------------------------->

## Get the Auth User

```shell
curl "http://api.letsdb.dev/v1/user"
    -L
    -H "Accept: application/json"
    -H "Authorization: Bearer auth_token"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "email": "john@example.com",
  "validated": true,
  "disabled": false,
  "last_logged_in_date": "2016-07-19T11:33:18+0000",
  "created_at": "2016-07-19T11:23:22+0000",
  "updated_at": "2016-07-19T11:23:22+0000"
}
```

This endpoint retrieves the authenticated user.


### HTTP Request

`GET http://api.letsdb.dev/v1/users/<id>`

### URL Parameters

Parameter | Description
--------- | -----------
id | The id of the user to retrieve





# Example code

<aside class="success">
Remember — a happy user is an authenticated user!
</aside>

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

<aside class="notice">This error section is stored in a separate file in `includes/_errors.md`. Slate allows you to optionally separate out your docs into many files...just save them to the `includes` folder and add them to the top of your `index.md`'s frontmatter. Files are included in the order listed.</aside>
