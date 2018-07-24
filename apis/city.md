# City APIs

**Resource path param:** `/city`

## APIs

METHOD | URL | AUTH | USAGE
--- | --- | --- | ---
GET | [`/city`](#GET-/city) | no | List all the active cities.

### <a name="GET-/city"></a>GET `/city`

List all the active cities.

#### Request

MODE | KEY | TYPE | OPTIONAL | DESCRIPTION
--- | --- | --- | --- | ---
QUERY | offset | string | yes | The offset for pagination. *Ref: [Pagination - Request Params](/conventions/basics.md#Pagination--Request-Params)*
QUERY | limit | int | yes | The limit for pagination. *Ref: [Pagination - Request Params](/conventions/basics.md#Pagination--Request-Params)*

#### Response

**Object:** [`city`](/object-models/common-models.md#city)

```javascript
{
	"items": [
		{
			"code": "NEW_YORK",
			"name": "New York"
		}
	],
	"nextUrl": "https://www.headout.com/api/public/v1/city?offset=21,limit=20",
	"prevUrl": "https://www.headout.com/api/public/v1/city?offset=0,limit=20",
	"total": 100,
	"nextOffset": 21
}
```
