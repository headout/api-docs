# Booking API

**Resource path param:** `/booking`

## APIs

METHOD | URL | USAGE
--- | --- | ---
POST | [`/booking/create`](#POST-/booking/create) | Create a booking.

### <a name="POST-/booking/create"></a>GET `/booking/create`

Creates a booking

#### Request

**Object:** [`booking-create`](/object-models/booking-models.md#booking-create)

```javascript
{
    "variantId": "1234",
    "inventoryId": "1455",
    "customersDetails": {
        "priceType" : "PER_PERSON",
        "count": 3,
        "customers": [
			{
	            "personType": "ADULT",
	            "isPrimary": true,
	            "inputFields": [{
	                "id": "EMAIL",
	                "value": "a@b.com"  
	            }]
        	}
        }]  
    },
    "variantInputFields": [
		{
	        "id": "",
	        "value": ""
    	}
	],
    "price": {
        "amount": 100,
        "currencyCode": "USD"
    }       
}
```

#### Response

**Object:** [`booking-create-response`](/object-models/booking-models.md#booking-create-response)

```javascript
{
  "itineraryId": "122725",
  "price": {
    "amount": 102,
    "currencyCode": "GBP"
  }
}
```
