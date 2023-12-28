# Collections API

**Resource path param:** `/collections`

## 1. <a name="GET - /collections"></a>GET `/collections`

### Overview
The Partner Collections API v2 provides endpoints for accessing the collections. This API is designed to facilitate partners in fetching relevant data for different cities and languages.

### Curl

#### Format
```shell
curl --location 'https://www.headout.com/api/partners/v2/collections?cityCode=<CITY_CODE>&languageCode=<LANGUAGE_CODE>&limit=<LIMIT>&offset=<OFFSET>' \
--header 'Headout-Auth: <YOUR_API_KEY>'
```

#### Sample Request
```shell
curl --location 'https://www.headout.com/api/partners/v2/collections?cityCode=NEW_YORK' \
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

**Object:** [`category`](/object-models/v2/Collection.md)

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
    "nextUrl": "https://www.headout.com/api/partners/v2/collections?cityCode=NEW_YORK&campaignName=SOME_CAMPAIGN&languageCode=ES&currencyCode=INR&offset=3&limit=3",
    "prevUrl": null,
    "total": 39,
    "nextOffset": 3
}
```

</details>

---

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
