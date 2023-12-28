Based on the provided class structure for `Product` and its related classes, here's a similar object model document:

### `Product`

Represents the detailed information of a partner product.

| KEY                    | TYPE                                                     | NULL/EMPTY | DESCRIPTION                                                                     |
|------------------------|----------------------------------------------------------|------------|---------------------------------------------------------------------------------|
| id                     | String                                                   | no         | Unique identifier for the product.                                              |
| name                   | String                                                   | no         | Name of the product.                                                            |
| url                    | String                                                   | no         | URL of the product.                                                             |
| canonicalUrl           | String                                                   | no         | Canonical URL of the product.                                                   |
| city                   | [`ProductCity`](#amproductcity)                          | no         | City details where the product is located.                                      |
| images                 | List<[`Media`](#ampartnermedia)>                         | no         | List of media items (images) associated with the product.                       |
| experienceVideo        | [`Media`](#ampartnermedia)?                              | yes        | Optional media item (video) showcasing the product experience.                  |
| startLocation          | [`Geolocation`](#geolocation)                            | no         | Geographical coordinates of the starting location of the product.               |
| tourType               | [`TourType`](#tourtype)                                  | no         | Type of tour, categorized by specific types such as TOUR, ACTIVITY, EVENT, etc. |
| reviewsDetails         | [`ProductReviewDetails`](#ampartnerproductreviewdetails) | no         | Review statistics including count and average rating.                           |
| listingPrice           | [`ListingPrice`](#amlistingprice)?                       | yes        | Optional pricing details of the product.                                        |
| currency               | [`TourGroupCurrency`](#amtourgroupcurrency)              | no         | Currency details used for the product.                                          |
| language               | Language                                                 | no         | Language in which the product information is presented.                         |
| urlSlugs               | Map<Language, String>?                                   | yes        | Optional mapping of languages to their respective URL slugs for the product.    |
| hidden                 | Boolean                                                  | no         | Indicates whether the product is hidden or not.                                 |
| hasInstantConfirmation | Boolean                                                  | no         | `true` if the product has instant booking confirmation.                         |
| primaryCategory        | [`Category`](#ampartnercategoryv2)?                      | yes        | Optional primary category of the product.                                       |
| primarySubCategory     | [`SubCategory`](#ampartnersubcategory)?                  | yes        | Optional primary subcategory of the product.                                    |
| primaryCollection      | [`Collection`](#ampartnercollection)?                    | yes        | Optional primary collection associated with the product.                        |

### `ProductCity`

Represents city details.

| KEY  | TYPE   | NULL/EMPTY | DESCRIPTION                 |
|------|--------|------------|-----------------------------|
| name | String | no         | Name of the city.           |
| code | String | no         | Code representing the city. |

### `Media`

Media details, including URL and type.

| KEY  | TYPE      | NULL/EMPTY | DESCRIPTION                         |
|------|-----------|------------|-------------------------------------|
| url  | String    | no         | URL of the media item.              |
| type | MediaType | no         | Type of the media (IMAGE or VIDEO). |

### `Geolocation`

Geographical location data.

| KEY       | TYPE   | NULL/EMPTY | DESCRIPTION           |
|-----------|--------|------------|-----------------------|
| latitude  | Double | no         | Latitude coordinate.  |
| longitude | Double | no         | Longitude coordinate. |

### `TourType`

Enum representing different types of tours.

### `ProductReviewDetails`

Review details of the product.

| KEY           | TYPE       | NULL/EMPTY | DESCRIPTION           |
|---------------|------------|------------|-----------------------|
| ratingsCount  | Int        | no         | Count of ratings.     |
| averageRating | BigDecimal | no         | Average rating value. |

### `ListingPrice`

Pricing details.

| KEY          | TYPE             | NULL/EMPTY | DESCRIPTION                |
|--------------|------------------|------------|----------------------------|
| type         | PriceProfileType | no         | Type of pricing profile.   |
| currencyCode | Currency         | no         | Currency code for pricing. |
| minimumPrice | MinimumPrice     | no         | Minimum price details.     |
| bestDiscount | Int              | no         | Best available discount.   |

### `TourGroupCurrency`

Currency details.

| KEY          | TYPE    | NULL/EMPTY | DESCRIPTION                   |
|--------------|---------|------------|-------------------------------|
| code         | String  | no         | Currency code.                |
| currencyName | String  | no         | Name of the currency.         |
| symbol       | String  | no         | Symbol of the currency.       |
| localSymbol  | String  | no         | Local symbol of the currency. |
| precision    | Integer | no         | Precision of the currency.    |

### `Category`

Category details of the product.

| KEY          | TYPE                  | NULL/EMPTY | DESCRIPTION                             |
|--------------|-----------------------|------------|-----------------------------------------|
| id           | String                | no         | Category identifier.                    |
| name         | String                | no         | Name of the category.                   |
| urlSlugs     | Map<Language, String> | no         | URL slugs for different languages.      |
| canonicalUrl | String?               | yes        | Optional canonical URL of the category. |

### `SubCategory`

Subcategory details.

| KEY          | TYPE    | NULL/EMPTY | DESCRIPTION                                |
|--------------|---------|------------|--------------------------------------------|
| id           | String  | no         | Subcategory identifier.                    |
| name         | String  | no         | Name of the subcategory.                   |
| categoryId   | String  | no         | Identifier of the parent category.         |
| canonicalUrl | String? | yes        | Optional canonical URL of the subcategory. |
| urlSlugs     | Map<    |            |                                            |