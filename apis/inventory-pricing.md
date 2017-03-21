# Inventory API

**Resource path param:** `/inventory`

## APIs

METHOD | URL | USAGE
--- | --- | ---
GET | [`/inventory/list-by/variant`](#GET-/inventory/list-by/variant) | Get the available inventory for a variant.

### <a name="GET-/inventory/list-by/variant"></a>GET `/inventory/list-by/variant`

Get the available inventory for a variant.

#### Request

MODE | KEY | TYPE | OPTIONAL | DESCRIPTION
--- | --- | --- | --- | ---
QUERY | variant-id | string | no | The ID of the variant for which the inventory needs to be fetched.

#### Response

**Object:** [inventory](/object-models/inventory-models#inventory)

```javascript
[
	{
		"startDateTime": "2017-03-30T15:30:00",	// based on inventory_type, can serve as start or opening time
		"endDateTime": "2017-03-30T15:30:00",	// based on inventory_type, can serve as end or closing time
		"availability": "LIMITED/UNLIMITED/CLOSED",
		"remaining": 5,
		"pricing": {
			"persons": [	// nullable
				{
					"type": "ADULT",
					"name": "Adult",
					"ageFrom": 6,	// nullable
					"ageTo": 10,	// nullable
					"price": 100
				}
			],
			"groups": [	//nullable
				{
					"size": 4,
					"price": 100,
				}
			]
		}
	}
]
```
