# Basics

* [Domain](#domain)
* [API Response Format](#api-response-format)
* [HTTPS](#https)
* [Versioning](#versioning)
* [Authentication](#authentication)
* [Pagination](#pagination)

## Domain

All production API calls need to be sent to <a href="https://www.headout.com">`https://www.headout.com`</a>. For testing, use the [testing sandbox environment](#Authentication--Testing-Sandbox).

## API Response Format

All APIs return a response in JSON format.

## HTTPS

APIs run over `HTTPS`. If you specify `HTTP`, the url will be redirected to `HTTPS` using `HTTP Status 301` (Permanent Redirect).

## Versioning

### Url Prefix

All APIs are prefixed with `/api/public/v{version_number}`. If the current version number is `1` then the your API prefix will be `/api/public/v1`. All previous APIs which worked under the previous paradigm of `/api/v{version_numer}` will still work but it is recommended to shift to the new url structure.

##### Deprecated
~~All APIs are prefixed with `/api/v{version_number}`. If the current version number is `1` then the your api prefix will be `/api/v1`.~~

## Authentication

There are certain APIs which can only be executed with appropriate authentication/authorization in place. Although there are open APIs which do not required authorization, it is recommended that you provide the authorization for every API call so that you do no need to care about which API mandates it.

Currently the authorization happens via api keys provided to concerned parties.

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

Our testing sandbox can be accessed at <a href="https://www.test-headout.com">`https://www.test-headout.com`</a>. You will need to use the test api key to access the same.

#### Get API Keys
<!-- ##Not working -->
Please signup on our <a href="https://www.headout.com/concierge/signup">Affiliate platform</a> to receive your api keys via email.

## Pagination

All apis which return a list result implement the pagination contract, until and unless, it's specified otherwise in the API which can only be in the case if the resulting list will theoretically always be small.

#### <a name="Pagination--Request-Params"></a>Request Params

You can provide the following **optional** params in the **query params** to control pagination for any request which supports pagination.

KEY | TYPE | DESCRIPTION
--- | --- | ---
offset | string | The offset from which the page should start. Typically this offset is an integer which starts from `0` and going on till `total - 1`, nevertheless, for cursor based apis this offset might be a cursor based string which may not have any correlation with subsequent keys. Such apis will mention this usage. If unspecified the default offset of `0` or the starting point of the cursor is assumed.
limit | int | The number of elements to be fetched. If unspecified this defaults to `20` unless the API states otherwise.

#### Response

Pagination responses are wrapped with a [`pagination-wrapper<T>`](/object-models/common-models.md#pagination-wrapper). You can use the pagination wrapper to help with navigation along with getting to know other metadata about the current pagination.

```javascript
{
	"items": [],
	"nextUrl": "https://next-url",
	"prevUrl": "https://prev-url",
	"total": 100,
	"nextOffset": 20
}
```
