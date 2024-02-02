# Product Models

Product signifies an experience that can be sold. Typically, a product will consist of various variants which are the actual bookable entities. A product will have at least 1 variant.
The inventory selection type determine the next steps in the booking flow. If the inventory selection type is `NORMAL`, then there is no involvement of seat selection.
If the inventory selection type is `SEATMAP`, then the user will be required to [select seats](/ui-components/seatmap.md#web-components) in the next step of the booking flow and use the seat ids in the booking request.

* [`product`](#product)
* [`product-content`](#product-content)
* [`rating-cumulative`](#rating-cumulative)
* [`product-variant`](#product-variant)
* [`product-variant-pax`](#product-variant-pax)
* [`product-variant-cashback`](#product-variant-cashback)
* [`product-variant-input-field`](#product-variant-input-field)
* [`product-variant-input-field-validation`](#product-variant-input-field-validation)
* [`product-listing`](#product-listing)
* [`product-listing-pricing`](#product-listing-pricing)
* [`product-listing-pricing-price`](#product-listing-pricing-price)
* [`product-category`](#product-category)

### `product`

Represents the full product information.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
id | string | no | Product id
name | string | no | Name of the product
neighbourhood | string | yes | Neighbourhood of the location of the product
city | [`city`](../common-models.md#city) | no | City of the product
currency | [`currency`](../common-models.md#currency) | no | Native currency of the product. This depends on the country of the product.
images | array[[`image`](../common-models.md#image)] | no | Product images
displayTags | array[string] | yes | Tags signifying the product
content | array[[`product-content`](#product-content)] | no | Content specifying the details of the product
startLocation | [`location`](../common-models.md#location) | no | Location of the start point
endLocation | [`location`](../common-models.md#location) | no | Location of the end point
productType | enum | no | Specifies the type of the product.`enum: TOUR, ACTIVITY, EVENT, ATTRACTION, TRANSFER`
ratingCumulative | [`rating-cumulative`](#rating-cumulative) | no | Cumulative rating of the product
hasInstantConfirmation | boolean | no | `true` if the booking will be instantly confirmed and the tickets will be delivered. If `false` then the booking confirmation and ticket delivery will happen within 20 minutes.
hasMobileTicket | boolean | no | `true` if the ticket can be shown on the mobile at the venue. If `false` you might have to take a print out or show the mobile ticket to get the actual tickets at the venue. The specifics will be mentioned in the product description.
variants | array[[`product-variant`](#product-variant)] | no | Variants of the product. Every product has variants which are the actual bookable entities. If there is only 1 variant, the variant does not have any special significance. If there are more than 1 variant then each variant will have it's own name and description.

### product-content

A content section of the product

| KEY   | TYPE   | NULL/EMPTY | DESCRIPTION                                |
|-------|--------|------------|--------------------------------------------|
| title | string | no         | Title of the content section               |
| html  | string | no         | The content of the section in html format. |

### rating-cumulative

Represent the cumulative rating information.

| KEY   | TYPE  | NULL/EMPTY | DESCRIPTION                                      |
|-------|-------|------------|--------------------------------------------------|
| avg   | float | no         | The average rating                               |
| count | int   | no         | The overall entries used to evaluate the rating. |

### product-variant

Represent a variant entry of the product.

| KEY                    | TYPE                                                          | NULL/EMPTY | DESCRIPTION                                                                                                                                                                                                                                              |
|------------------------|---------------------------------------------------------------|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                     | string                                                        | no         | Variant ID.                                                                                                                                                                                                                                              |
| name                   | string                                                        | yes        | Variant display name. Will be null/empty **only if** there is only 1 variant in a product.                                                                                                                                                               |
| description            | string                                                        | yes        | Variant description.                                                                                                                                                                                                                                     |
| inventoryType          | enum                                                          | no         | Specifies the inventory type of the variant. `enum: FIXED_START_FIXED_DURATION, FIXED_START_FLEXIBLE_DURATION, FLEXIBLE_START_FIXED_DURATION, FLEXIBLE_START_FLEXIBLE_DURATION`. *Ref: [`product-variantinventoryType`](#product-variant-inventoryType)* |
| duration               | int                                                           | yes        | Specifies the duration of the variant in milliseconds. Will be `null` only for `inventoryType` `FIXED_START_FLEXIBLE_DURATION` & `FLEXIBLE_START_FLEXIBLE_DURATION`                                                                                      |
| priceType              | enum                                                          | no         | The pricing type for this inventory. `enum: PER_PERSON, PER_GROUP`. *Ref: [`product-variant.priceType`](#product-variant.priceType).*                                                                                                                    |
| pax                    | [`product-variant-pax`](#product-variant-pax)                 | no         | Specifies the pax/people limit specification for the variant.                                                                                                                                                                                            |
| cashback               | [`product-variant-cashback`](#product-variant-cashback)       | yes        | Specified the cashback that can be achieved by purchasing this variant. It can be `null` if there is no cashback available.                                                                                                                              |
| ticketDeliveryInfoHtml | string                                                        | yes        | Specified how the ticket will be delivered. Currently this is in HTML format. This will transition to an `enum` based approach in upcoming api iterations. This can be `null`/empty if the information is currently not available.                       |
| inputFields            | [`product-variant-input-field`](#product-variant-input-field) | no         | These fields represent the information that need to be taken from the consumer and submitted while making a purchase.                                                                                                                                    |

#### `product-variant-inventoryType`

* `FIXED_START_FIXED_DURATION`: Signifies that the variant experience has a fixed start time and a fixed duration. Eg: Broadway Show, it has a fixed start time and ends at a fixed time.
* `FIXED_START_FLEXIBLE_DURATION`: Signifies that the variant experience has a fixed start time but a flexible duration. Eg: Entry for Rockefeller - Top of the rock observatory. It has a fixed start time, but once you're in, you can stay over there as long as you want till the place closes down.
* `FLEXIBLE_START_FIXED_DURATION`: Signifies that the variant experience has a flexible start time but a fixed duration. Eg: Hot air balloon ride, you can enter at any time, but the duration of the experience is fixed.
* `FLEXIBLE_START_FLEXIBLE_DURATION`: Signifies that the variant experience has a flexible start time and a flexible duration. Eg: Entry tickets for Disneyland, you can enter at any time and can stay there till any time (till the venue closes down).

##### `product-variant.priceType`

* `PER_PERSON`: A `PER_PERSON` price type specifies that there is a price applicable for every person partaking in the booking. There can be different type of people like `Adult`, `Child`, `Senior` etc. with their own age specification. Each individual type can have its own price point.
* `PER_GROUP`: A `PER_GROUP` price type specifies that the inventory is on group pricing. Group pricing signifies that a singular price applies to a group of people and might vary for a given range. For example, 1-4 people $100, 5-7 people $120, 8-10 people $150.

*See Also: [`inventory.pricing`](/object-models/v1/inventory-pricing-models.md.md#inventory)*

### `product-variant-pax`

Specified the pax/people limitation specification for a variant

| KEY | TYPE | NULL/EMPTY | DESCRIPTION                                                                                                                       |
|-----|------|------------|-----------------------------------------------------------------------------------------------------------------------------------|
| min | int  | no         | Specifies the lower limit for number of people to be present in a booking. If there is no lower limit, this will be 0.            |
| max | int  | yes        | Specifies the upper limit for number of people that can be present in a booking. If there is no upper limit, this will be `null`. |

### `product-variant-cashback`

Specifies the cashback specifications for a variant.

| KEY   | TYPE   | NULL/EMPTY | DESCRIPTION                                                                                                                                                                                                                                                                                            |
|-------|--------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| value | float  | no         | Value of the cashback.                                                                                                                                                                                                                                                                                 |
| type  | string | no         | Specified the type of cashback. `enum: ABSOLUTE, PERCENTAGE`. A `value` of `10` with `type` `ABSOLUTE` represents that the user will get an absolute cashback of `10` value in the product's currency. If `type` is `PERCENTAGE` the user will get a cashback of `10%` of the overall variant's price. |

### `product-variant-input-field`

Specifies a user input field for a variant which is required to make a booking.

| KEY        | TYPE                                                                                | NULL/EMPTY | DESCRIPTION                                                                                                                                                                            |
|------------|-------------------------------------------------------------------------------------|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id         | string                                                                              | no         | An ID representing the field for the variant.                                                                                                                                          |
| name       | string                                                                              | no         | Display name of the field                                                                                                                                                              |
| dataType   | enum                                                                                | no         | Data type of the field. `enum: INT, FLOAT, STRING, BOOL, ENUM`. *Ref: [`product-variant-input-field.dataType`](#product-variant-input-field.dataType)*                                 |
| level      | enum                                                                                | no         | Specified the level of applicability of the field. `enum: PRIMARY_CUSTOMER`, `ALL_CUSTOMERS`, `TOUR`. *Ref: [`product-variant-input-field.level`](#product-variant-input-field.level)* |
| validation | [`product-variant-input-field-validation`](#product-variant-input-field-validation) | no         | Specifies the validation required for the field.                                                                                                                                       |

##### <a name="product-variant-input-field.dataType"></a>`product-variant-input-field.dataType`

* `INT`: Represents an **integer** type.
* `FLOAT`: Represents a **float**/**double** type.
* `STRING`: Represents a **string** type.
* `BOOL`: Represents a **bool** type.
* `ENUM`: Represents an **enumeration** type. The applicable values will be specified in [`product-variant-input-field-validation.values`](#product-variant-input-field-validation).

##### <a name="product-variant-input-field.level"></a>`product-variant-input-field.level`

* `PRIMARY_CUSTOMER`: Represents that the field only needs to be asked for the primary customer. A primary customer represents the customer who will be internally linked for the booking. There is only 1 primary customer per booking. There will always be at least 1 input field representing the primary customer.  Typically **Full name**, **Email**, **Phone Number** & **Address** and mostly asked as information required for the primary customer.
* `ALL_CUSTOMERS`: Represents that the field needs to be asked for all the customers included in the booking (including the primary customer). Typically, fields asking for all customer information are not there. Nevertheless, there can be cases where information like **Weight**, **Height**, **Meal preference** etc. are required for all the customers.
* `VARIANT`: Represents that the field information needs to be taken on a variant level. It is agnostic to customer or the number of customers partaking in a booking. It needs to be collected only once just like `PRIMARY_CUSTOMER`, nevertheless, it does not represent information of a user. Hence, a separate enumeration to signify the difference which can help with UI organization.

### `product-variant-input-field-validation`

Specifies the validation contract for a variant input field.

| KEY       | TYPE          | NULL/EMPTY | DESCRIPTION                                                                                                                                                                            |
|-----------|---------------|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| required  | bool          | no         | Specifies whether the input field is mandatory or not.                                                                                                                                 |
| regex     | string        | yes        | The regex validation for the field                                                                                                                                                     |
| minLength | int           | yes        | The minimum length required for the field. This can be `null` if not applicable (example for `dataType` `INT` fields)                                                                  |
| maxLength | int           | yes        | The maximum length required for the field. This can be `null` if not applicable (example for `dataType` `INT` fields)                                                                  |
| minValue  | int           | yes        | The minimum value required for the field. This can be `null` if not applicable (example for `dataType` `STRING` fields)                                                                |
| maxValue  | int           | yes        | The maximum value required for the field. This can be `null` if not applicable (example for `dataType` `STRING` fields)                                                                |
| values    | array[string] | no         | Specifies that the field values need to be restricted to entries in this array. This is applicable only for `dataType` `ENUM` fields. For other `dataType`, this will be `null`/empty. |

### `product-listing`

Represent a product's listing

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
id | string | no | Product ID.
name | string | no | Product name.
url | string | no | URL for the product
city | [`city`](../common-models.md#city) | no | City of the product
image | [`image`](../common-models.md#image) | no | The primary image for the product.
neighbourhood | string | yes | The neighbourhood of the location of the product.
primaryCategory | [`product-category`](#product-category) | no | The primary category for the product.
startGeolocation | [`geo-location`](../common-models.md#geolocation) | no | The geo location of the product.
ratingCumulative | [`rating-cumulative`](#rating-cumulative) | no | The cumulative rating of the product.
pricing | [`product-listing-pricing`](#product-listing-pricing) | no | Specifies the pricing data for the product listing

### `product-listing-pricing`

Represents the pricing data for the product listing

| KEY          | TYPE                                                              | NULL/EMPTY | DESCRIPTION                                                                                                                                                                                                                                                                                                                                                                  |
|--------------|-------------------------------------------------------------------|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| type         | enum                                                              | no         | Specifies the price type for the product. `enum: PER_PERSON, PER_GROUP`. Although this is on a variant level, nevertheless, right now we don't support any products with variants of different price types. Hence this is value is currently specified over here. This might get deprecated in the future. *Ref: [`product-variant.priceType`](#product-variant-priceType).* |
| currencyCode | string                                                            | no         | The currency code of the price.                                                                                                                                                                                                                                                                                                                                              |
| minimumPrice | [`product-listing-pricing-price`](#product-listing-pricing-price) | no         | Object specifying the minimum price applicable for the product.                                                                                                                                                                                                                                                                                                              |
| bestDiscount | int                                                               | no         | The best discount available across all available inventory.                                                                                                                                                                                                                                                                                                                  |

### `product-listing-pricing-price`

Represents a price object for listing pricing.

| KEY           | TYPE  | NULL/EMPTY | DESCRIPTION                                                 |
|---------------|-------|------------|-------------------------------------------------------------|
| originalPrice | float | no         | The original retail price for the corresponding final price |
| finalPrice    | float | no         | The final sale price.                                       |

### `product-category`

Represents a minimal category object for product.

| KEY      | TYPE   | NULL/EMPTY | DESCRIPTION                                       |
|----------|--------|------------|---------------------------------------------------|
| id       | string | no         | The ID of the category.                           |
| name     | string | no         | The display name of the category.                 |
| cityCode | string | no         | The city of the category. Eg: `NEW_YORK`, `DUBAI` |
| url      | string | no         | The relative url for the category page.           |
