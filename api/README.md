# Getting started :id=title

You can use Guizhan Image Hosting API to do just about anything you can do on our website.

The Guizhan Image Hosting API is a RESTful API based on HTTPS and JSON responses. If you are registered, you can obtain your API token from ["API tokens"](https://www.gzssimg.com/app/my/tokens) page.

## Endpoints :id=endpoints

The API is accessed by making HTTPS requests to a specific version endpoint URL, in which GET, POST, PUT, PATCH, and DELETE methods dictate how your interact with the information available. Every endpoint is accessed only via the SSL-enabled HTTPS (port 443) protocol.

The base URL for all endpoints is:

```
https://api.gzssimg.com/v1/
```

## Requests :id=requests

Requests must be sent over HTTPS with a payload formatted in JSON or FormData. The requests are authenticated with valid API Tokens.

### API Tokens :id=api-tokens

API tokens are the only way to authenticate with Guizhan Image Hosting API.

*Headers*

|Name|Format|Description|
|-|-|-|
|**API Token**|Authorization: Bearer &lt;token&gt;|API Token generated from ["API tokens"](https://www.gzssimg.com/app/my/tokens) page|

### Example request :id=example-request

Requests are generally formatted as follows:

```
GET images
```

**API Token cURL** (example)

```
curl -X GET "https://api.gzssimg.com/v1/images" \
     -H "Content-Type:application/json" \
     -H "Authorization: Bearer eyJ0eXAiOi...8FAaCFU8"
```

### Rate limiting :id=rate-limiting

The Guizhan Image Hosting API sets a maximum of 60 requests in a one minute period.

### Pagination :id=pagination

Depending on your request, the results returned may be limited. You can page through the returned results with the following query parameters.

|Name|Type|Description|
|-|-|-|
|page|*integer*|Which page of results to return|
|per_page|*integer*|How many results to return per page|
|order|*string*|Attribute name to order the responses by|
|direction|*string*|Either `ASC` or `DESC`|

**cURL** (example)

```
curl -X GET "https://api.gzssimg.com/v1/images?page=2&per_page=10&order=upload_time&direction=DESC" \
     -H "Content-Type:application/json" \
     -H "Authorization: Bearer eyJ0eXAiOi...8FAaCFU8"
```

## Responses :id=responses

### Format

Each response is a JSON object. The data requested is wrapped in the `result` tag. If you have a response, it will always be within the `result` field. We also include two fields `code` and `message` in the response. The `code` of a success response is 0.

Date fields will always be in UTC ISO-8601 format, including microseconds.

**Success response** (example)

```json
{
    "code": 0,
    "message": null,
    "result": [
        {
            "name":"HNxEE3W",
            "fullname":"HNxEE3W.jpeg",
            "size":24902,
            "upload_time":"2021-01-09T17:52:03.000000Z",
            "url":"https:\/\/gzimg.cc\/21w01\/HNxEE3W.jpeg"
        }
    ]
}
```

**Error response** (example)

```json
{
    "code": 1002,
    "message": "Image size exceeds the limit.",
    "result": []
}
```