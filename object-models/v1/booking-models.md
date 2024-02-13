# Common Models

* [`booking`](#booking)
* [`booking-product`](#booking-product)
* [`booking-customers-details`](#booking-customers-details)
* [`booking-customer`](#booking-customer)
* [`booking-input-field`](#booking-input-field)
* [`booking-create-response`](#booking-create-response)
* [`ticket`](#ticket)

### `booking`

Represents the complete booking object.

KEY | TYPE | METHOD | NULL/EMPTY | DESCRIPTION
--- | --- | --- | --- | ---
bookingId | string | `GET` | no | The id of the booking.
partnerReferenceId | string | `GET` `PUT` | yes | The reference id provided by a partner while making the booking. This is provided in the second booking step called using `PUT`.
variantId | string | `GET` `POST` | no | ID of the variant of the product that needs to be booked. Every product has atleast 1 bookable variant entry.
inventoryId | string | `POST` | no | ID of the inventory that needs to be booked. This id itself will not be stored, but will be used to fetch `startDateTime`, pricing profile for price validation etc.
startDateTime | string | `GET` | no | The start date time of the experience. This could also signify the opening time for an attraction depending upon the inventory type. *Format: [fm-date-time](/conventions/formats.md#fm-date-time)* *Ref: [`product-variant.inventoryType`](product-models.md#product-variant.inventoryType)*
product | [`booking.product`](#booking-product) | `GET` | no | Minimalistic information about the product booked.
customersDetails | [`booking-customers-details`](#booking-customers-details) | `GET` `POST` | no | All the details of the customers partaking in the booking.
variantInputFields | array[[`booking-input-field`](#booking-input-field)] | `GET` `POST` | yes | Variant level input field. For `POST` the values that are required to be submitted are specified in [product-variant.inputFields](product-models.md#product-variant).
price | [`price`](../common-models.md#price) | `GET` `POST` | no | The price at which the purchase needs is made. This needs to be submitted in `POST` for backend verification. The submitted currency currently should conform to the currency of the product.
status | enum | `GET` `PUT` | no | The current status of the booking. After `POST` this will always be `UNCAPTURED`. The status can be changed using `PUT` to `PENDING` to specify to the backend. `enum: UNCAPTURED ,PENDING ,COMPLETED ,CANCELLED ,DIRTY , CAPTURE_TIMEDOUT`. *Ref: [`booking.status`](#booking.status)*
voucherUrl | string | `GET` | no | Link to the voucher of the booking. Voucher is inherently a dynamic entity and currently can either be a PDF or an HTML page.
tickets | array[[`ticket`](#ticket)] | `GET` | yes | An array of tickets associated with this booking. This can be empty if the booking hasn't been confirmed or cancelled.
creationTimestamp | int | `GET` | no | The epoch timestamp specifying the time when the booking was created. *Format: [fm-timestamp](/conventions/formats.md#fm-timestamp)*.

##### <a name="booking.status"></a>`booking.status`

* `UNCAPTURED`: This state means that the booking entry is created on our system but in a dormant state. It will not be processed by our system until the state is changed to `PENDING`. Bookings with `UNCAPTURED` status are automatically moved to `CAPTURE_TIMEOUT` state after 1 hour and are then can not be captured.
* `PENDING`: This state means that the booking has been captured and is now being processed by our system.
* `COMPLETED`: The booking is successful and has been completed.
* `CANCELLED`: The booking has been cancelled.
* `DIRTY`: The booking has been modified from its original specification. This happens only when specific booking modification requests are made by the customer. This might evolve into a different specification in the future.
* `CAPTURE_TIMEOUT`: If a booking has been there on our system in `UNCAPTURED` state for more than an hour it is moved to `CAPTURE_TIMEOUT` state and then cannot be captured.

### `booking-product`

| KEY     | TYPE                                                  | METHOD | NULL/EMPTY | DESCRIPTION                                  |
|---------|-------------------------------------------------------|--------|------------|----------------------------------------------|
| id      | string                                                | `GET`  | no         | The id of the product                        |
| name    | string                                                | `GET`  | no         | The name of the product                      |
| variant | [`booking-product-variant`](#booking-product-variant) | `GET`  | no         | The variant of the product which was booked. |

### `booking-product-variant`

| KEY  | TYPE   | METHOD | NULL/EMPTY | DESCRIPTION                                                                               |
|------|--------|--------|------------|-------------------------------------------------------------------------------------------|
| id   | string | `GET`  | no         | The is of the variant                                                                     |
| name | string | `GET`  | yes        | The name of the variant. This can be empty if this is the default variant of the product. |

### `booking-customers-details`

Represents all the details for the customers partaking in the booking.

| KEY       | TYPE                                           | METHOD       | NULL/EMPTY | DESCRIPTION                                    |
|-----------|------------------------------------------------|--------------|------------|------------------------------------------------|
| count     | int                                            | `GET` `POST` | no         | The number of people partaking in the booking. |
| customers | array[[`booking-customer`](#booking-customer)] | `GET` `POST` | no         | Array of details of every customer.            |

### `booking-customer`

Details of a singular customer

| KEY         | TYPE                                                | METHOD       | NULL/EMPTY | DESCRIPTION                                                                                                                                                                                                                                          |
|-------------|-----------------------------------------------------|--------------|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| personType  | string                                              | `GET` `POST` | yes        | The person type if the `priceType` is `PER_PERSON`. Not required/present if `priceType` is `PER_GROUP`. *Ref: [`product-variant.priceType`](product-models.md#product-variant.priceType) & [`pricing.persons`](inventory-pricing-models.md#pricing)* |
| isPrimary   | bool                                                | `GET` `POST` | no         | Specifies whether this customer is the primary customer or not. There needs to be exactly 1 primary customer in [`booking-customers-details.customers`](#booking-customers-details)                                                                  |
| inputFields | array[[`booking-input-field`](#booking-input-field) | `GET` `POST` | yes        | All the input fields for this level customer as specified in [`product-variant.inputFields`](product-models.md#product-variant).                                                                                                                     |

### `booking-input-field`

An input field which represents the submission of the contract represented by [`product-variant-input-field`](product-models.md#product-variant-input-field)

| KEY   | TYPE   | METHOD       | NULL/EMPTY | DESCRIPTION                                                                           |
|-------|--------|--------------|------------|---------------------------------------------------------------------------------------|
| id    | string | `GET` `POST` | no         | The ID of the field.                                                                  |
| name  | string | `GET`        | no         | The name of the field. Not required for `POST` since the id field signifies the same. |
| value | string | `GET` `POST` | no         | The submitted value of the field.                                                     |

### `booking-create-response`

Response object for booking create api (api has been deprecated).

KEY | TYPE | METHOD | NULL/EMPTY | DESCRIPTION
--- | --- | --- | --- | ---
itineraryId | string | `GET` | no | The ID for the booking.
price | [`price`](../common-models.md#price) | `GET` | no | The price payed for the booking.

### `ticket`

Represents information of a ticket. The ticket accessed via `url` is always in PDF format.

| KEY      | TYPE   | METHOD | NULL/EMPTY | DESCRIPTION                   |
|----------|--------|--------|------------|-------------------------------|
| publicId | string | `GET`  | no         | The public id for the ticket. |
| url      | string | `GET`  | no         | The url to access the ticket. |
