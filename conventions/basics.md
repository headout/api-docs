# Basics

## API Response Format

All APIs return a response in JSON format.

## Https

APIs run over `https`. If you specify `http`, the url will be redirected to `https` using HTTP Status 301 (Permanent Redirect).

## Versioning

### Url Prefix

All APIs are prefixed with `/api/v{version_number}`. If the current version number is `1` then the your api prefix will be `/api/v1`.

## Authentication

TODO:

## Pagination

All apis which return a list result implement the pagination contract, until and unless, it's specified otherwise in the API which can only be in the case if the resulting list will theoretically always be small.

### <a name="Pagination--Request-Params"></a>Request Params

You can provide the following **optional** params in the **query params** to control pagination for any request which supports pagination.

KEY | TYPE | DESCRIPTION
--- | --- | ---
`offset` | string | The offset from which the page should start. Typically this offset is an integer which starts from `0` and going on till `total - 1`, nevertheless, for cursor based apis this offset might be a cursor based string which may not have any correlation with subsequent keys. Such apis will mention this usage. If unspecified the default offset of `0` or the starting point of the cursor is assumed.
`limit` | int | The number of elements to be fetched. If unspecified this defaults to `20` unless the API states otherwise.

### Response

Pagination responses are wrapped with a [pagination-wrapper](/object-models/common-models.md#pagination-wrapper). You can use the pagination wrapper to help with navigation along with getting to know other metadata about the current pagination.

```javascript
{
	"items": [],
	"nextUrl": "https://next-url",
	"prevUrl": "https://prev-url",
	"total": 100,
	"nextOffset": 21
}
```
