# Collections API

**Resource path param:** `/collections`

## 1. <a name="GET - /collections"></a>GET `/collections`

### Overview
The Partner Collections API v2 provides endpoints for accessing the collections. This API is designed to facilitate partners in fetching relevant data for different cities and languages.

### Curl

#### Format
```shell
curl --location 'https://www.headout.com/api/public/v2/collections?cityCode=<CITY_CODE>&languageCode=<LANGUAGE_CODE>&limit=<LIMIT>&offset=<OFFSET>' \
--header 'Headout-Auth: <YOUR_API_KEY>'
```

#### Sample Request
```shell
curl --location 'https://www.headout.com/api/public/v2/collections?cityCode=NEW_YORK' \
--header 'Headout-Auth: <YOUR_API_KEY>'
```

### Request

#### API Parameters
| Parameter      | Required / Optional | Description                             | Default Value |
|----------------|---------------------|-----------------------------------------|---------------|
| `cityCode`     | Required            | The city code to fetch collections for. |               |
| `languageCode` | Optional            | Language code.                          | `EN`          |
| `offset`       | Optional            | Offset for pagination.                  | `0`           |
| `limit`        | Optional            | Limit for pagination.                   | `10`          |

#### API Headers
| Header         | Required / Optional | Description              |
|----------------|---------------------|--------------------------|
| `Headout-Auth` | Required            | The Authorization Token. |


### Response

**Object:** [`Collection`](/object-models/v2/Collection.md)

<details>
<summary>Response Example</summary>

```json
{
  "collections": [
    {
      "id": "24",
      "name": "Broadway",
      "cityCode": "NEW_YORK",
      "localeSpecificUrls": {
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
      "id": "161",
      "name": "Off Broadway Show Tickets",
      "cityCode": "NEW_YORK",
      "localeSpecificUrls": {
        "EN": "/off-broadway-show-tickets-c-161/",
        "ES": "/es/entradas-espectaculos-off-broadway-c-161/",
        "FR": "/fr/off-broadway-c-161/",
        "IT": "/it/biglietti-per-spettacoli-off-broadway-c-161/",
        "DE": "/de/off-broadway-c-161/",
        "PT": "/pt/ingressos-para-espetaculos-off-broadway-c-161/",
        "NL": "/nl/off-broadway-c-161/"
      },
      "canonicalUrl": "https://www.headout.com/off-broadway-show-tickets-c-161/"
    },
    {
      "id": "121",
      "name": "Statue of Liberty",
      "cityCode": "NEW_YORK",
      "localeSpecificUrls": {
        "EN": "/statue-of-liberty-cruises-c-121/",
        "ES": "/es/estatua-de-la-libertad-c-121/",
        "FR": "/fr/statue-de-la-liberte-c-121/",
        "IT": "/it/statua-della-liberta-c-121/",
        "DE": "/de/freiheitsstatue-c-121/",
        "PT": "/pt/estatua-da-liberdade-c-121/",
        "NL": "/nl/vrijheidsbeeld-c-121/"
      },
      "canonicalUrl": "https://www.headout.com/statue-of-liberty-cruises-c-121/"
    }
  ],
  "nextUrl": null,
  "prevUrl": null,
  "total": 3,
  "nextOffset": null
}
```

</details>

---

## Error Handling
Refer to [this](./error-handling.md) document for handling errors in the APIs.

## Notes
- Ensure that all required parameters are included in your requests.
- Use appropriate city and language codes as per your application requirements.
- Pagination parameters (`offset` and `limit`) help in managing large datasets.
