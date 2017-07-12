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
QUERY | startDateTime | string | yes | The start date time from which the inventory needs to be fetched. If unspecified then the current timestamp is taken into consideration. *Format: [fm-date-time](/conventions/formats.md#fm-date-time)*. *Ref: [`inventory.startDateTime`](#inventory.startDateTime)*
QUERY | endDateTime | string | yes | The end date time till which the inventory needs to be fetched. If unspecified then this is taken as infinity. *Format: [fm-date-time](/conventions/formats.md#fm-date-time)*. *Ref: [`inventory.startDateTime`](#inventory.startDateTime)*
QUERY | offset | string | yes | The offset for pagination. *Ref: [Pagination - Request Params](/conventions/basics.md#Pagination--Request-Params)*
QUERY | limit | int | yes | The limit for pagination. *Ref: [Pagination - Request Params](/conventions/basics.md#Pagination--Request-Params)*

#### Response

**Object:** [`pagination-wrapper`](/object-models/common-models.md#pagination-wrapper)`<`[`inventory`](/object-models/inventory-pricing-models.md#inventory)`>`

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
	"nextUrl": "https://www.headout.com/api/v1/inventory/list-by/variant?variantId=1234,offset=21,limit=20",
	"prevUrl": "https://www.headout.com/api/v1/inventory/list-by/variant?variantId=1234,offset=0,limit=20",
	"total": 100,
	"nextOffset": 21
}
```
