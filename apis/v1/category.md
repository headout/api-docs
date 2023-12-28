# Category/Collection APIs

**Resource path param:** `/category`

## APIs

| METHOD | URL                                                     | AUTH | USAGE                        |
|--------|---------------------------------------------------------|------|------------------------------|
| GET    | [`/category/list-by/city`](#GET-/category/list-by/city) | no   | List all categories by city. |

### <a name="GET-/category/list-by/city"></a>GET `/category/list-by/city`

List all categories by city.

#### Request

| MODE  | KEY      | TYPE   | OPTIONAL | DESCRIPTION                                                                                                        |
|-------|----------|--------|----------|--------------------------------------------------------------------------------------------------------------------|
| QUERY | cityCode | string | no       | The city code. Eg: `NEW_YORK`, `DUBAI`                                                                             |
| QUERY | offset   | string | yes      | The offset for pagination. *Ref: [Pagination - Request Params](/conventions/basics.md#Pagination--Request-Params)* |
| QUERY | limit    | int    | yes      | The limit for pagination. *Ref: [Pagination - Request Params](/conventions/basics.md#Pagination--Request-Params)*  |

#### Response

**Object:** [`category`](/object-models/v1/category-models.md#category)

<details>
<summary>Response Example</summary>

```json
{
	"items": [
		{
			"id": "123",
			"name": "Broadway",
			"cityCode": "NEW_YORK",
			"canonicalUrl": "https://www.headout.com/category/24/broadway"
		}
	],
	"nextUrl": "https://www.headout.com/api/public/v1/category/list-by/city?cityCode=NEW_YORK,offset=21,limit=20",
	"prevUrl": "https://www.headout.com/api/public/v1/category/list-by/city?cityCode=NEW_YORK,offset=0,limit=20",
	"total": 100,
	"nextOffset": 21
}
```
</details>