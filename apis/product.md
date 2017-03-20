# Product

**Resource path param:** `/product`

## APIs

METHOD | URL | USAGE
--- | --- | ---
GET | [`/product/get/{product_id}`](#GET-/product/get/{product_id}) | Get product by `id`.
GET | [`/product/inventory/get/{product_id}`]() | Get product inventory by `id`
GET | [`/product/listing/list-by/city`]() | List product listing by city

### <a name="GET-/product/get/{product_id}"></a>GET `/product/get/{product_id}`

Gets a product by `product_id`.

#### Request

MODE | KEY | TYPE | OPTIONAL | DESCRIPTION
--- | --- | --- | --- | ---
PATH | product_id | string | no | Product id

#### Response

**Object:** [product-listing]()

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
			"url": "//cdn-imgix.headout.com/tour/647/TOUR-IMAGE/a9e14ae1-78ab-4cbe-8166-2e55f3060c42-512-new-york-wicked-07.jpg"[currency]()
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
			"countryName": "United States"
			"postalCode": "10036",
		}
	},
	"productType": "EVENT",
	"ratingCumulative": {
		"avg": 4.2,
		"count": 251
	}
	"variants": [
		{
			"id": 654,
			"name": "Orchestra (Center Rows: A-O,AA-CC, Side Rows:A-J)",	// nullable
			"description": "The best view of all the seat groups",	// nullable
			"inventoryType": "FIXED_START_FIXED_DURATION",
			"duration": 9000000,
			"pax": {
				"min": 1,	// nullable
				"max": 9,	// nullable
			},
			"cashback": {	// nullable
				"value": 10,
				"type": "PERCENTAGE",
			},
			"ticketDeliveryInfoHtml": "<p>Your booking confirmation will be emailed to you shortly.</p>",
			"inputFields": [	// not empty
				{
					"id": "SOME_ID", // NAME, EMAIL, ADDRESS, PHONE, CUSTOM_<id>
					"name": "Name",
					"dataType": "STRING",	// INT, FLOAT, STRING, BOOL, ENUM
					"level": "PRIMARY_CUSTOMER"	// PRIMARY_CUSTOMER, ALL_CUSTOMERS, TOUR
					"validation": [
						"required": true,
						"regex": "\\s*[^\\s]+\\s+[^\\s]+.*", // optional
						"minLength": 3, // optional
						"maxLength": 80	// optional
						"minValue": null,		//optional
						"maxValue": null, // optional
						"values": [	// optional. This is available only when "dataType" == "ENUM"
							"Vegetarian",
							"Non-vegeratian",
							"Diabetic"
						]
					]
				}
			]
		}
	]
}
```
