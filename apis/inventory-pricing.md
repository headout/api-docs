# Inventory & Pricing APIs

**Resource path param:** `/inventory`

## APIs

METHOD | URL | AUTH | USAGE
--- | --- | --- | ---
GET | [`/inventory/list-by/variant`](#GET-/inventory/list-by/variant) | no | Get the available inventory for a variant.

### <a name="GET-/inventory/list-by/variant"></a>GET `/inventory/list-by/variant`

Get the available inventory for a variant.

#### Request

MODE | KEY | TYPE | OPTIONAL | DESCRIPTION
--- | --- | --- | --- | ---
QUERY | variantId | string | no | The ID of the variant for which the inventory needs to be fetched.
QUERY | offset | string | yes | The offset for pagination. *Ref: [Pagination - Request Params](/conventions/basic.md#Pagination--Request-Params)*
QUERY | limit | int | yes | The limit for pagination. *Ref: [Pagination - Request Params](/conventions/basic.md#Pagination--Request-Params)*

#### Response

**Object:** [`pagination-wrapper`](/object-models/common-models.md#pagination-wrapper)`<`[`inventory`](/object-models/inventory-models.md#inventory)`>`

```javascript
{
	"items": [
		{
			"startDateTime": "2017-03-30T15:30:00",
			"endDateTime": "2017-03-30T15:30:00",
			"availability": "LIMITED/UNLIMITED/CLOSED",
			"remaining": 5,
			"pricing": {
				"persons": [
					{
						"type": "ADULT",
						"name": "Adult",
						"ageFrom": 6,
						"ageTo": 10,
						"price": 100
					}
				],
				"groups": [
					{
						"size": 4,
						"price": 100,
					}
				]
			}
		}
	],
	"nextUrl": "https://www.headout.com/api/v1/inventory/list-by/variant?variant-id=1234,offset=21,limit=20",
	"prevUrl": "https://www.headout.com/api/v1/inventory/list-by/variant?variant-id=1234,offset=0,limit=20",
	"total": 100,
	"nextOffset": 21
}
```
