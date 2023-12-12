# Product APIs

**Resource path param:** `/product`

## APIs

| METHOD | URL                                                                           | AUTH | USAGE                            |
|--------|-------------------------------------------------------------------------------|------|----------------------------------|
| GET    | [`/product/get/{product_id}`](#GET-/product/get/{product_id})                 | no   | Get product by `id`.             |
| GET    | [`/product/listing/list-by/city`](#GET-/product/listing/list-by/city)         | no   | List product listing by city     |
| GET    | [`/product/listing/list-by/category`](#GET-/product/listing/list-by/category) | no   | List product listing by category |

### <a name="GET-/product/get/{product_id}"></a>GET `/product/get/{product_id}`

Gets a product by `productId`.

#### Example curl
```shell
curl --location 'https://api.headout.com/api/v1/product/get/3336?currencyCode=EUR&language=PT&fetch-variants=true'
```

#### Request

| MODE  | KEY            | TYPE    | OPTIONAL            | DESCRIPTION                                                                                                                                                           |
|-------|----------------|---------|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| PATH  | productId      | string  | no                  | Product id                                                                                                                                                            |
| QUERY | currencyCode   | string  | yes                 | The currency in which pricing information will be returned. Eg: `USD`, `AED`. *Ref: [https://en.wikipedia.org/wiki/ISO_4217](https://en.wikipedia.org/wiki/ISO_4217)* |
| QUERY | fetch-variants | boolean | yes (Default: true) | Flag to toggle the option of fetching variants.                                                                                                                       |
| QUERY | language       | string  | yes (Default: EN)   | The language in which the product details will be returned. Eg: `EN`, `ES`, `FR`, `IT`, `DE`, `PT`, `NL`, etc.                                                        |

#### Response

**Object:** [`product`](/object-models/product-models.md#product)

<details>
<summary>Response Example</summary>

```json
{
  "id": 512,
  "name": "Wicked",
  "url": "/broadway-tickets/wicked-e-512/",
  "canonicalUrl": "https://www.headout.com/broadway-tickets/wicked-e-512/",
  "neighbourhood": "",
  "city": {
    "name": "New York",
    "code": "NEW_YORK"
  },
  "currency": {
    "code": "USD",
    "name": "United States Dollar",
    "symbol": "US$",
    "localSymbol": "$",
    "precision": 2
  },
  "displayTags": [
    "Broadway",
    "Musical",
    "Best of Broadway",
    "Entertainment"
  ],
  "images": [
    {
      "url": "https://cdn-imgix.headout.com/media/images/5276fb91a066165e4069516143ae2ea3-512-new-york-wicked-01.jpg",
      "altText": "wicked-1",
      "description": "Wicked Newyork",
      "credit": "Broadway Inbound, Inc"
    }
  ],
  "contentListHtml": [
    {
      "title": "Summary",
      "type": "SUMMARY_HTML",
      "html": "<h2>Why Watch Wicked</h2>\n<p>Dive deep into the enchanting world of Oz, presented from a perspective you've never witnessed before. Secure your Wicked Broadway tickets to step into a multi-award-winning phenomenon. With its spellbinding cast, extraordinary crew, and accolades that stretch beyond Broadway's glimmering lights, Wicked is an unmatched theatrical experience. The numerous awards and consistent critical acclaim stand testimony to its brilliance. Don't miss your chance to be swept away by this bewitching tale of friendship, love, and the cost of integrity.</p>\n<h2>The Story</h2>\n<p>Before Dorothy and her famous ruby slippers, there was a profound friendship between two young women, one with emerald green skin. This is their story. Book your Wicked Broadway tickets now and embark on a magical journey that unveils the untold tale of the witches of Oz. Witness the transformation of Elphaba, the future Wicked Witch of the West, and Glinda, the Good Witch. It's a mesmerizing, heart-tugging story filled with songs and emotions that promise to leave an indelible mark on your soul.</p>\n<h2>Great For</h2>\n<p>Fans of Fantasy | Musical Enthusiasts | Night Out with Family</p>"
    }
  ],
  "content": [
    {
      "title": "Summary",
      "type": "SUMMARY_HTML",
      "html": "<h2>Why Watch Wicked</h2>\n<p>Dive deep into the enchanting world of Oz, presented from a perspective you've never witnessed before. Secure your Wicked Broadway tickets to step into a multi-award-winning phenomenon. With its spellbinding cast, extraordinary crew, and accolades that stretch beyond Broadway's glimmering lights, Wicked is an unmatched theatrical experience. The numerous awards and consistent critical acclaim stand testimony to its brilliance. Don't miss your chance to be swept away by this bewitching tale of friendship, love, and the cost of integrity.</p>\n<h2>The Story</h2>\n<p>Before Dorothy and her famous ruby slippers, there was a profound friendship between two young women, one with emerald green skin. This is their story. Book your Wicked Broadway tickets now and embark on a magical journey that unveils the untold tale of the witches of Oz. Witness the transformation of Elphaba, the future Wicked Witch of the West, and Glinda, the Good Witch. It's a mesmerizing, heart-tugging story filled with songs and emotions that promise to leave an indelible mark on your soul.</p>\n<h2>Great For</h2>\n<p>Fans of Fantasy | Musical Enthusiasts | Night Out with Family</p>"
    }
  ],
  "startLocation": {
    "geolocation": {
      "latitude": 40.762332916259766,
      "longitude": -73.98523712158203
    },
    "address": {
      "addressLine1": "Gershwin Theatre",
      "addressLine2": "222 West 51 Street",
      "cityName": "New York",
      "postalCode": "10019",
      "state": "New York",
      "countryName": "United States"
    }
  },
  "endLocation": {
    "geolocation": {
      "latitude": 40.762332916259766,
      "longitude": -73.98523712158203
    },
    "address": {
      "addressLine1": "Gershwin Theatre",
      "addressLine2": "222 West 51 Street",
      "cityName": "New York",
      "postalCode": "10019",
      "state": "New York",
      "countryName": "United States"
    }
  },
  "productType": "EVENT",
  "ratingCumulative": {
    "avg": 4.43,
    "count": 1262
  },
  "hasInstantConfirmation": false,
  "hasMobileTicket": false,
  "variants": [
    {
      "id": 647,
      "name": "Rear Orchestra/Rear Mezzanine",
      "description": "",
      "duration": 9900000,
      "inventoryType": "FIXED_START_FIXED_DURATION",
      "pax": {
        "min": 1,
        "max": 8
      },
      "cashback": {
        "value": 0.0000,
        "type": "PERCENTAGE"
      },
      "ticketDeliveryInfoHtml": null,
      "inputFields": [
        {
          "oldId": 62,
          "id": "NAME",
          "name": "Full Name",
          "dataType": "STRING",
          "validation": {
            "regex": "\\s*[^\\s]+\\s+[^\\s]+.*",
            "minLength": 3,
            "maxLength": 80,
            "minValue": null,
            "maxValue": null,
            "required": true,
            "values": null
          },
          "level": "PRIMARY_CUSTOMER"
        }
      ],
      "tags": [
        "BROADWAY",
        "BROADWAY2",
        "BROADWAYFORKIDS",
        "BROADWAYFORKIDS2",
        "BTTFA"
      ]
    }
  ],
  "pricing": {
    "type": "PER_PERSON",
    "currencyCode": "USD",
    "minimumPrice": {
      "originalPrice": 96.50,
      "finalPrice": 96.50
    },
    "bestDiscount": 0
  }
}
```
</details>

### <a name="GET-/product/listing/list-by/city"></a>GET `/product/listing/list-by/city`

List product listing using city.

#### Example curl
```shell
curl --location 'https://api.headout.com/api/v1/product/listing/list-by/city?cityCode=LONDON&currencyCode=CAD&language=FR&limit=10&offset=10'
```

#### Request

| MODE  | KEY          | TYPE   | OPTIONAL          | DESCRIPTION                                                                                                                                                           |
|-------|--------------|--------|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| QUERY | cityCode     | string | no                | The city code. Eg: `NEW_YORK`, `DUBAI`                                                                                                                                |
| QUERY | currencyCode | string | yes               | The currency in which pricing information will be returned. Eg: `USD`, `AED`. *Ref: [https://en.wikipedia.org/wiki/ISO_4217](https://en.wikipedia.org/wiki/ISO_4217)* |
| QUERY | language     | string | yes (Default: EN) | The language in which the product details will be returned. Eg: `EN`, `ES`, `FR`, `IT`, `DE`, `PT`, `NL`                                                              |
| QUERY | offset       | string | yes               | The offset for pagination. *Ref: [Pagination - Request Params](/conventions/basics.md#Pagination--Request-Params)*                                                    |
| QUERY | limit        | int    | yes               | The limit for pagination. *Ref: [Pagination - Request Params](/conventions/basics.md#Pagination--Request-Params)*                                                     |

#### Response

**Object:** [`pagination-wrapper`](/object-models/common-models.md#pagination-wrapper)`<`[`product-listing`](/object-models/product-models.md#product-listing)`>`

<details>
<summary>Response Example</summary>

```json
{
  "items": [
    {
      "id": "2844",
      "name": "Fast Track Tickets to the London Eye",
      "url": "/london-eye-tickets/fast-track-tickets-to-the-london-eye-e-2844/",
      "canonicalUrl": "https://www.headout.com/london-eye-tickets/fast-track-tickets-to-the-london-eye-e-2844/",
      "city": {
        "name": "London",
        "code": "LONDON"
      },
      "image": {
        "url": "https://cdn-imgix.headout.com/tour/4407/TOUR-IMAGE/12d3a2c5-a39e-4f0f-9724-dcd63f5429cb-2844-london-london-eye--fast-track-entry-tickets-04.jpg"
      },
      "neighbourhood": null,
      "primaryCategory": {
        "id": 279,
        "name": "London Eye Tickets",
        "cityCode": "LONDON",
        "url": "/category/279"
      },
      "currency": {
        "code": "USD",
        "currencyName": "United States Dollar",
        "symbol": "US$",
        "localSymbol": "$",
        "precision": 2,
        "currency": "USD"
      },
      "startGeolocation": {
        "latitude": 51.50345230102539,
        "longitude": -0.119518555700779
      },
      "ratingCumulative": {
        "avg": 4.47,
        "count": 3398
      },
      "pricing": {
        "type": "PER_PERSON",
        "currencyCode": "USD",
        "minimumPrice": {
          "originalPrice": 58.4,
          "finalPrice": 58.4
        },
        "bestDiscount": 0
      },
      "hasInstantConfirmation": true
    }
  ],
  "nextUrl": "https://api.headout.com/api/v1/product/listing/list-by/city?cityCode=LONDON&currencyCode=USD&language=EN&offset=11&limit=1",
  "prevUrl": "https://api.headout.com/api/v1/product/listing/list-by/city?cityCode=LONDON&currencyCode=USD&language=EN&offset=9&limit=1",
  "total": 224,
  "nextOffset": 11
}
```
</details>

### <a name="GET-/product/listing/list-by/category"></a>GET `/product/listing/list-by/category`

List product listing using category.

#### Example curl
```shell
curl --location 'https://api.headout.com/api/v1/product/listing/list-by/category?categoryId=3956&language=ES&currencyCode=EUR&limit=20&offset=10'
```

#### Request

| MODE  | KEY          | TYPE   | OPTIONAL          | DESCRIPTION                                                                                                                                                           |
|-------|--------------|--------|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| QUERY | categoryId   | string | no                | The id of the category.                                                                                                                                               |
| QUERY | language     | string | yes (Default: EN) | The language in which the product details will be returned. Eg: `EN`, `ES`, `FR`, `IT`, `DE`, `PT`, `NL`                                                              |
| QUERY | currencyCode | string | yes               | The currency in which pricing information will be returned. Eg: `USD`, `AED`. *Ref: [https://en.wikipedia.org/wiki/ISO_4217](https://en.wikipedia.org/wiki/ISO_4217)* |
| QUERY | limit        | int    | yes               | The limit for pagination. *Ref: [Pagination - Request Params](/conventions/basics.md#Pagination--Request-Params)*                                                     |
| QUERY | offset       | string | yes               | The offset for pagination. *Ref: [Pagination - Request Params](/conventions/basics.md#Pagination--Request-Params)*                                                    |

#### Response

**Object:** [`pagination-wrapper`](/object-models/common-models.md#pagination-wrapper)`<`[`product-listing`](/object-models/product-models.md#product-listing)`>`

<details>
<summary>Response Example</summary>
```json
{
  "items": [
    {
      "id": "11228",
      "name": "Tickets to Khao Kheow Open Zoo",
      "url": "/es/khao-kheow-open-zoo/khao-kheow-open-zoo-e-11228/",
      "canonicalUrl": "https://www.headout.com/es/khao-kheow-open-zoo/khao-kheow-open-zoo-e-11228/",
      "city": {
        "name": "Pattaya",
        "code": "PATTAYA"
      },
      "image": {
        "url": "https://cdn-imgix.headout.com/tour/21259/TOUR-IMAGE/4dd55cf1-4beb-45ad-aa50-7d6b8b58ca39-11228-pattaya-khao-kheow-open-zoo-01.jpg"
      },
      "neighbourhood": null,
      "primaryCategory": {
        "id": 4842,
        "name": "Khao Kheow Open Zoo",
        "cityCode": "PATTAYA",
        "url": "/category/4842"
      },
      "currency": {
        "code": "EUR",
        "currencyName": "Euro",
        "symbol": "EUR",
        "localSymbol": "€",
        "precision": 2,
        "currency": "EUR"
      },
      "startGeolocation": {
        "latitude": 13.214982986450195,
        "longitude": 101.05597686767578
      },
      "ratingCumulative": {
        "avg": 4.44,
        "count": 2023
      },
      "pricing": {
        "type": "PER_PERSON",
        "currencyCode": "EUR",
        "minimumPrice": {
          "originalPrice": 6.51,
          "finalPrice": 5.73
        },
        "bestDiscount": 12
      },
      "hasInstantConfirmation": true
    }
  ],
  "nextUrl": "https://api.headout.com/api/v1/product/listing/list-by/category?categoryId=3956&language=ES&currencyCode=EUR&offset=11&limit=1",
  "prevUrl": "https://api.headout.com/api/v1/product/listing/list-by/category?categoryId=3956&language=ES&currencyCode=EUR&offset=9&limit=1",
  "total": 25,
  "nextOffset": 11
}
```
</details>