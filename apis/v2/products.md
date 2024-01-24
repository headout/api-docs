# Products API

**Resource path param:** `/products`

## 1. <a name="GET - /products"></a>GET `/products`

### Overview
The Partner Products API v2 provides endpoints for accessing the products. This API is designed to facilitate partners in fetching relevant data for different cities and languages.

### Curl

#### Format
```shell
curl --location 'https://www.headout.com/api/public/v2/products?cityCode=<CITY_CODE>&collectionId=<COLLECTION_ID>&campaignName=<CAMPAIGN_NAME>&languageCode=<LANGUAGE_CODE>&currencyCode=<CURRENCY_CODE>&limit=<LIMIT>&offset=<OFFSET>' \
--header 'Headout-Auth: <YOUR_API_KEY>'
```

#### Sample Request
```shell
curl --location 'https://www.headout.com/api/public/v2/products?cityCode=NEW_YORK' \
--header 'Headout-Auth: <YOUR_API_KEY>'
```

### Request

#### API Parameters
| Parameter       | Required / Optional | Description                          | Default Value |
|-----------------|---------------------|--------------------------------------|---------------|
| `cityCode`      | Required            | The city code to fetch products for. |               |
| `collectionId`  | Optional            | Collection ID to filter products.    |               |
| `categoryId`    | Optional            | Category ID to filter products.      |               |
| `subCategoryId` | Optional            | Subcategory ID to filter products.   |               |
| `languageCode`  | Optional            | Language code.                       | `EN`          |
| `currencyCode`  | Optional            | Currency code.                       |               |
| `campaignName`  | Optional            | Campaign name for filtering.         |               |
| `offset`        | Optional            | Offset for pagination.               | `0`           |
| `limit`         | Optional            | Limit for pagination.                | `20`          |

#### API Headers
| Header         | Required / Optional | Description              |
|----------------|---------------------|--------------------------|
| `Headout-Auth` | Required            | The Authorization Token. |


### Response

**Object:** [`Product`](/object-models/v2/Product.md)

<details>
<summary>Response Example</summary>

