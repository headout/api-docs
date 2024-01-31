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

**Object:** [`Category`](/object-models/v2/Category.md)

<details>
<summary>Response Example</summary>

```json
{
  "categories": [
    {
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
    {
      "id": "2",
      "name": "Tours",
      "localeSpecificUrls": {
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
      "id": "3",
      "name": "Transportation",
      "localeSpecificUrls": {
        "EN": "/transportation-new_york-ca-3~21553/",
        "ES": "/es/traslados-new_york-ca-3~21553/",
        "FR": "/fr/transport-new_york-ca-3~21553/",
        "IT": "/it/trasferimenti-new_york-ca-3~21553/",
        "DE": "/de/transfer-new_york-ca-3~21553/",
        "PT": "/pt/transporte-new_york-ca-3~21553/",
        "NL": "/nl/vervoer-new_york-ca-3~21553/"
      },
      "canonicalUrl": "https://www.headout.com/transportation-new_york-ca-3~21553/"
    }
  ]
}
```

</details>

---

## Error Handling
Refer to [this](./error-handling.md) document for handling errors in the APIs.

## Notes
- Ensure that all required parameters are included in your requests.
- Use appropriate city and language codes as per your application requirements.
