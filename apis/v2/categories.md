# Categories API
**Resource path param:** `/categories`

## 1. <a name="GET - /categories"></a>GET `/categories`

### Overview
The Partner Categories API v2 provides endpoints for accessing the categories. This API is designed to facilitate partners in fetching relevant data for different cities and languages.

### Curl

#### Format
```shell
curl --location 'https://www.headout.com/api/public/v2/categories?cityCode=<CITY_CODE>&languageCode=<LANGUAGE_CODE>' \
--header 'Headout-Auth: <YOUR_API_KEY>'
```

#### Sample Request
```shell
curl --location 'https://www.headout.com/api/public/v2/categories?cityCode=NEW_YORK' \
--header 'Headout-Auth: <YOUR_API_KEY>'
```

### Request

#### API Parameters
| Parameter      | Required / Optional | Description                            | Default Value |
|----------------|---------------------|----------------------------------------|---------------|
| `cityCode`     | Required            | The city code to fetch categories for. |               |
| `languageCode` | Optional            | Language code.                         | `EN`          |

#### API Headers
| Header         | Required / Optional | Description              |
|----------------|---------------------|--------------------------|
| `Headout-Auth` | Required            | The Authorization Token. |


### Response

**Object:** [`category`](/object-models/v2/Category.md)

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
