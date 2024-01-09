# Basics

* [Domain](#domain)
* [API Response Format](#api-response-format)
* [HTTPS](#https)
* [Versioning](#versioning)
* [Authentication](#authentication)
* [Pagination](#pagination)

## Domain

All production API calls need to be sent to <a href="https://www.headout.com">`https://www.headout.com`</a>. For testing, use the <a href="https://sandbox.api.test-headout.com/">`https://sandbox.api.test-headout.com`</a>

## API Response Format

All APIs return a response in JSON format.

## HTTPS

APIs run over `HTTPS`. If you specify `HTTP`, the url will be redirected to `HTTPS` using `HTTP Status 301` (Permanent Redirect).

## Versioning

### Endpoints
- All Partner APIs are prefixed with `/api/public/v{api_version}`. E.g. if the version of the API is `v2.beta`, the url will be `/api/public/v2.beta`. 
- For V1 which worked under the previous paradigm of `/api/v1` will still work, but it is recommended to shift to the new url structure `/api/public/v1`.

## Authentication

In dealing with v1 and v2 APIs, it's important to note that while v1 APIs have a mix of open APIs that don't require authorization and those that do, it's generally best to use authorization for all API calls. This eliminates the need to differentiate between those that require it and those that don't. However, in the case of v2 APIs, authorization is a mandatory requirement for every API call, without exception.

Currently, the authorization happens via api keys provided to concerned parties.

### API Key based

#### `Headout-Auth` header

You need to specify your api key in `Headout-Auth` header with a request for authorization to happen.

`Headout-Auth: {api-token}`

**Example:** `Headout-Auth: pk_fgjsfg597sf7g5shsfhgf7hs7fg57s64sfg74h`

#### Key types

There are two types of api keys, production and testing. You will always get both the keys.

* Production Keys: Production keys will only authorize in our production environment and are prefixed with `pk_`. All live production work should use this key.
* Testing Keys: Testing keys will only authorize in our testing sandbox environment and are prefixed with `tk_`. All testing work should use this key.

#### <a name="Authentication--Testing-Sandbox">Testing Sandbox

Our testing sandbox can be accessed at <a href="https://sandbox.api.test-headout.com">`https://sandbox.api.test-headout.com`</a>. You will need to use the test api key to access the same.

#### Get API Keys

Please signup on our <a href="https://partner.headout.com/affiliate">Affiliate platform</a> to receive your api keys via email.

## Pagination

All apis which return a list result implement the pagination contract, until and unless, it's specified otherwise in the API which can only be in the case if the resulting list will theoretically always be small.

#### <a name="Pagination--Request-Params"></a>Request Params

You can provide the following **optional** params in the **query params** to control pagination for any request which supports pagination.

| KEY    | TYPE   | DESCRIPTION                                                                                                                                                                                                                                                                                                                                                                                               |
|--------|--------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| offset | string | The offset from which the page should start. Typically this offset is an integer which starts from `0` and going on till `total - 1`, nevertheless, for cursor based apis this offset might be a cursor based string which may not have any correlation with subsequent keys. Such apis will mention this usage. If unspecified the default offset of `0` or the starting point of the cursor is assumed. |
| limit  | int    | The number of elements to be fetched. If unspecified this defaults to `20` unless the API states otherwise.                                                                                                                                                                                                                                                                                               |

#### Response

Pagination responses are wrapped with a [`pagination-wrapper<T>`](/object-models/common-models.md#pagination-wrapper). You can use the pagination wrapper to help with navigation along with getting to know other metadata about the current pagination.

```json
{
	"items": [],
	"nextUrl": "https://next-url",
	"prevUrl": "https://prev-url",
	"total": 100,
	"nextOffset": 20
}
```
