# Subcategories API

**Resource path param:** `/subcategories`

## 1. <a name="GET - /subcategories"></a>GET `/subcategories`

### Overview
The Partner Subcategories API v2 provides endpoints for accessing the subcategories. This API is designed to facilitate partners in fetching relevant data for different cities and languages.

### Curl

#### Format
```shell
curl --location 'https://www.headout.com/api/public/v2/subcategories?cityCode=<CITY_CODE>&languageCode=<LANGUAGE_CODE>' \
--header 'Headout-Auth: <YOUR_API_KEY>'
```

#### Sample Request
```shell
curl --location 'https://www.headout.com/api/public/v2/subcategories?cityCode=NEW_YORK' \
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

**Object:** [`SubCategory`](/object-models/v2/Subcategory.md)

<details>
<summary>Response Example</summary>

```json
{
  "subCategories": [
    {
      "id": "1002",
      "name": "Museums",
      "categoryId": "1",
      "canonicalUrl": "https://www.headout.com/museums-new_york-sc-1002~21553/",
      "localeSpecificUrls": {
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
      "id": "1006",
      "name": "Religious Sites",
      "categoryId": "1",
      "canonicalUrl": "https://www.headout.com/religious-sites-new_york-sc-1006~21553/",
      "localeSpecificUrls": {
        "EN": "/religious-sites-new_york-sc-1006~21553/",
        "ES": "/es/sitios-religiosos-new_york-sc-1006~21553/",
        "FR": "/fr/site-religieux-new_york-sc-1006~21553/",
        "IT": "/it/siti-religiosi-new_york-sc-1006~21553/",
        "DE": "/de/religiose-statten-new_york-sc-1006~21553/",
        "PT": "/pt/locais-religiosos-new_york-sc-1006~21553/",
        "NL": "/nl/religieuze-plaatsen-new_york-sc-1006~21553/"
      }
    },
    {
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