```json
{
  "products": [
    {
      "id": "19513",
      "name": "Edge Observation Deck Tickets",
      "canonicalUrl": "https://www.headout.com/edge-observation-deck-tickets/tickets-to-edge-observation-deck-e-19513/?affiliate_code=n5cprT&utm_medium=affiliate&utm_source=",
      "city": {
        "code": "NEW_YORK",
        "name": "New York",
        "image": {
          "url": "//cdn-imgix.headout.com/media/images/ee075882083344be170ed38c8c76b4a1-new-york-city-01.jpeg"
        }
      },
      "media": [
        {
          "url": "https://cdn-imgix.headout.com/media/images/7dff2143faf0c49109d1aeca8a7dcd9f-19513-new-york-edge-observation-deck-adimssion-tickets--09.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/13457e49907d62d8240ed934d0c3ee4e-19513-TicketstoEdgeObservationDeck---002.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/649480a68651bab273b313916235160e-19513-TicketstoEdgeObservationDeck---003.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/4ef5529db833ea7a1798d495cee3ccb0-19513-TicketstoEdgeObservationDeck---004.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/cb2d4b053a719b3cf6c74459795258f4-19513-TicketstoEdgeObservationDeck---005.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/4b621678552897b11e5632d62be8160c-19513-new-york-edge-observation-deck-adimssion-tickets--07.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/94dc11b01eb6040267b2d3ac96444d55-19513-new-york-edge-observation-deck-adimssion-tickets--06.jpg",
          "type": "IMAGE"
        }
      ],
      "startLocation": {
        "latitude": 40.75412368774414,
        "longitude": -74.0009765625
      },
      "productType": "ATTRACTION",
      "reviewsSummary": {
        "ratingsCount": 2763,
        "averageRating": 4.03
      },
      "listingPrice": {
        "type": "PER_PERSON",
        "currencyCode": "USD",
        "minimumPrice": {
          "originalPrice": 41.00,
          "finalPrice": 41.00
        },
        "bestDiscount": 0
      },
      "currency": {
        "code": "USD",
        "currencyName": "United States Dollar",
        "symbol": "US$",
        "localSymbol": "$",
        "precision": 2,
        "currency": "USD"
      },
      "localeSpecificUrls": {
        "EN": "/edge-observation-deck-tickets/tickets-to-edge-observation-deck-e-19513/",
        "ES": "/es/edge-nyc/entradas-a-la-plataforma-de-observacion-edge-e-19513/",
        "FR": "/fr/edge-nyc/billets-pour-le-pont-dobservation-edge-e-19513/",
        "IT": "/it/edge-nyc/biglietti-per-il-ponte-di-osservazione-di-edge-30-hudson-yards-e-19513/",
        "DE": "/de/rand-nyc/tickets-fur-die-aussichtsplattform-the-edge-e-19513/",
        "PT": "/pt/borda-nyc/ingressos-para-o-edge-observation-deck-e-19513/",
        "NL": "/nl/rand-nyc/tickets-voor-edge-observation-deck-e-19513/"
      },
      "hasInstantConfirmation": true,
      "hasMobileTicket": true,
      "primaryCategory": {
        "id": "1",
        "name": "Tickets",
        "localeSpecificUrls": {
          "EN": "/tickets-new_york-ca-1~21553/",
          "ES": "/es/entradas-new_york-ca-1~21553/",
          "FR": "/fr/billets-new_york-ca-1~21553/",
          "IT": "/it/biglietti-new_york-ca-1~21553/",
          "DE": "/de/tickets-new_york-ca-1~21553/",
          "PT": "/pt/ingressos-new_york-ca-1~21553/",
          "NL": "/nl/tickets-new_york-ca-1~21553/"
        },
        "canonicalUrl": "https://www.headout.com/tickets-new_york-ca-1~21553/"
      },
      "primarySubCategory": {
        "id": "1007",
        "name": "Landmarks",
        "categoryId": "1",
        "canonicalUrl": "https://www.headout.com/landmarks-new_york-sc-1007~21553/",
        "localeSpecificUrls": {
          "EN": "/landmarks-new_york-sc-1007~21553/",
          "ES": "/es/principales-atracciones-new_york-sc-1007~21553/",
          "FR": "/fr/monuments-new_york-sc-1007~21553/",
          "IT": "/it/punti-di-interesse-new_york-sc-1007~21553/",
          "DE": "/de/wahrzeichen-new_york-sc-1007~21553/",
          "PT": "/pt/marcos-historicos-new_york-sc-1007~21553/",
          "NL": "/nl/bezienswaardigheden-new_york-sc-1007~21553/"
        }
      },
      "primaryCollection": {
        "id": "4012",
        "name": "Edge NYC",
        "cityCode": "NEW_YORK",
        "localeSpecificUrls": {},
        "canonicalUrl": "https://www.headout.com/edge-observation-deck-tickets-c-4012/"
      }
    },
    {
      "id": "593",
      "name": "Empire State Building Observatory Skip-the-Line Tickets",
      "canonicalUrl": "https://www.headout.com/empire-state-building-tickets/empire-state-building-observatory-tickets-e-593/?affiliate_code=n5cprT&utm_medium=affiliate&utm_source=",
      "city": {
        "code": "NEW_YORK",
        "name": "New York",
        "image": {
          "url": "//cdn-imgix.headout.com/media/images/ee075882083344be170ed38c8c76b4a1-new-york-city-01.jpeg"
        }
      },
      "media": [
        {
          "url": "https://cdn-imgix.headout.com/media/images/e783f141025783e733cf2e6f80d745ba-593-new-york-empire-state-building-observatory-tickets-11.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/tour/724/TOUR-IMAGE/9622bde2-0000-408f-b3f2-1d8938367795-593-new-york-empire-state-building-observatory-tickets-06.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/tour/724/TOUR-IMAGE/43205213-a763-4533-a23a-d544b4148b17-593-new-york-empire-state-building-observatory-tickets-09.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/tour/724/TOUR-IMAGE/94b5164c-1ebc-4bf1-aaa1-7df77868daa8-593-new-york-empire-state-building-observatory-tickets-08.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/tour/724/TOUR-IMAGE/5dbcd7d1-108d-42cb-b408-c2619a99f005-593-new-york-empire-state-building-observatory-tickets-07.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/tour/724/TOUR-IMAGE/ee824c63-5a83-4f2f-a122-9abec55543bb-593-new-york-empire-state-building-observatory-tickets-04.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/tour/724/TOUR-IMAGE/68e4067d-1135-497c-99c8-47b1e6d3af64-593-new-york-empire-state-building-observatory-tickets-03.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/tour/724/TOUR-IMAGE/ab7aabf3-994f-4a01-92cf-bf57553e4c53-593-new-york-empire-state-building-observatory-tickets-01.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/tour/724/TOUR-IMAGE/0d5d7d1c-7d6f-4d31-9bc0-14a24ee22f74-593-new-york-empire-state-building-observatory-tickets-02.jpg",
          "type": "IMAGE"
        }
      ],
      "startLocation": {
        "latitude": 40.74843978881836,
        "longitude": -73.98566436767578
      },
      "productType": "ATTRACTION",
      "reviewsSummary": {
        "ratingsCount": 3873,
        "averageRating": 4.31
      },
      "listingPrice": {
        "type": "PER_PERSON",
        "currencyCode": "USD",
        "minimumPrice": {
          "originalPrice": 43.98,
          "finalPrice": 43.98
        },
        "bestDiscount": 0
      },
      "currency": {
        "code": "USD",
        "currencyName": "United States Dollar",
        "symbol": "US$",
        "localSymbol": "$",
        "precision": 2,
        "currency": "USD"
      },
      "localeSpecificUrls": {
        "EN": "/empire-state-building-tickets/empire-state-building-observatory-tickets-e-593/",
        "ES": "/es/entradas-empire-state-building/entradas-al-empire-state-building-e-593/",
        "FR": "/fr/empire-state-building/billets-pour-lobservatoire-de-lempire-state-building-e-593/",
        "IT": "/it/biglietti-empire-state-building/biglietti-regolari-e-salta-la-coda-per-empire-state-building-e-593/",
        "DE": "/de/buchen-sie-empire-state-building-tickets-skip-the-line-zugang/empire-state-building-tickets-fur-die-aussichtsplattform-e-593/",
        "PT": "/pt/ingressos-empire-state-building/ingressos-observatorio-empire-state-building-e-593/",
        "NL": "/nl/boek-tickets-voor-het-empire-state-building-toegang-tot-de-wachtrij/empire-state-building-observatory-skip-the-line-tickets-e-593/"
      },
      "hasInstantConfirmation": true,
      "hasMobileTicket": true,
      "primaryCategory": {
        "id": "1",
        "name": "Tickets",
        "localeSpecificUrls": {
          "EN": "/tickets-new_york-ca-1~21553/",
          "ES": "/es/entradas-new_york-ca-1~21553/",
          "FR": "/fr/billets-new_york-ca-1~21553/",
          "IT": "/it/biglietti-new_york-ca-1~21553/",
          "DE": "/de/tickets-new_york-ca-1~21553/",
          "PT": "/pt/ingressos-new_york-ca-1~21553/",
          "NL": "/nl/tickets-new_york-ca-1~21553/"
        },
        "canonicalUrl": "https://www.headout.com/tickets-new_york-ca-1~21553/"
      },
      "primarySubCategory": {
        "id": "1007",
        "name": "Landmarks",
        "categoryId": "1",
        "canonicalUrl": "https://www.headout.com/landmarks-new_york-sc-1007~21553/",
        "localeSpecificUrls": {
          "EN": "/landmarks-new_york-sc-1007~21553/",
          "ES": "/es/principales-atracciones-new_york-sc-1007~21553/",
          "FR": "/fr/monuments-new_york-sc-1007~21553/",
          "IT": "/it/punti-di-interesse-new_york-sc-1007~21553/",
          "DE": "/de/wahrzeichen-new_york-sc-1007~21553/",
          "PT": "/pt/marcos-historicos-new_york-sc-1007~21553/",
          "NL": "/nl/bezienswaardigheden-new_york-sc-1007~21553/"
        }
      },
      "primaryCollection": {
        "id": "234",
        "name": "Empire State Building",
        "cityCode": "NEW_YORK",
        "localeSpecificUrls": {},
        "canonicalUrl": "https://www.headout.com/empire-state-building-tickets-c-234/"
      }
    },
    {
      "id": "16722",
      "name": "SUMMIT One Vanderbilt Tickets",
      "canonicalUrl": "https://www.headout.com/summit-one-vanderbilt/summit-one-vanderbilt-summit-experience-tickets-e-16722/?affiliate_code=n5cprT&utm_medium=affiliate&utm_source=",
      "city": {
        "code": "NEW_YORK",
        "name": "New York",
        "image": {
          "url": "//cdn-imgix.headout.com/media/images/ee075882083344be170ed38c8c76b4a1-new-york-city-01.jpeg"
        }
      },
      "media": [
        {
          "url": "https://cdn-imgix.headout.com/media/images/d8105cea5ffac3d7b626719b57856d96-16722Vanderbilt-0000s-0018-SUMMITOVAffinityDaytimeFather-DaughterCloseUp.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/e0f42ed5b1c6163fff9afb92b2a2b579-16722Vanderbilt-0000s-0016-SUMMITOneVanderbiltAffinity2.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/ae9ec1e1323fde409b4feea088fad2d6-16722Vanderbilt-0000s-0005-SUMMITOneVanderbiltUnity.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/0d0e3e2c66b6b7f4de9a3f9c5043627b-16722Vanderbilt-0000s-0009-SUMMITOVReflect.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/ea537004c0390a31240213121ae73e2b-16722Vanderbilt-0000s-0006-SUMMITOneVanderbiltAerialCloseUp.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/2cbc6ad100ede58f651bd25212d428d8-16722Vanderbilt-0000s-0003-SUMMITOVApre-sTerraceBar.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/b9e3d346f2089a1b4b738fc504555f46-16722Vanderbilt-0000s-0004-SUMMITOVApre-sCafe-SouthView.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/78f0895523e615963d3c5f297f833359-16722Vanderbilt-0000s-0012-SUMMITOneVanderbiltTranscendenceLounging.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/2868ac656026e65fe63573ff0fadbc52-16722Vanderbilt-0000s-0021-Transcendence-Sunset.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/4dcf25c322347255fe64e5d19bd00ca8-16722Vanderbilt-0000s-0011-SUMMITOneVanderbiltTranscendencePortal.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/97a3d307e00ddfa34ec8bbdca2130c24-16722Vanderbilt-0000s-0013-SUMMITOneVanderbiltTranscendenceatNight.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/15389840d6fd3520417f100458098c27-16722Vanderbilt-0000s-0015-SUMMITOneVanderbiltatNight3.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/9b0e785ceff45ece83c1dcc817f36c4d-16722Vanderbilt-0000s-0000-OneVanderbiltAerialatSunset.jpg",
          "type": "IMAGE"
        },
        {
          "url": "https://cdn-imgix.headout.com/media/images/e4c991ee65e4ef7390082a32b9c4e9d4-16722Vanderbilt-0000s-0010-OneVanderbiltatNight.jpg",
          "type": "IMAGE"
        }
      ],
      "startLocation": {
        "latitude": 40.75276565551758,
        "longitude": -73.97874450683594
      },
      "productType": "TOUR",
      "reviewsSummary": {
        "ratingsCount": 2246,
        "averageRating": 4.45
      },
      "listingPrice": {
        "type": "PER_PERSON",
        "currencyCode": "USD",
        "minimumPrice": {
          "originalPrice": 42.00,
          "finalPrice": 42.00
        },
        "bestDiscount": 0
      },
      "currency": {
        "code": "USD",
        "currencyName": "United States Dollar",
        "symbol": "US$",
        "localSymbol": "$",
        "precision": 2,
        "currency": "USD"
      },
      "localeSpecificUrls": {
        "EN": "/summit-one-vanderbilt/summit-one-vanderbilt-summit-experience-tickets-e-16722/",
        "ES": "/es/entradas-para-summit-one-vanderbilt-nueva-york-headout/entradas-summit-one-vanderbilt-e-16722/",
        "FR": "/fr/billets-pour-le-summit-one-vanderbilt-new-york-headout/billets-pour-le-summit-one-vanderbilt-e-16722/",
        "IT": "/it/biglietti-per-summit-one-vanderbilt-new-york-uscita-di-testa/biglietti-per-summit-one-vanderbilt-e-16722/",
        "DE": "/de/summit-one-vanderbilt-tickets-new-york-headout/summit-one-vanderbilt-tickets-e-16722/",
        "PT": "/pt/ingressos-summit-one-vanderbilt-nova-york-headout/ingressos-para-summit-one-vanderbilt-e-16722/",
        "NL": "/nl/tickets-voor-summit-one-vanderbilt-new-york/tickets-voor-summit-one-vanderbilt-e-16722/"
      },
      "hasInstantConfirmation": true,
      "hasMobileTicket": true,
      "primaryCategory": {
        "id": "1",
        "name": "Tickets",
        "localeSpecificUrls": {
          "EN": "/tickets-new_york-ca-1~21553/",
          "ES": "/es/entradas-new_york-ca-1~21553/",
          "FR": "/fr/billets-new_york-ca-1~21553/",
          "IT": "/it/biglietti-new_york-ca-1~21553/",
          "DE": "/de/tickets-new_york-ca-1~21553/",
          "PT": "/pt/ingressos-new_york-ca-1~21553/",
          "NL": "/nl/tickets-new_york-ca-1~21553/"
        },
        "canonicalUrl": "https://www.headout.com/tickets-new_york-ca-1~21553/"
      },
      "primarySubCategory": {
        "id": "1007",
        "name": "Landmarks",
        "categoryId": "1",
        "canonicalUrl": "https://www.headout.com/landmarks-new_york-sc-1007~21553/",
        "localeSpecificUrls": {
          "EN": "/landmarks-new_york-sc-1007~21553/",
          "ES": "/es/principales-atracciones-new_york-sc-1007~21553/",
          "FR": "/fr/monuments-new_york-sc-1007~21553/",
          "IT": "/it/punti-di-interesse-new_york-sc-1007~21553/",
          "DE": "/de/wahrzeichen-new_york-sc-1007~21553/",
          "PT": "/pt/marcos-historicos-new_york-sc-1007~21553/",
          "NL": "/nl/bezienswaardigheden-new_york-sc-1007~21553/"
        }
      },
      "primaryCollection": {
        "id": "3732",
        "name": "SUMMIT One Vanderbilt",
        "cityCode": "NEW_YORK",
        "localeSpecificUrls": {},
        "canonicalUrl": "https://www.headout.com/summit-one-vanderbilt-c-3732/"
      }
    }
  ],
  "nextUrl": "/api/public/v2/products?cityCode=NEW_YORK&offset=3&limit=3",
  "prevUrl": null,
  "total": 69,
  "nextOffset": 3
}
```

</details>

## Error Handling
Refer to [this](./error-handling.md) document for handling errors in the APIs.

## Notes
- Ensure that all required parameters are included in your requests.
- Use appropriate city and language codes as per your application requirements.
- Pagination parameters (`offset` and `limit`) help in managing large datasets.
