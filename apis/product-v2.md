# Partner Product API v2

## Overview
The Partner Product API v2 provides endpoints for accessing collections, categories, subcategories, and Products. This API is designed to facilitate partners in fetching relevant data for different cities and languages.

## Endpoints

### 1. Fetch Collections
**GET** `/api/partners/v2/collections`

#### Parameters:
- `cityCode` (required): The city code to fetch collections for.
- `languageCode` (optional, default `EN`): Language code.
- `offset` (optional, default `0`): Offset for pagination.
- `limit` (optional, default `10`): Limit for pagination.

#### Headers:
- `Headout-Auth` (required): The Authorization Token.

<details>
<summary>Response Example</summary>

```json
{
    "city": "NEW_YORK",
    "collections": [
        {
            "id": "24",
            "name": "Broadway",
            "city": "NEW_YORK",
            "urlSlugs": {
                "EN": "/broadway-tickets-c-24/",
                "ES": "/es/entradas-espectaculos-de-broadway-c-24/",
                "FR": "/fr/billets-comedie-musicale-broadway-c-24/",
                "IT": "/it/broadway-biglietti-c-24/",
                "DE": "/de/broadway-tickets-c-24/",
                "PT": "/pt/broadway-c-24/",
                "NL": "/nl/broadway-c-24/"
            },
            "canonicalUrl": "https://www.headout.com/broadway-tickets-c-24/"
        },
        {
            "id": "3546",
            "name": "Cruceros por el río Hudson",
            "city": "NEW_YORK",
            "urlSlugs": {
                "EN": "/hudson-river-cruises-c-3546/",
                "ES": "/es/cruceros-por-el-rio-hudson-c-3546/",
                "FR": "/fr/croisieres-sur-la-riviere-hudson-c-3546/",
                "IT": "/it/crociere-hudson-rive-c-3546/",
                "DE": "/de/hudson-rive-kreuzfahrten-c-3546/",
                "PT": "/pt/cruzeiros-em-hudson-rive-c-3546/",
                "NL": "/nl/hudson-rive-cruises-c-3546/"
            },
            "canonicalUrl": "https://www.headout.com/hudson-river-cruises-c-3546/"
        },
        {
            "id": "234",
            "name": "Edificio Empire State",
            "city": "NEW_YORK",
            "urlSlugs": {
                "EN": "/empire-state-building-tickets-c-234/",
                "ES": "/es/entradas-empire-state-building-c-234/",
                "FR": "/fr/empire-state-building-c-234/",
                "IT": "/it/biglietti-empire-state-building-c-234/",
                "DE": "/de/buchen-sie-empire-state-building-tickets-skip-the-line-zugang-c-234/",
                "PT": "/pt/ingressos-empire-state-building-c-234/",
                "NL": "/nl/boek-tickets-voor-het-empire-state-building-toegang-tot-de-wachtrij-c-234/"
            },
            "canonicalUrl": "https://www.headout.com/empire-state-building-tickets-c-234/"
        }
    ],
    "nextUrl": "https://api.headout.com/api/partners/v2/collections?cityCode=NEW_YORK&campaignName=SOME_CAMPAIGN&languageCode=ES&currencyCode=INR&offset=3&limit=3",
    "prevUrl": null,
    "total": 39,
    "nextOffset": 3
}
```

</details>

---

### 2. Fetch Categories
**GET** `/api/partners/v2/categories`

#### Parameters:
- `cityCode` (required): The city code to fetch categories for.
- `languageCode` (optional, default `EN`): Language code.

#### Headers:
- `Headout-Auth` (required): The Authorization Token.

<details>
<summary>Response Example</summary>

