# Common Models

* [`booking-create`](#booking-create)
* [`booking-create-customers-details`](#booking-create-customers-details)
* [`booking-create-customer`](#booking-create-customer)
* [`booking-create-input-field`](#booking-create-input-field)
* [`booking-create-response`](#booking-create-response)

### `booking-create`

Represents all the information required to create a booking

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
variantId | string | no | ID of the variant of the product that needs to be booked. Every product has atleast 1 bookable variant entry.
inventoryId | string | no | ID of the inventory that needs to be booked.
customerDetails | [`booking-create-customers-details`](#booking-create-customers-details) | no | All the details required of the customers partaking in the booking.
variantInputFields | array[[`booking-create-input-field`](#booking-create-input-field)] | yes | Any variant level input field values that were required to be submitted as specified in [product-variant.inputFields](product-models.md#product-variant).
price | [`price`](common-models.md#price) | no | The price at which the purchase needs to be made. The currency currently should conform to the currency of the product.

### `booking-create-customers-details`

Represents all the details for the customers partaking in the booking.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
priceType | enum | no | The price type as specified in the inventory. `enum: PER_PERSON, PER_GROUP`. TODO: Ref to inventory.
count | int | no | The number of people partaking in the booking
customers | array[[`booking-create-customer`](#booking-create-customer)] | no | Details of a singular customer

### `booking-create-customer`

Details of a singular customer

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
personType | string | yes | The person type if the `priceType` is `PER_PERSON`. Not required if `priceType` is `PER_GROUP`. *Ref: [`product-variant.priceType`](#product-models.md#product-variant.priceType) & [`pricing.persons`](inventory-pricing-models.md#pricing.persons)*
isPrimary | bool | no | Specifies whether this customer is the primary customer or not. There need to be exactly 1 primary customer in [`booking-create-customers-details.customers`](#booking-create-customers-details)
inputFields | array[[`booking-create-input-field`](#booking-create-input-field) | yes | All the input fields for this level customer as specified in [`product-variant.inputFields`](product-models.md#product-variant).

### `booking-create-input-field`

An input field which represents the submission of the contract represented by [`product-variant-input-field`](product-models.md#product-variant-input-field)

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
id | string | no | The ID of the field.
value | string | no | The submitted value of the field.

### `booking-create-response`

Response object for a booking.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
itineraryId | string | no | The ID for the booking. TODO: Does this make sense?
price | [`price`](common-models.md#price) | no | The price payed for the booking.
