# Object Models

[Product Models](#Product Models)
* [product](#product)
* [product-content](#product-content)

[Common Models](#Common Models)
* [city](#city)
* [currency](#currency)
* [location](#location)
* [geo-location](#geo-location)
* [address](#address)
* [rating-cumulative](#rating-cumulative)

## Product Models

### product

Represents the full product information.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
id | string | no | Product id
name | string | no | Name of the product
neighbourhood | string | no | Neighbourhood of the location of the product
city | [city](#city) | no | City of the product
currency | [currency](#currency) | no | Native currency of the product. This depends on the country of the product.
images | array[[image](#image)] | no | Product images
displayTags | array[string] | yes | Tags signifying the product
content | array[[product-content](#product-content)] | no | Content specifying the details of the product
startLocation | [location](#location) | no | Location of the start point
endLocation | [location](#location) | no | Location of the end point
productType | array[string] | no | Specifies the type of the product.`enum: TOUR, ACTIVITY, EVENT, ATTRACTION, TRANSFER`
ratingCumulative | [rating-cumulative](#rating-cumulative) | no | Cumulative rating of the product
variant | array[[variant]()] | no | Variants of the product. Every product has variants which are the actual bookable entities. If there is only 1 variant, the variant does not have any special significance. If there are more than 1 variant then each variant will have it's own name and description.

### product-content

A content section of the product

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
title | string | no | Title of the content section
html | string | no | The content of the section in html format.

## Common

### city

Representation of a city

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
code | string | no | Code name for the city. Example: `NEW_YORK`, `DUBAI`
name | string | no | Display name of the city

### currency

Complete representation of a currency

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
code | string | no | ISO 4217 currency codes. Example: `USD`, `AED`
name | string | no | Display name of the currency
symbol | string | no | Full symbol representation of the currency. Example: `US$`
localSymbol | string | no | Shorthand symbol representation that would be understood by local people in the currency's native country. Example `$`
precision | int | no | Precision of decimal digits for values in this currency

### image

Representation of an image

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
url | string | no | Url of the image

### location

Representation of a point on the map with address information.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
geo | [geo-location](#geo-location) | no | The geo location of the point.
address | [address](#address) | no | The address representing the point

### geo-location

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
latitude | float | no | The latitude of the point.
longitude | float | no | The latitude of the point.

### address

Represents an address

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
line1 | string | no | Line 1 of the address
line2 | string | yes | Line 2 of the address
cityName | string | no | City name
stateName | string | yes | State name
countryName | string | no | Country name
postalCode | string | yes | Postal/Zip code

### rating-cumulative

Represent the cumulative rating information.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
avg | float | no | The average rating
count | int | no | The overall entries used to evaluate the rating.