```json
{
    "categories": [
        {
            "id": "1",
            "name": "Tickets",
            "urlSlugs": {
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
        {
            "id": "2",
            "name": "Tours",
            "urlSlugs": {
                "EN": "/tours-new_york-ca-2~21553/",
                "ES": "/es/tours-new_york-ca-2~21553/",
                "FR": "/fr/visites-new_york-ca-2~21553/",
                "IT": "/it/tour-new_york-ca-2~21553/",
                "DE": "/de/touren-new_york-ca-2~21553/",
                "PT": "/pt/tours-new_york-ca-2~21553/",
                "NL": "/nl/tours-new_york-ca-2~21553/"
            },
            "canonicalUrl": "https://www.headout.com/tours-new_york-ca-2~21553/"
        },
        {
            "id": "7",
            "name": "Entertainment",
            "urlSlugs": {
                "EN": "/entertainment-new_york-ca-7~21553/",
                "ES": "/es/entretenimiento-new_york-ca-7~21553/",
                "FR": "/fr/loisirs-new_york-ca-7~21553/",
                "IT": "/it/intrattenimento-new_york-ca-7~21553/",
                "DE": "/de/unterhaltung-new_york-ca-7~21553/",
                "PT": "/pt/entretenimento-new_york-ca-7~21553/",
                "NL": "/nl/entertainment-new_york-ca-7~21553/"
            },
            "canonicalUrl": "https://www.headout.com/entertainment-new_york-ca-7~21553/"
        }
    ],
    "language": "ES",
    "city": "NEW_YORK"
}
```

</details>

---

### 3. Fetch Subcategories
**GET** `/api/partners/v2/subcategories`

#### Parameters:
- `cityCode` (required): The city code to fetch subcategories for.
- `languageCode` (optional, default `EN`): Language code.

#### Headers:
- `Headout-Auth` (required): The Authorization Token.

<details>
<summary>Response Example</summary>

```json
{
    "subCategories": [
        {
            "id": "1001",
            "name": "Theme Parks",
            "categoryId": "1",
            "canonicalUrl": "https://www.headout.com/theme-parks-new_york-sc-1001~21553/",
            "urlSlugs": {
                "EN": "/theme-parks-new_york-sc-1001~21553/",
                "ES": "/es/parques-tematicos-new_york-sc-1001~21553/",
                "FR": "/fr/parcs-a-theme-new_york-sc-1001~21553/",
                "IT": "/it/parchi-a-tema-new_york-sc-1001~21553/",
                "DE": "/de/freizeitparks-new_york-sc-1001~21553/",
                "PT": "/pt/parques-tematicos-new_york-sc-1001~21553/",
                "NL": "/nl/themaparken-new_york-sc-1001~21553/"
            }
        },
        {
            "id": "1002",
            "name": "Museums",
            "categoryId": "1",
            "canonicalUrl": "https://www.headout.com/museums-new_york-sc-1002~21553/",
            "urlSlugs": {
                "EN": "/museums-new_york-sc-1002~21553/",
                "ES": "/es/museos-new_york-sc-1002~21553/",
                "FR": "/fr/musees-new_york-sc-1002~21553/",
                "IT": "/it/musei-new_york-sc-1002~21553/",
                "DE": "/de/museen-new_york-sc-1002~21553/",
                "PT": "/pt/museus-new_york-sc-1002~21553/",
                "NL": "/nl/musea-new_york-sc-1002~21553/"
            }
        },
        {
            "id": "1003",
            "name": "Zoos",
            "categoryId": "1",
            "canonicalUrl": "https://www.headout.com/zoos-new_york-sc-1003~21553/",
            "urlSlugs": {
                "EN": "/zoos-new_york-sc-1003~21553/",
                "ES": "/es/zoo-y-acuarios-new_york-sc-1003~21553/",
                "FR": "/fr/zoos-new_york-sc-1003~21553/",
                "IT": "/it/zoo-e-acquari-new_york-sc-1003~21553/",
                "DE": "/de/zoos-und-aquarien-new_york-sc-1003~21553/",
                "PT": "/pt/zoos-e-aquarios-new_york-sc-1003~21553/",
                "NL": "/nl/dierentuinen-en-aquariums-new_york-sc-1003~21553/"
            }
        }
    ],
    "language": "ES",
    "city": "NEW_YORK"
}
```

</details>

---

### 4. Fetch Products
**GET** `/api/partners/v2/products`

