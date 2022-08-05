# Welcome to Trisk.io documentation

## Make an HTTP Request in the Trisk.io

There are a lot of ways you can make an HTTP request to the Trisk.io API. You can make a raw HTTP request in your code or by using a tool like [Postman](https://www.postman.com/).

## Credentials

Most of all requests to Trisk.io REST API need to be authenticated. The Trisk.io API uses API keys and [HTTP bearer authentication](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication) to authenticate requests. You can view your API keys in the {Your tenant name} Management -> INTEGRATIONS -> API Key Integration.

Your API keys carry many privileges, so be sure to keep them secure! Do not share your secret API keys in publicly accessible areas such as GitHub, client-side code, and so forth.

Use your API key by  setting it in the headers.
```X-API-KEY``` this is a Public key from the API Key Integration
```X-API-SECRET``` this is a Secret key from the API Key Integration

To get a HTTP bearer authentication token you need to [Authenticate using credentials](https://documentation.develop.trisk.us/api/authenticate-using-credentials#authenticate-using-credentials) and [exchange](https://documentation.develop.trisk.us/api/get-jwt-token-from-authentication#get-jwt-token-from-authentication) the ```auth_codes_internal``` to the jwt bearer token.

Working with an HTTP bearer authentication, you work in the user session, and all user restrictions are included.

**Pay attention!  The HTTP bearer authentication doesn't work without API keys**

All API requests must be made over  [HTTPS](http://en.wikipedia.org/wiki/HTTP_Secure). Calls made over plain HTTP will fail. API requests without authentication will also fail.

## HTTP Methods

Trisk.io uses the GET and POST HTTP methods on the various resources.

## HTTP Headers

Every request should has default Headers:
```Accept: application/vnd.api+json```
```Content-Type: application/vnd.api+json```

API has multi-tenant application scheme. Every request should has X-Domain Header:
```X-Domain: example```

Authorization token should be set via Authorization Header:
```Authorization: Bearer t318a31a-0bcf-48d1-9350-a6ae499007c0```

API doesn't accept DELETE method, instead of this please set X-HTTP-METHOD-OVERRIDE Header:
```X-HTTP-METHOD-OVERRIDE: DELETE```

API doesn't accept PATCH method, instead of this please set X-HTTP-METHOD-OVERRIDE Header:
```X-HTTP-METHOD-OVERRIDE: PATCH```

API doesn't accept PUT method, instead of this please set X-HTTP-METHOD-OVERRIDE Header:
```X-HTTP-METHOD-OVERRIDE: PUT```

More details about where used each method described in the specific request.

## Status Codes

As you make requests, you'll see responses indicating what's happening on the other side of the server. The following is a list of common status codes you'll see in response from the Trisk.io API, and what they mean.

| Status Code | Meaning | Description | 
| -------- | -------- | ------ | 
| 200 | OK | Everything worked as expected.| 
| 201 | CREATED | The request was successful, we created a new resource and the response body contains the representation. This should only appear for POST requests.|
| 401 | UNAUTHORIZED | The client request has not been completed because it lacks valid authentication credentials for the requested resource.|
| 403 | FORBIDDEN | The supplied credentials are not sufficient to access the resource.|
| 404 | NOT FOUND | The requested resource doesn't exist.|
| 422 | UNPROCESSABLE | The server understands the content type of the request entity, and the syntax of the request entity is correct, but it was unable to process the contained instructions.|
| 500 | SERVER ERROR | We couldn't return the representation due to an internal server error.|

# Errors

Trisk.io uses conventional HTTP response codes to indicate the success or failure of an API request.
- Codes in the  `2xx`  range indicate success.
- Codes in the  `4xx`  range indicate an error that failed given the information provided (e.g., a required parameter was omitted, etc.).
- Codes in the  `5xx`  range indicate an error with Trisk.io servers.


# Link Builder Examples

Each request  _CAN_  contains  `include`  and  `fields`  as a  `GET`  parameters

-   include: (string) accepts  `?include=*`  for all nested relationships. For concrete relationships use  `?include=relation_name`. For nested with nested use dot notation  `?include=relationship1.relationship1.1`  For multiple relationships  `?include=relationship_one,relationship_two`

-   fields: (array[string]). By the default response contains all object fields. Accepts:  `fields[relationship_name]=field_one,field_two`  or multiple  `fields[relation_ship_one]=field_one,field_two&fields[relation_two]=field_three`

-   filter: array[string]). By the default response contains all object fields. Accepts:  `filter[property]=value`  or multiple  `filter[property_one]=value&filter[property_two]=another value`  or search (not strict compliance)  `filter[property_one][contains]=value`

**Pay attention! All IDs and credentials in the documentation are examples. To work with the system, you should use actual data.**
