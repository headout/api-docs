# Common Models

* [`city`](#city)
* [`currency`](#currency)
* [`image`](#image)
* [`location`](#location)
* [`geo-location`](#geo-location)
* [`address`](#address)
* [`price`](#price)
* [`pagination-wrapper<T>`](#pagination-wrapper)

### `city`

Representation of a city

| KEY   | TYPE                              | NULL/EMPTY | DESCRIPTION                                          |
|-------|-----------------------------------|------------|------------------------------------------------------|
| code  | string                            | no         | Code name for the city. Example: `NEW_YORK`, `DUBAI` |
| name  | string                            | no         | Display name of the city                             |
| image | [`image`](common-models.md#image) | no         | The primary image for the city.                      |

### `currency`

Complete representation of a currency

| KEY         | TYPE   | NULL/EMPTY | DESCRIPTION                                                                                                                            |
|-------------|--------|------------|----------------------------------------------------------------------------------------------------------------------------------------|
| code        | string | no         | ISO 4217 currency codes. Example: `USD`, `AED` *Ref: [https://en.wikipedia.org/wiki/ISO_4217](https://en.wikipedia.org/wiki/ISO_4217)* |
| name        | string | no         | Display name of the currency                                                                                                           |
| symbol      | string | no         | Full symbol representation of the currency. Example: `US$`                                                                             |
| localSymbol | string | no         | Shorthand symbol representation that would be understood by local people in the currency's native country. Example `$`                 |
| precision   | int    | no         | Precision of decimal digits for values in this currency                                                                                |

### `image`

Representation of an image

| KEY | TYPE   | NULL/EMPTY | DESCRIPTION      |
|-----|--------|------------|------------------|
| url | string | no         | Url of the image |

### `location`

Representation of a point on the map with address information.

| KEY     | TYPE                            | NULL/EMPTY | DESCRIPTION                        |
|---------|---------------------------------|------------|------------------------------------|
| geo     | [`geo-location`](#geo-location) | no         | The geo location of the point.     |
| address | [`address`](#address)           | no         | The address representing the point |

### `geo-location`

| KEY       | TYPE  | NULL/EMPTY | DESCRIPTION                |
|-----------|-------|------------|----------------------------|
| latitude  | float | no         | The latitude of the point. |
| longitude | float | no         | The latitude of the point. |

### `address`

Represents an address

| KEY         | TYPE   | NULL/EMPTY | DESCRIPTION           |
|-------------|--------|------------|-----------------------|
| line1       | string | no         | Line 1 of the address |
| line2       | string | yes        | Line 2 of the address |
| cityName    | string | no         | City name             |
| stateName   | string | yes        | State name            |
| countryName | string | no         | Country name          |
| postalCode  | string | yes        | Postal/Zip code       |

### `price`

Represent a price with currency

| KEY          | TYPE   | NULL/EMPTY | DESCRIPTION                                                              |
|--------------|--------|------------|--------------------------------------------------------------------------|
| amount       | float  | no         | The amount of the price                                                  |
| currencyCode | string | no         | The currency of the price ISO 4217 currency codes. Example: `USD`, `AED` |

### `pagination-wrapper`

Wrapper object to support pagination. Is used to wrap the response by all the APIs if the response is a list of results which can be paginated. The API dictates whether it will be using a pagination wrapper or not.

| KEY        | TYPE     | NULL/EMPTY | DESCRIPTION                                                                                                                                            |
|------------|----------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| items      | array[T] | yes        | The response object array whose whole result is being paginated. The object type T is dictated by the api. This can be empty if there were no results. |
| nextUrl    | string   | yes        | The next page url. Empty if this is the last page.                                                                                                     |
| prevUrl    | string   | yes        | The previous page url. Empty if this is the first page.                                                                                                |
| total      | int      | no         | Specifies the total results.                                                                                                                           |
| nextOffset | int      | yes        | Specifies the next offset which can be used to create the next url. This will be empty/`null` if there is the last page.                               |
