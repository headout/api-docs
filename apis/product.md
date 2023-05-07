# Product APIs

**Resource path param:** `/product`

## APIs

METHOD | URL | AUTH | USAGE
--- | --- | --- | ---
GET | [`/product/get/{product_id}`](#GET-/product/get/{product_id}) | no | Get product by `id`.
GET | [`/product/listing/list-by/city`](#GET-/product/listing/list-by/city) | no | List product listing by city
GET | [`/product/listing/list-by/category`](#GET-/product/listing/list-by/category) | no | List product listing by category

### <a name="GET-/product/get/{product_id}"></a>GET `/product/get/{product_id}`

Gets a product by `productId`.

#### Request

MODE | KEY | TYPE | OPTIONAL | DESCRIPTION
--- | --- | --- | --- | ---
PATH | product-id | string | no | Product id

#### Response

**Object:** [`product`](/object-models/product-models.md#product)

```javascript
{
	"id": 512,
	"name": "Wicked",
	"neighbourhood": "Theatre District",
	"city": {
		"code": "NEW_YORK",
		"name": "New York"
	},
	"currency": {
		"code": "USD",
		"name": "United States Dollar",
		"symbol": "US$",
		"localSymbol": "$",
		"precision": 2,
	},
	"images": [
		{
			"url": "//cdn-imgix.headout.com/tour/647/TOUR-IMAGE/a9e14ae1-78ab-4cbe-8166-2e55f3060c42-512-new-york-wicked-07.jpg"
		}
	],
	"displayTags": [
		"Broadway",
		"Musical",
		"Best of Broadway",
		"Entertainment"
	],
	"content": [
		{
			"title": "Summary",
			"html": "<p>Before Dorothy arrived in Oz, there was a girl with emerald-green skin — misunderstood, and extremely talented.</p>"
		}
	],
	"startLocation": {
		"latitude": 40.762393951416016,
		"longitude": -73.9851303100586,
		"addressLine1": "The Gershwin Theatre",
		"addressLine2": "222 W 51st Street",
		"cityName": "New York",
		"postalCode": "10036",
		"state": "New York",
		"countryName": "United States"
	},
	"endLocation": {
		"geo": {
			"latitude": 40.762393951416016,
			"longitude": -73.9851303100586,
		}
		"address": {
			"line1": "The Gershwin Theatre",
			"ine2": "222 W 51st Street",
			"cityName": "New York",
			"stateName": "New York",
			"countryName": "United States",
			"postalCode": "10036",
		}
	},
	"productType": "EVENT",
	"ratingCumulative": {
		"avg": 4.2,
		"count": 251
	},
	"hasInstantConfirmation": true,
	"hasMobileTicket": true,
	"variants": [
		{
			"id": 654,
			"name": "Orchestra (Center Rows: A-O,AA-CC, Side Rows:A-J)",
			"description": "The best view of all the seat groups",
			"inventoryType": "FIXED_START_FIXED_DURATION",
			"duration": 9000000,
			"priceType": "PER_PERSON",
			"pax": {
				"min": 1,
				"max": 9,
			},
			"cashback": {
				"value": 10,
				"type": "PERCENTAGE",
			},
			"ticketDeliveryInfoHtml": "<p>Your booking confirmation will be emailed to you shortly.</p>",
			"inputFields": [
				{
					"id": "SOME_ID",
					"name": "Name",
					"dataType": "STRING",
					"level": "PRIMARY_CUSTOMER",
					"validation": {
						"required": true,
						"regex": "\\s*[^\\s]+\\s+[^\\s]+.*",
						"minLength": 3,
						"maxLength": 80,
						"minValue": null,
						"maxValue": null,
						"values": [
							"Vegetarian",
							"Non-vegeratian",
							"Diabetic"
						]
					}
				}
			]
		}
	]
}
```

### <a name="GET-/product/listing/list-by/city"></a>GET `/product/listing/list-by/city`

List product listing using city.

#### Request

MODE | KEY | TYPE | OPTIONAL | DESCRIPTION
--- | --- | --- | --- | ---
QUERY | cityCode | string | no | The city code. Eg: `NEW_YORK`, `DUBAI`
QUERY | offset | string | yes | The offset for pagination. *Ref: [Pagination - Request Params](/conventions/basics.md#Pagination--Request-Params)*
QUERY | limit | int | yes | The limit for pagination. *Ref: [Pagination - Request Params](/conventions/basics.md#Pagination--Request-Params)*
QUERY | currencyCode | string | yes | The currency in which pricing information will be returned. Eg: `USD`, `AED`. *Ref: [https://en.wikipedia.org/wiki/ISO_4217](https://en.wikipedia.org/wiki/ISO_4217)*

#### Response

**Object:** [`pagination-wrapper`](/object-models/common-models.md#pagination-wrapper)`<`[`product-listing`](/object-models/product-models.md#product-listing)`>`

```javascript
{
	"items": [
		{
			"id": "Product ID",
			"name": "Product Name",
			"url": "https://product_url",
			"city": {
				"code": "NEW_YORK",
				"displayName": "New York"
			},
			"image": {
				"url": "https://imageurl"
			},
			"neighbourhood": "Madison Square Garden",
			"primaryCategory": {
				"id": "123",
				"name": "Broadway",
				"cityCode": "NEW_YORK",
				"canonicalUrl": "https://www.headout.com/category/24/broadway"
			},
			"startGeolocation": {
				"latitude": 40.701568603515625,
				"longitude": -74.0091323852539
			},
			"ratingCumulative": {
				"avg": 3.5,
				"count": 5
			},
			"pricing": {
			    "type": "PER_PERSON",
			    "currencyCode": "AED",
			    "minimumPrice": {
			        "originalPrice": 551,
			        "finalPrice": 518,
			    }
			    "bestDiscount": 28
			}
		}
	],
	"nextUrl": "https://www.headout.com/api/public/v1/product/listing/list-by/city?cityCode=NEW_YORK,offset=21,limit=20",
	"prevUrl": "https://www.headout.com/api/public/v1/product/listing/list-by/city?cityCode=NEW_YORK,offset=0,limit=20",
	"total": 100,
	"nextOffset": 21
}
```

### <a name="GET-/product/listing/list-by/category"></a>GET `/product/listing/list-by/category`

List product listing using category.

#### Request

MODE | KEY | TYPE | OPTIONAL | DESCRIPTION
--- | --- | --- | --- | ---
QUERY | categoryId | string | no | The id of the category.
QUERY | offset | string | yes | The offset for pagination. *Ref: [Pagination - Request Params](/conventions/basics.md#Pagination--Request-Params)*
QUERY | limit | int | yes | The limit for pagination. *Ref: [Pagination - Request Params](/conventions/basics.md#Pagination--Request-Params)*
QUERY | currencyCode | string | yes | The currency in which pricing information will be returned. Eg: `USD`, `AED`. *Ref: [https://en.wikipedia.org/wiki/ISO_4217](https://en.wikipedia.org/wiki/ISO_4217)*

#### Response

**Object:** [`pagination-wrapper`](/object-models/common-models.md#pagination-wrapper)`<`[`product-listing`](/object-models/product-models.md#product-listing)`>`

```javascript
{
	"items": [
		{
			"id": "Product ID",
			"name": "Product Name",
			"url": "https://product_url",
			"city": {
				"code": "NEW_YORK",
				"displayName": "New York"
			},
			"image": {
				"url": "https://imageurl"
			},
			"neighbourhood": "Madison Square Garden",
			"primaryCategory": {
				"id": "123",
				"name": "Broadway",
				"cityCode": "NEW_YORK",
				"canonicalUrl": "https://www.headout.com/category/24/broadway"
			},
			"startGeolocation": {
				"latitude": 40.701568603515625,
				"longitude": -74.0091323852539
			},
			"ratingCumulative": {
				"avg": 3.5,
				"count": 5
			},
			"pricing": {
			    "type": "PER_PERSON",
			    "currencyCode": "AED",
			    "minimumPrice": {
			        "originalPrice": 551,
			        "finalPrice": 518,
			    }
			    "bestDiscount": 28
			}
		}
	],
	"nextUrl": "https://www.headout.com/api/public/v1/product/listing/list-by/category?categoryId=23,offset=21,limit=20",
	"prevUrl": "https://www.headout.com/api/public/v1/product/listing/list-by/category?categoryId=23,offset=0,limit=20",
	"total": 100,
	"nextOffset": 21
}
```
