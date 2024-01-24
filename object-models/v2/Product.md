# `Product`

Represents detailed information about a specific product.

| KEY                                                                                           | TYPE                                | NULL/EMPTY | DESCRIPTION                                                                             |
|-----------------------------------------------------------------------------------------------|-------------------------------------|------------|-----------------------------------------------------------------------------------------|
| id                                                                                            | String                              | no         | Unique identifier for the product.                                                      |
| name                                                                                          | String                              | no         | Name of the product.                                                                    |
| canonicalUrl                                                                                  | String                              | no         | Canonical URL of the product.                                                           |
| city                                                                                          | [City](./../common-models.md#city)  | no         | Object representing the city associated with the product.                               |
| media                                                                                         | List<[MediaDetails](#MediaDetails)> | no         | List of media details (images, videos) associated with the product.                     |
| startLocation                                                                                 | [Geolocation](#Geolocation)         | no         | Geographical coordinates for the starting location of the product.                      |
| productType                                                                                   | TourType                            | no         | Type of the product (TOUR, ACTIVITY, EVENT, ATTRACTION, TRANSFER, AIRPORT_TRANSFER).    |
| reviewsSummary                                                                                | [ReviewDetails](#ReviewDetails)     | no         | Summary of product reviews including ratings count and average rating.                  |
| listingPrice                                                                                  | [ListingPrice](#ListingPrice)       | yes        | Listing price details for the product. Can be null.                                     |
| currency                                                                                      | [Currency](#Currency)               | no         | Currency information for the product pricing.                                           |
| localeSpecificUrls                                                                            | Map<String, String>                 | yes        | Mapping of language codes to their respective URL strings for the product. Can be null. |
| hasInstantConfirmation                                                                        | Boolean                             | no         | Indicates whether the product has instant confirmation.                                 |
| hasMobileTicket                                                                               | Boolean                             | no         | Indicates whether the product supports mobile ticketing.                                |
| primaryCategory                                                                               | [Category](./Category.md)           | yes        | Primary category associated with the product. Can be null.                              |
| primarySubCategory                                                                            | [SubCategory](./Subcategory.md)     | yes        | Primary sub-category associated with the product. Can be null.                          |
| primaryCollection                                                                             | [Collection](./Collection.md)       | yes        | Primary collection associated with the product. Can be null.                            |
| variants (Only when fetching a specific product; Variants don't get returned on the bulk API) | List<[Variant](#Variant)>           | yes        | List of variants of the product. Can be null.                                           |

## `MediaDetails`

Represents media details associated with the product.

| KEY  | TYPE      | NULL/EMPTY | DESCRIPTION                       |
|------|-----------|------------|-----------------------------------|
| url  | String    | no         | URL of the media.                 |
| type | MediaType | no         | Type of the media (IMAGE, VIDEO). |

## `Geolocation`

Represents the geolocation coordinates.

| KEY       | TYPE   | NULL/EMPTY | DESCRIPTION                 |
|-----------|--------|------------|-----------------------------|
| latitude  | Double | no         | Latitude of the coordinate  |
| longitude | Double | no         | Longitude of the coordinate |

## `ReviewDetails`

Represents summary details of product reviews.

| KEY           | TYPE       | NULL/EMPTY | DESCRIPTION                       |
|---------------|------------|------------|-----------------------------------|
| ratingsCount  | Int        | no         | Count of ratings for the product. |
| averageRating | BigDecimal | no         | Average rating of the product.    |

## `ListingPrice`

Represents the pricing details of a product.

| KEY          | TYPE                          | NULL/EMPTY | DESCRIPTION                                        |
|--------------|-------------------------------|------------|----------------------------------------------------|
| type         | PriceProfileType              | no         | Type of the price profile. (PER_PERSON, PER_GROUP) |
| currencyCode | Currency                      | no         | Currency code for the pricing.                     |
| minimumPrice | [MinimumPrice](#MinimumPrice) | no         | Minimum price details for the product.             |
| bestDiscount | int                           | no         | Best available discount on the product.            |

## `Currency`

Represents currency information relevant to a product.

| KEY          | TYPE     | NULL/EMPTY | DESCRIPTION                          |
|--------------|----------|------------|--------------------------------------|
| code         | String   | no         | Currency code.                       |
| currencyName | String   | no         | Full name of the currency.           |
| symbol       | String   | no         | Currency symbol.                     |
| localSymbol  | String   | no         | Local symbol for the currency.       |
| precision    | Integer  | no         | Precision of the currency value.     |
| currency     | Currency | no         | Enum representing the currency type. |

## `Variant`
Represents a variant of a product.

| KEY                    | TYPE                          | NULL/EMPTY | DESCRIPTION                                                                                                                                                     |
|------------------------|-------------------------------|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                     | Int                           | no         | Unique identifier for the variant.                                                                                                                              |
| name                   | String                        | no         | Name of the variant. Can be null.                                                                                                                               |
| description            | String                        | no         | Description of the variant. Can be null.                                                                                                                        |
| duration               | Long                          | yes        | Duration of the variant. Can be null.                                                                                                                           |
| inventoryType          | InventoryType                 | no         | Type of inventory for the variant. (FIXED_START_FIXED_DURATION, FLEXIBLE_START_FIXED_DURATION, FIXED_START_FLEXIBLE_DURATION, FLEXIBLE_START_FLEXIBLE_DURATION) |
| pax                    | [Pax](#Pax)                   | no         | Pax details for the variant.                                                                                                                                    |
| cashback               | [CashBack](#CashBack)         | yes        | Cashback information for the variant. Can be null.                                                                                                              |
| ticketDeliveryInfoHtml | String                        | yes        | HTML content for ticket delivery information. Can be null.                                                                                                      |
| inputFields            | List<[UserField](#UserField)> | no         | List of user input fields for the variant.                                                                                                                      |
| tags                   | Set<String>                   | no         | Set of tags associated with the variant.                                                                                                                        |

## `Pax`
Represents the passenger (pax) capacity details for a tour or activity.

| KEY | TYPE | NULL/EMPTY | DESCRIPTION                                                                       |
|-----|------|------------|-----------------------------------------------------------------------------------|
| min | Int  | no         | The minimum number of passengers required.                                        |
| max | Int  | yes        | The maximum number of passengers allowed. Can be null if there is no upper limit. |

## `CashBack`
Represents cashback information associated with a product or service.

| KEY   | TYPE         | NULL/EMPTY | DESCRIPTION                                                       |
|-------|--------------|------------|-------------------------------------------------------------------|
| value | BigDecimal   | yes        | The monetary value of the cashback. Can be null.                  |
| type  | CashbackType | yes        | The type of cashback offered (ABSOLUTE, PERCENTAGE). Can be null. |

## `MinimumPrice`
Represents the minimum price details of a product.

| KEY           | TYPE       | NULL/EMPTY | DESCRIPTION                                              |
|---------------|------------|------------|----------------------------------------------------------|
| originalPrice | BigDecimal | no         | The original price of the product before any discounts.  |
| finalPrice    | BigDecimal | no         | The final price of the product after applying discounts. |

## `UserField`
Represents a user input field with associated validation for a tour or activity.

| KEY        | TYPE                                | NULL/EMPTY | DESCRIPTION                                                     |
|------------|-------------------------------------|------------|-----------------------------------------------------------------|
| oldId      | Int                                 | no         | Legacy identifier for the user field.                           |
| id         | String                              | no         | Unique identifier for the user field in the current system.     |
| name       | String                              | no         | Name of the user field.                                         |
| dataType   | String                              | no         | Data type of the user field (e.g., String, Integer).            |
| validation | [FieldValidation](#FieldValidation) | no         | Validation rules and constraints for the user field.            |
| level      | TourUserFieldLevel                  | no         | Level of the user field (TOUR, PRIMARY_CUSTOMER, ALL_CUSTOMER). |

## `FieldValidation`

Encapsulates validation rules and constraints for a user input field.

| KEY       | TYPE         | NULL/EMPTY | DESCRIPTION                                                                             |
|-----------|--------------|------------|-----------------------------------------------------------------------------------------|
| regex     | String       | yes        | Regular expression pattern that the field value must match. Can be null.                |
| minLength | Int          | yes        | Minimum length of the field value. Can be null.                                         |
| maxLength | Int          | yes        | Maximum length of the field value. Can be null.                                         |
| minValue  | String       | yes        | Minimum value for the field, applicable for numeric fields. Can be null.                |
| maxValue  | String       | yes        | Maximum value for the field, applicable for numeric fields. Can be null.                |
| required  | Boolean      | no         | Indicates whether the field is required.                                                |
| values    | List<String> | yes        | List of permissible values for the field, applicable for enum-type fields. Can be null. |
