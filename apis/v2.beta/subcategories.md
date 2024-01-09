# Subcategories API

**Resource path param:** `/subcategories`

## 1. <a name="GET - /subcategories"></a>GET `/subcategories`

### Overview
The Partner Subcategories API v2 provides endpoints for accessing the subcategories. This API is designed to facilitate partners in fetching relevant data for different cities and languages.

### Curl

#### Format
```shell
curl --location 'https://www.headout.com/api/public/v2.beta/subcategories?cityCode=<CITY_CODE>&languageCode=<LANGUAGE_CODE>' \
--header 'Headout-Auth: <YOUR_API_KEY>'
```

#### Sample Request
```shell
curl --location 'https://www.headout.com/api/public/v2.beta/subcategories?cityCode=NEW_YORK' \
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

**Object:** [`subcategory`](/object-models/v2.beta/Subcategory.md)

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
