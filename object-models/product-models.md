# Product Models

Product signifies an experience that can be sold. Typically a product will consist of various variants which are the actual bookable entities. A product will have atleast 1 variant.

* [product](#product)
* [product-content](#product-content)
* [rating-cumulative](#rating-cumulative)
* [product-variant](#product-variant)
* [product-variant-pax](#product-variant-pax)
* [product-variant-cashback](#product-variant-cashback)
* [product-variant-input-field](#product-variant-input-field)
* [product-variant-input-field-validation](#product-variant-input-field-validation)
* [product-listing](#product-listing)

### product

Represents the full product information.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
id | string | no | Product id
name | string | no | Name of the product
neighbourhood | string | yes | Neighbourhood of the location of the product
city | [city](common-models.md#city) | no | City of the product
currency | [currency](common-models.md#currency) | no | Native currency of the product. This depends on the country of the product.
images | array[[image](common-models.md#image)] | no | Product images
displayTags | array[string] | yes | Tags signifying the product
content | array[[product-content](#product-content)] | no | Content specifying the details of the product
startLocation | [location](common-models.md#location) | no | Location of the start point
endLocation | [location](common-models.md#location) | no | Location of the end point
productType | enum | no | Specifies the type of the product.`enum: TOUR, ACTIVITY, EVENT, ATTRACTION, TRANSFER`
ratingCumulative | [rating-cumulative](#rating-cumulative) | no | Cumulative rating of the product
variants | array[[product-variant](#product-variant)] | no | Variants of the product. Every product has variants which are the actual bookable entities. If there is only 1 variant, the variant does not have any special significance. If there are more than 1 variant then each variant will have it's own name and description.

### product-content

A content section of the product

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
title | string | no | Title of the content section
html | string | no | The content of the section in html format.

### rating-cumulative

Represent the cumulative rating information.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
avg | float | no | The average rating
count | int | no | The overall entries used to evaluate the rating.

### product-variant

Represent a variant entry of the product.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
id | string | no | Variant ID.
name | string | yes | Variant display name. Will be null/empty **only if** there is only 1 variant in a product.
description | string | yes | Variant description.
inventoryType | enum | no | Specifies the inventory type of the variant. `enum: FIXED_START_FIXED_DURATION, FIXED_START_FLEXIBLE_DURATION, FLEXIBLE_START_FIXED_DURATION, FLEXIBLE_START_FLEXIBLE_DURATION`. Ref: [product-variant.inventoryType](#product-variant--inventoryType)
duration | int | yes | Specifies the duration of the variant. Will be `null` only for `inventoryType` `FIXED_START_FLEXIBLE_DURATION` & `FLEXIBLE_START_FLEXIBLE_DURATION`
pax | [product-variant-pax](#product-variant-pax) | no | Specifies the pax/people limit specification for the variant.
cashback | [product-variant-cashback](#product-variant-cashback) | yes | Specified the cashback that can be achieved by purchasing this variant. It can be `null` if there is no cashback available.
ticketDeliveryInfoHtml | string | yes | Specified how the ticket will be delivered. Currently this is in HTML format. This will transition to an `enum` based approach in upcoming api iterations. This can be `null`/empty if the information is currently not available.
inputFields | [product-variant-input-field](#product-variant-input-field) | no | These fields represent the information that need to be taken from the consumer and submitted while making a purchase.

##### <a name="product-variant--inventoryType"></a>`product-variant.inventoryType`

* `FIXED_START_FIXED_DURATION`: Signifies that the variant experience has a fixed start time and a fixed duration. Eg: Broadway Show, it has a fixed start time and ends at a fixed time.
* `FIXED_START_FLEXIBLE_DURATION`: Signifies that the variant experience has a fixed start time but a flexible duration. Eg: Entry for Rockefeller - Top of the rock observatory. It has a fixed start time, but once you're in, you can stay over there as long as you want till the place closes down.
* `FLEXIBLE_START_FIXED_DURATION`: Signifies that the variant experience has a flexible start time but a fixed duration. Eg: Hot air balloon ride, you can enter at any time, but the duration of the experience is fixed.
* `FLEXIBLE_START_FLEXIBLE_DURATION`: Signifies that the variant experience has a flexible start time and a flexible duration. Eg: Entry tickets for Disneyland, you can enter at any time and can stay there till any time (till the venue closes down).

TODO: Ref to how inventory startDateTime & endDateTime meaning changes wrt this.

### product-variant-pax

Specified the pax/people limitation specification for a variant

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
min | int | no | Specifies the lower limit for number of people to be present in a booking. If there is no lower limit, this will be 0.
max | int | yes | Specifies the upper limit for number of people that can be present in a booking. If there is no upper limit, this will be `null`.

### product-variant-cashback

Specifies the cashback specifications for a variant.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
value | float | no | Value of the cashback.
type | string | no | Specified the type of cashback. `enum: ABSOLUTE, PERCENTAGE`. A `value` of `10` with `type` `ABSOLUTE` represents that the user will get an absoute cashback of `10` value in the product's currency. If `type` is `PERCENTAGE` the user will get a cashback of `10%` of the overall variant's price.

### product-variant-input-field

Specifies a user input field for a variant which is required to make a booking.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
id | string | no | An ID representing the field for the variant.
name | string | no | Display name of the field
dataType | enum | no | Data type of the field. `enum: INT, FLOAT, STRING, BOOL, ENUM`. Ref: [product-variant-input-field.dataType](#product-variant-input-field--dataType)
level | enum | no | Specified the level of applicability of the field. `enum: PRIMARY_CUSTOMER`, `ALL_CUSTOMERS`, `TOUR`. Ref: [product-variant-input-field.level](#product-variant-input-field--level).
validation | [product-variant-input-field-validation](#product-variant-input-field-validation) | no | Specifies the validation required for the field.

##### <a name="product-variant-input-field--dataType"></a>`product-variant-input-field.dataType`

* `INT`: Represents an **integer** type.
* `FLOAT`: Represents a **float**/**double** type.
* `STRING`: Represents a **string** type.
* `BOOL`: Represents a **bool** type.
* `ENUM`: Represents an **enumeration** type. The applicable values will be specified in [product-variant-input-field-validation](#product-variant-input-field-validation).`values`.

##### <a name="product-variant-input-field--level"></a>`product-variant-input-field.level`

* `PRIMARY_CUSTOMER`: Represents that the field only needs to be asked for the primary customer. A primary customer represents the customer who will be internally linked for the booking. There is only 1 primary customer per booking. There will always be atleast 1 input field representing the primary customer.  Typically **Full name**, **Email**, **Phone Number** & **Address** and mostly asked as information required for the primary customer.
* `ALL_CUSTOMERS`: Represents that the field needs to be asked for all the customers included in the booking (including the primary customer). Typically fields asking for all customer information are not there. Nevertheless there can be cases where information like **Weight**, **Height**, **Meal preference** etc. are required for all the customers.
* `VARIANT`: Represents that the field information needs to be taken on a variant level. It is agnostic to customer or the number of customers partaking in a booking. It needs to be collected only once just like `PRIMARY_CUSTOMER`, nevertheless, it does not represent information of a user. Hence a separate enumeration to signify the difference which can help with UI organization.

### product-variant-input-field-validation

Specifies the validation contract for a variant input field.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
required | bool | no | Specifies whether the input field is mandatory or not.
regex | string | yes | The regex validation for the field
minLength | int | yes | The minimum length required for the field. This can be `null` if not applicable (example for `dataType` `INT` fields)
maxLength | int | yes | The maximum length required for the field. This can be `null` if not applicable (example for `dataType` `INT` fields)
minValue | int | yes | The minimum value required for the field. This can be `null` if not applicable (example for `dataType` `STRING` fields)
maxValue | int | yes | The maximum value required for the field. This can be `null` if not applicable (example for `dataType` `STRING` fields)
values | array[string] | no | Specifies that the field values need to be restricted to entries in this array. This is applicable only for `dataType` `ENUM` fields. For other `dataType`, this will be `null`/empty.

### product-listing

Represent a product's listing

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
id | string | no | Product ID.
name | string | no | Product name.
url | string | no | URL for the product
city | [city](common-models#city) | no | City of the product
image | [image](common-models.md#image) | no | The primary image for the product.
neighbourhood | string | yes | The neighbourhood of the location of the product.
primaryCategory | [category](category-models.md#category) | no | The primary category for the product.
startGeolocation | [geo-location](common-models#geolocation) | no | The geo location of the product.
ratingCumulative | [rating-cumulative](#rating-cumulative) | no | The cumulative rating of the product.

### inventory

Represents the inventory of a variant.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
startDateTime | string | no | Start local date time for the inventory. Format: TODO
endDateTime | string | no | End local date time for the inventory. Format: TODO
availability | enum | no | Specifies the type of availability for the inventory. `enum: LIMITED, UNLIMITED, CLOSED`. Ref: [inventory.availability](#inventory--availability)
remaining | int | no | The total number of seats left which can be booked for this inventory.
type | enum | no | The pricing type for this inventory. `enum: PER_PERSON, PER_GROUP`. Ref: [inventory.type](#inventory--type). TODO: `priceType`
persons | array[[price-person](#price-person)] | yes | Specifies the specification for per person pricing. This is non-empty only if `priceType` is `PER_PERSON`.
groups | array[[price-group](#price-group)] | no | Specifies the specification for per person pricing. This is non-empty only if `priceType` is `PER_GROUP`.

##### <a name="inventory--availability"></a>`inventory.availability`

* `LIMITED`: Specifies that there is limited availability for this inventory and the remaining seats can be fetched from [inventory.remaining](#inventory)
* `UNLIMITED`: Specifies that there is unlimited availability for this inventory and can be booked any number of times.
* `CLOSED`: Specified that the inventory is closed.

TODO: See if this is necessary.

##### <a name="inventory--type"></a>`inventory.type`

* `PER_PERSON`: A `PER_PERSON` type specifies that there is a price applicable for every person partaking in the booking. There can be different type of people like `Adult`, `Child`, `Senior` etc. with their own age specification. Each individual type can have it's own price point.
* `PER_GROUP`: A `PER_GROUP` type specifies that the inventory is on group pricing. Group pricing signifies that a singular price applies to a group of people and might vary for a given range. For example, 1-4 people $100, 5-7 people $120, 8-10 people $150.

TODO: Shouldn't this be on a Variant level?

### price-person

Specifies the specification for per person pricing. This is only applicable for `PER_PERSON` price types.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
id | string | no | The ID of the specification.
name | string | no | The displayable name for the person. Ex: `Adult`, `Child`, `Senior`
ageFrom | int | yes | The minimum age for the type. If this not specified then there is no minimum age.
ageTo | int | no | The maximum age for the type. If this is not specified then there is no macimum age.
price | float | no | The price payable for this type.

TODO: Need to tell the type -> id, name change.

### price-group

Specifies the specification for per group pricing. This is only applicable for `PER_GROUP` price types.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
size | int | no | The upper bound of the size of this group. The lower bound is the next lowest size overall from this size plus 1.
price | float | no | The price payable for this type.

##### Eg:

`size=4, price=100; size=7, price=120; size=10, prize=150`

Signifies (For currency $):

`1-4 persons cost $100; 5-7 persons cost $120; 8-10 persons cost $150`