#### Parameters:
- `cityCode` (required): The city code to fetch products for.
- `collectionId` (optional): Collection ID to filter products.
- `categoryId` (optional): Category ID to filter products.
- `subCategoryId` (optional): Subcategory ID to filter products.
- `languageCode` (optional, default `EN`): Language code.
- `currencyCode` (optional): Currency code.
- `campaignName` (optional): Campaign name for filtering.
- `offset` (optional, default `0`): Offset for pagination.
- `limit` (optional, default `20`): Limit for pagination.

#### Headers:
- `Headout-Auth` (required): The Authorization Token.

<details>
<summary>Response Example</summary>

```json
{
    "city": "NEW_YORK",
    "products": [
        {
            "id": "24664",
            "name": "City Climb Skyscraping Experience Tickets",
            "url": "/es/edge-nyc/city-climb-experience-e-24664/",
            "canonicalUrl": "https://www.headout.com/es/edge-nyc/city-climb-experience-e-24664/?utm_campaign=SOME_CAMPAIGN&affiliate_code=n5cprT&utm_medium=affiliate&utm_source=",
            "city": {
                "name": "New York",
                "code": "NEW_YORK"
            },
            "images": [
                {
                    "url": "https://cdn-imgix.headout.com/media/images/8c48afce4d6daf505afcb02632dd2d4b-19513-new-york-edge-observation-deck-adimssion-tickets--05.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/ecf60d7cf9ad489b49905cbc6c4985ec-19513-new-york-edge-observation-deck-adimssion-tickets--01.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/1d9836d6c7777ba6e2fbfc531b43c0e1-19513-new-york-edge-observation-deck-adimssion-tickets--02.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/31913c1479c7c9b2efbe40a719eafd64-19513-new-york-edge-observation-deck-adimssion-tickets--03.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/3075e826691d43154d433bb429684f69-2.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/983a66d0f6ad1d715d9dd92eba106519-3.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/28093c5fe0dc132da6e91b12cea9417a-1.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/4b621678552897b11e5632d62be8160c-19513-new-york-edge-observation-deck-adimssion-tickets--07.jpg",
                    "type": "IMAGE"
                }
            ],
            "experienceVideo": null,
            "startLocation": {
                "latitude": 40.75412368774414,
                "longitude": -74.0009765625
            },
            "tourType": "ACTIVITY",
            "reviewsDetails": {
                "ratingsCount": 6,
                "averageRating": 5.00
            },
            "listingPrice": {
                "type": "PER_PERSON",
                "currencyCode": "INR",
                "minimumPrice": {
                    "originalPrice": 16785,
                    "finalPrice": 16785
                },
                "bestDiscount": 0
            },
            "currency": {
                "code": "INR",
                "currencyName": "Indian Rupee",
                "symbol": "INR",
                "localSymbol": "₹",
                "precision": 0,
                "currency": "INR"
            },
            "language": "EN",
            "urlSlugs": {
                "EN": "/edge-observation-deck-tickets/tickets-to-city-climb-skyscraping-experience-e-24664/",
                "ES": "/es/edge-nyc/city-climb-experience-e-24664/",
                "FR": "/fr/edge-nyc/city-climb-experience-e-24664/",
                "IT": "/it/edge-nyc/city-climb-experience-e-24664/",
                "DE": "/de/rand-nyc/city-climb-experience-e-24664/",
                "PT": "/pt/borda-nyc/city-climb-experience-e-24664/",
                "NL": "/nl/rand-nyc/city-climb-experience-e-24664/"
            },
            "hidden": false,
            "hasInstantConfirmation": true,
            "primaryCategory": {
                "id": "1",
                "name": "Tickets",
                "urlSlugs": {
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
                "id": "1098",
                "name": "Observation Decks",
                "categoryId": "1",
                "canonicalUrl": "https://www.headout.com/observation-decks-new_york-sc-1098~21553/",
                "urlSlugs": {
                    "EN": "/observation-decks-new_york-sc-1098~21553/",
                    "ES": "/es/plataformas-de-observacion-new_york-sc-1098~21553/",
                    "FR": "/fr/ponts-dobservation-new_york-sc-1098~21553/",
                    "IT": "/it/ponti-di-osservazione-new_york-sc-1098~21553/",
                    "DE": "/de/aussichtsplattformen-new_york-sc-1098~21553/",
                    "PT": "/pt/mirantes-new_york-sc-1098~21553/",
                    "NL": "/nl/observatiedekken-new_york-sc-1098~21553/"
                }
            },
            "primaryCollection": {
                "id": "4012",
                "name": "Edge NYC",
                "city": "NEW_YORK",
                "urlSlugs": {},
                "canonicalUrl": "https://www.headout.com/edge-observation-deck-tickets-c-4012/"
            }
        },
        {
            "id": "24671",
            "name": "Harmony: A New Musical -",
            "url": "/es/entradas-espectaculos-de-broadway/harmony-a-new-musical-e-24671/",
            "canonicalUrl": "https://www.headout.com/es/entradas-espectaculos-de-broadway/harmony-a-new-musical-e-24671/?utm_campaign=SOME_CAMPAIGN&affiliate_code=n5cprT&utm_medium=affiliate&utm_source=",
            "city": {
                "name": "New York",
                "code": "NEW_YORK"
            },
            "images": [
                {
                    "url": "https://cdn-imgix.headout.com/media/images/0af0a0b0de9f3dfabdb2fcab5e7e7b30-24671-new-york-harmony-a-new-musical-01.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/53b26b80284d68b2a0dee3350a98be32-24671-new-york-harmony-a-new-musical-02.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/7ba7ceba127ea596af62e1b3a457ea6a-24671-new-york-harmony-a-new-musical-03.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/27d8c4a8e3d949da91aa7c3c275d298b-24671-new-york-harmony-a-new-musical-04.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/313be5d8818d77066ec53556a6a89542-24671-new-york-harmony-a-new-musical-05.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/a103dd77fb108604b32bab667d32201b-24671-new-york-harmony-a-new-musical-06.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/22132605ed1d6cdb30e0fdd8f19eb4b2-24671-new-york-harmony-a-new-musical-07.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/d4f2d9bb801223bfd5f416bc41cf3a4d-24671-new-york-harmony-a-new-musical-08.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/d08f11713fc8bcb4d922ef85e147b7b3-24671-new-york-harmony-a-new-musical-09.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/4794eb14635fe1de93dbea9d5aa22450-24671-new-york-harmony-a-new-musical-10.jpg",
                    "type": "IMAGE"
                }
            ],
            "experienceVideo": null,
            "startLocation": {
                "latitude": 40.760009765625,
                "longitude": -73.98624420166016
            },
            "tourType": "EVENT",
            "reviewsDetails": {
                "ratingsCount": 0,
                "averageRating": 0
            },
            "listingPrice": {
                "type": "PER_PERSON",
                "currencyCode": "INR",
                "minimumPrice": {
                    "originalPrice": 4458,
                    "finalPrice": 4458
                },
                "bestDiscount": 0
            },
            "currency": {
                "code": "INR",
                "currencyName": "Indian Rupee",
                "symbol": "INR",
                "localSymbol": "₹",
                "precision": 0,
                "currency": "INR"
            },
            "language": "ES",
            "urlSlugs": {
                "EN": "/broadway-tickets/harmony-a-new-musical-e-24671/",
                "ES": "/es/entradas-espectaculos-de-broadway/harmony-a-new-musical-e-24671/",
                "FR": "/fr/billets-comedie-musicale-broadway/harmony-la-nouvelle-comedie-musicale-e-24671/",
                "IT": "/it/broadway-biglietti/harmony-a-new-musical-e-24671/",
                "DE": "/de/broadway-tickets/harmony-a-new-musical-e-24671/",
                "PT": "/pt/broadway/harmony-a-new-musical-e-24671/",
                "NL": "/nl/broadway/harmony-a-new-musical-e-24671/"
            },
            "hidden": false,
            "hasInstantConfirmation": true,
            "primaryCategory": {
                "id": "7",
                "name": "Entertainment",
                "urlSlugs": {
                    "EN": "/entertainment-new_york-ca-7~21553/",
                    "ES": "/es/entretenimiento-new_york-ca-7~21553/",
                    "FR": "/fr/loisirs-new_york-ca-7~21553/",
                    "IT": "/it/intrattenimento-new_york-ca-7~21553/",
                    "DE": "/de/unterhaltung-new_york-ca-7~21553/",
                    "PT": "/pt/entretenimento-new_york-ca-7~21553/",
                    "NL": "/nl/entertainment-new_york-ca-7~21553/"
                },
                "canonicalUrl": "https://www.headout.com/entertainment-new_york-ca-7~21553/"
            },
            "primarySubCategory": {
                "id": "1036",
                "name": "Musicals",
                "categoryId": "7",
                "canonicalUrl": "https://www.headout.com/musicals-new_york-sc-1036~21553/",
                "urlSlugs": {
                    "EN": "/musicals-new_york-sc-1036~21553/",
                    "ES": "/es/musicales-new_york-sc-1036~21553/",
                    "FR": "/fr/comedies-musicales-new_york-sc-1036~21553/",
                    "IT": "/it/musical-new_york-sc-1036~21553/",
                    "DE": "/de/musicals-new_york-sc-1036~21553/",
                    "PT": "/pt/musicais-new_york-sc-1036~21553/",
                    "NL": "/nl/musicals-new_york-sc-1036~21553/"
                }
            },
            "primaryCollection": {
                "id": "24",
                "name": "Broadway",
                "city": "NEW_YORK",
                "urlSlugs": {},
                "canonicalUrl": "https://www.headout.com/broadway-tickets-c-24/"
            }
        },
        {
            "id": "24863",
            "name": "& Juliet",
            "url": "/es/entradas-espectaculos-de-broadway/juliet-e-24863/",
            "canonicalUrl": "https://www.headout.com/es/entradas-espectaculos-de-broadway/juliet-e-24863/?utm_campaign=SOME_CAMPAIGN&affiliate_code=n5cprT&utm_medium=affiliate&utm_source=",
            "city": {
                "name": "New York",
                "code": "NEW_YORK"
            },
            "images": [
                {
                    "url": "https://cdn-imgix.headout.com/media/images/4bee83f69d26f92fe6b459731fe1b3d7-24863-new-york---juliet-01.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/6a48cb2c0259f8515ae07c20696ec2f2-24863-new-york---juliet-02.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/897e413b648ab43541b31fd3d1f72e8a-24863-new-york---juliet-03.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/f45286280c8c49aa16f2e9bfe43a14c7-24863-new-york---juliet-04.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/fbd873bdfb7c1da394d8c912f58c0c8b-24863-new-york---juliet-05.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/85b9b3ed961d087a1b3e7f4f7b4b65f9-24863-new-york---juliet-06.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/84eae0652451c2ffc49ee950e1374b96-24863-new-york---juliet-07.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/ea2279a400a8148e64615e171b8833d2-24863-new-york---juliet-08.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/c31ddcfd0db7e16d623a524875c7674d-24863-new-york---juliet-09.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/ca083c5697667407211f6ad6976ff8d8-24863-new-york---juliet-10.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/5a9ecc44227eb917584569100a05aafa-24863-new-york---juliet-11.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/b94619a5ab7a3935bb1da84e29e16d2a-24863-new-york---juliet-12.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/4cee7229c6d41a7442c3ce8dee09a5f8-24863-new-york---juliet-13.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/e0d19c5a46416a65435a49e9dd76d10f-24863-new-york---juliet-14.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/89f98b11c8a45bc65ee5175647575cd7-24863-new-york---juliet-15.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/26139db2ca57a81b91283066b3f4a2e7-24863-new-york---juliet-16.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/0b5fc25de9660002b7d536984dce7fff-24863-new-york---juliet-17.jpg",
                    "type": "IMAGE"
                },
                {
                    "url": "https://cdn-imgix.headout.com/media/images/ba3a7b63d881b3f876479b834e1afb7d-24863-new-york---juliet-18.jpg",
                    "type": "IMAGE"
                }
            ],
            "experienceVideo": null,
            "startLocation": {
                "latitude": 40.75586700439453,
                "longitude": -73.98490142822266
            },
            "tourType": "EVENT",
            "reviewsDetails": {
                "ratingsCount": 2,
                "averageRating": 5.00
            },
            "listingPrice": {
                "type": "PER_PERSON",
                "currencyCode": "INR",
                "minimumPrice": {
                    "originalPrice": 8875,
                    "finalPrice": 8875
                },
                "bestDiscount": 0
            },
            "currency": {
                "code": "INR",
                "currencyName": "Indian Rupee",
                "symbol": "INR",
                "localSymbol": "₹",
                "precision": 0,
                "currency": "INR"
            },
            "language": "ES",
            "urlSlugs": {
                "EN": "/broadway-tickets/and-juliet-e-24863/",
                "ES": "/es/entradas-espectaculos-de-broadway/juliet-e-24863/",
                "FR": "/fr/billets-comedie-musicale-broadway/and-juliet-e-24863/",
                "IT": "/it/broadway-biglietti/juliet-e-24863/",
                "DE": "/de/broadway-tickets/juliet-e-24863/",
                "PT": "/pt/broadway/juliet-e-24863/",
                "NL": "/nl/broadway/juliet-e-24863/"
            },
            "hidden": false,
            "hasInstantConfirmation": true,
            "primaryCategory": {
                "id": "7",
                "name": "Entertainment",
                "urlSlugs": {
                    "EN": "/entertainment-new_york-ca-7~21553/",
                    "ES": "/es/entretenimiento-new_york-ca-7~21553/",
                    "FR": "/fr/loisirs-new_york-ca-7~21553/",
                    "IT": "/it/intrattenimento-new_york-ca-7~21553/",
                    "DE": "/de/unterhaltung-new_york-ca-7~21553/",
                    "PT": "/pt/entretenimento-new_york-ca-7~21553/",
                    "NL": "/nl/entertainment-new_york-ca-7~21553/"
                },
                "canonicalUrl": "https://www.headout.com/entertainment-new_york-ca-7~21553/"
            },
            "primarySubCategory": {
                "id": "1036",
                "name": "Musicals",
                "categoryId": "7",
                "canonicalUrl": "https://www.headout.com/musicals-new_york-sc-1036~21553/",
                "urlSlugs": {
                    "EN": "/musicals-new_york-sc-1036~21553/",
                    "ES": "/es/musicales-new_york-sc-1036~21553/",
                    "FR": "/fr/comedies-musicales-new_york-sc-1036~21553/",
                    "IT": "/it/musical-new_york-sc-1036~21553/",
                    "DE": "/de/musicals-new_york-sc-1036~21553/",
                    "PT": "/pt/musicais-new_york-sc-1036~21553/",
                    "NL": "/nl/musicals-new_york-sc-1036~21553/"
                }
            },
            "primaryCollection": {
                "id": "24",
                "name": "Broadway",
                "city": "NEW_YORK",
                "urlSlugs": {},
                "canonicalUrl": "https://www.headout.com/broadway-tickets-c-24/"
            }
        }
    ],
    "nextUrl": "https://api.headout.com/api/partners/v2/products?cityCode=NEW_YORK&campaignName=SOME_CAMPAIGN&languageCode=ES&currencyCode=INR&offset=3&limit=3",
    "prevUrl": null,
    "total": 75,
    "nextOffset": 3
}
```

</details>

## Error Handling

### Missing Request Parameters
If any required parameter is missing in the request, the API responds with a `400 Bad Request` status and details about the missing parameter.

<details>
<summary>Example Error Response</summary>

```json
{
  "status": 400,
  "error": {
    "code": "E_MISSING_PARAMETER",
    "message": "Missing required parameter: [parameter_name]"
  }
}
```

</details>

## Notes
- Ensure that all required parameters are included in your requests.
- Use appropriate city and language codes as per your application requirements.
- Pagination parameters (`offset` and `limit`) help in managing large datasets.

For more information or support, please contact [support email/contact details].