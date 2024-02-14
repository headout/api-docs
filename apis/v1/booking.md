# Booking APIs

**Resource path param:** `/booking`

## APIs

| METHOD | URL                                                           | AUTH | USAGE                                                    |
|--------|---------------------------------------------------------------|------|----------------------------------------------------------|
| GET    | [`/booking`](#GET-/booking)                                   | yes  | Fetch all bookings.                                      |
| GET    | [`/booking/{id}`](#GET-/booking/{id})                         | yes  | Fetch a booking by it's id.                              |
| POST   | [`/booking`](#POST-/booking)                                  | yes  | Create a booking in `UNCAPTURED` state.                  |
| PUT    | [`/booking/{id}`](#PUT-/booking)                              | yes  | Modify the state of the booking given it's id.           |
| POST   | *`DEPRECATED`* [~~`/booking/create`~~](#POST-/booking/create) | yes  | Create a booking. Use: [`POST /booking`](#POST-/booking) |

### <a name="GET-/booking"></a>GET `get-booking`

List all bookings.

#### Response

**Object:** [`pagination-wrapper`](/object-models/common-models.md#pagination-wrapper)`<`[`booking`](/object-models/v1/booking-models.md#booking)`>`

<details>
<summary>Response Example</summary>

```json
{
	"items": [{
		"bookingId": "126890",
		"partnerReferenceId": "AX67873DDFSR",
		"variantId": "1234",
		"startDateTime": "2017-04-12T19:30:00",
		"product": {
			"id": "2832",
			"name": "Aladdin",
			"variant": {
				"id": "4384",
				"name": "Grand Circle"
			}
		},
		"customersDetails": {
			"count": 3,
			"customers": [{
				"personType": "ADULT",
				"isPrimary": true,
				"inputFields": [{
					"id": "EMAIL",
					"name": "Name",
					"value": "a@b.com"  
				}]
			}]  
		},
		"variantInputFields": [{
			"id": "TRANSPORTATION_TYPE",
			"name": "Transportation Type",
			"value": "Limousine"
		}],
		"price": {
			"amount": 100,
			"currencyCode": "USD"
		},
		"status": "COMPLETED",
		"voucherUrl": "https://www.headout.com/voucher/126890?key=AAAD6AAAABhsDVGlVXsL2YDAf65qMsOQAlqJZdsw80eczQCIL6sa5rITsvOjxoD5NwaoBDiwlEY%3D",
		"tickets": [
		{
			"publicId": "9e4d8330-abc7-40f8-951d-19b9e8731dcf",
			"url": "https://cdn-s3.headout.com/itinerary/126890/voucher-9e4d8330-abc7-40f8-951d-19b9e8731dcf.pdf"
		}],
		"creationTimestamp": 1491902295

	}],
	"nextUrl": "https://www.headout.com/api/public/v1/booking?offset=1&limit=1",
	"prevUrl": null,
	"total": 100,
	"nextOffset": 1
}
```

</details>

### <a name="GET-/booking/{id}"></a>GET `/booking/{id}`

Get a booking by its ID.

#### Request

| MODE | KEY | TYPE   | OPTIONAL | DESCRIPTION     |
|------|-----|--------|----------|-----------------|
| PATH | id  | string | no       | The booking id. |

#### Response

**Object:** [`booking`](/object-models/v1/booking-models.md#booking)

<details>
<summary>Response Example</summary>

```json
{
	"bookingId": "126890",
	"partnerReferenceId": "AX67873DDFSR",
	"variantId": "1234",
	"startDateTime": "2017-04-12T19:30:00",
	"product": {
		"id": "2832",
		"name": "Aladdin",
		"variant": {
			"id": "4384",
			"name": "Grand Circle"
		}
	},
	"customersDetails": {
		"count": 3,
		"customers": [{
			"personType": "ADULT",
			"isPrimary": true,
			"inputFields": [{
				"id": "EMAIL",
				"name": "Name",
				"value": "a@b.com"  
			}]
		}]  
	},
	"variantInputFields": [{
		"id": "TRANSPORTATION_TYPE",
		"name": "Transportation Type",
		"value": "Limousine"
	}],
	"price": {
		"amount": 100,
		"currencyCode": "USD"
	},
	"status": "COMPLETED",
	"voucherUrl": "https://www.headout.com/voucher/126890?key=AAAD6AAAABhsDVGlVXsL2YDAf65qMsOQAlqJZdsw80eczQCIL6sa5rITsvOjxoD5NwaoBDiwlEY%3D",
	"tickets": [
	{
		"publicId": "9e4d8330-abc7-40f8-951d-19b9e8731dcf",
		"url": "https://cdn-s3.headout.com/itinerary/126890/voucher-9e4d8330-abc7-40f8-951d-19b9e8731dcf.pdf"
	}],
	"creationTimestamp": 1491902295
}
```
</details>

### <a name="POST-/booking"></a>POST `/booking`

Create a new booking object in `UNCAPTURED` state.

The booking creation and acceptance flow is a 2-step flow. Calling this API creates the initial booking in `UNCAPTURED` state and returns back the same booking along with the new booking id. You should call this API before fulfilling the booking flow on your end. Once you get a response, you can then fulfill the booking flow on your end and then call [`PUT /booking`](#PUT-/booking) to capture the booking and start the fulfillment process of the booking on our end.

If the booking capturing doesn't happen within an hour then the booking status is automatically changed to `CAPTURE_TIMEOUT`.

#### Request

**Object:** [`booking`](/object-models/v1/booking-models.md#booking)

<details>
<summary>Request Example</summary>

```json
{
	"variantId": "1234",
	"inventoryId": "1455",
    "inventorySeatIds": ["SE-GRANDCIRCLE-A-20","SE-GRANDCIRCLE-A-21"], 
	"customersDetails": {
		"count": 3,
		"customers": [{
			"personType": "ADULT",
			"isPrimary": true,
			"inputFields": [{
				"id": "EMAIL",
				"value": "a@b.com"  
			}]
		}]  
	},
	"variantInputFields": [{
		"id": "",
		"value": ""
	}],
	"price": {
		"amount": 100,
		"currencyCode": "USD"
	}       
}
```
</details>

#### Response

**Object:** [`booking`](/object-models/v1/booking-models.md#booking)

<details>
<summary>Response Example</summary>

```json
{
	"bookingId": "126890",
	"partnerReferenceId": null,
	"variantId": "1234",
	"startDateTime": "2017-04-12T19:30:00",
	"product": {
		"id": "2832",
		"name": "Aladdin",
		"variant": {
			"id": "4384",
			"name": "Grand Circle"
		}
	},
	"customersDetails": {
		"count": 3,
		"customers": [{
			"personType": "ADULT",
			"isPrimary": true,
			"inputFields": [{
				"id": "EMAIL",
				"name": "Name",
				"value": "a@b.com"  
			}]
		}]  
	},
	"variantInputFields": [{
		"id": "TRANSPORTATION_TYPE",
		"name": "Transportation Type",
		"value": "Limousine"
	}],
	"price": {
		"amount": 100,
		"currencyCode": "USD"
	},
	"status": "UNCAPTURED",
	"voucherUrl": "https://www.headout.com/voucher/126890?key=AAAD6AAAABhsDVGlVXsL2YDAf65qMsOQAlqJZdsw80eczQCIL6sa5rITsvOjxoD5NwaoBDiwlEY%3D",
	"tickets": [],
	"creationTimestamp": 1491902295
}
```

</details>

### <a name="PUT-/booking"></a>PUT `/booking/{id}`

Used to modify a booking. Currently, this is only used for capturing the booking and assigning a `partnerReferenceId`. Use this method to capture the booking by specifying the status as `PENDING`. The booking will be fulfilled on our end only once you capture it.

#### Request

**Object:** [`booking`](/object-models/v1/booking-models.md#booking)

<details>
<summary>Request Example</summary>

```json
{
	"status": "PENDING",
	"partnerReferenceId": "AX67873DDFSR"
}
```
</details>

#### Response

**Object:** [`booking`](/object-models/v1/booking-models.md#booking)

<details>
<summary>Response Example</summary>

```json
{
	"bookingId": "126890",
	"partnerReferenceId": "AX67873DDFSR",
	"variantId": "1234",
	"startDateTime": "2017-04-12T19:30:00",
	"product": {
		"id": "2832",
		"name": "Aladdin",
		"variant": {
			"id": "4384",
			"name": "Grand Circle"
		}
	},
	"customersDetails": {
		"count": 3,
		"customers": [{
			"personType": "ADULT",
			"isPrimary": true,
			"inputFields": [{
				"id": "EMAIL",
				"name": "Name",
				"value": "a@b.com"  
			}]
		}]  
	},
	"variantInputFields": [{
		"id": "TRANSPORTATION_TYPE",
		"name": "Transportation Type",
		"value": "Limousine"
	}],
	"price": {
		"amount": 100,
		"currencyCode": "USD"
	},
	"status": "PENDING",
	"voucherUrl": "https://www.headout.com/voucher/126890?key=AAAD6AAAABhsDVGlVXsL2YDAf65qMsOQAlqJZdsw80eczQCIL6sa5rITsvOjxoD5NwaoBDiwlEY%3D",
	"tickets": [],
	"creationTimestamp": 1491902295

}
```
</details>

### <a name="POST-/booking/create"></a>`DEPRECATED` ~~POST `/booking/create`~~

Creates a booking

#### Request

**Object:** [`booking`](/object-models/v1/booking-models.md#booking)

<details>
<summary>Request Example</summary>

```json
{
	"variantId": "1234",
	"inventoryId": "1455",
	"customersDetails": {
		"priceType" : "PER_PERSON",
		"count": 3,
		"customers": [{
			"personType": "ADULT",
			"isPrimary": true,
			"inputFields": [{
				"id": "EMAIL",
				"value": "a@b.com"  
			}]
		}]  
	},
	"variantInputFields": [{
		"id": "",
		"value": ""
	}],
	"price": {
		"amount": 100,
		"currencyCode": "USD"
	}       
}
```
</details>

#### Response

**Object:** [`booking-create-response`](/object-models/v1/booking-models.md#booking-create-response)

<details>
<summary>Response Example</summary>

```json
{
	"itineraryId": "122725",
	"price": {
		"amount": 102,
		"currencyCode": "GBP"
	}
}
```
</details>