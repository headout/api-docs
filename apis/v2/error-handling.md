# Error Handling

## Missing Request Parameters
If a required parameter is missing in the request, the API responds with a `400 Bad Request` status and provides details about the missing parameter.

<details>
<summary>Example Error Response for Missing Parameters</summary>

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

## Invalid Argument Errors
This category includes errors due to invalid values for parameters or type mismatches. The API responds with a `400 Bad Request` status and a specific error message indicating the nature of the invalid argument.

### Invalid Enum Value
When an invalid enum value is provided (e.g., for `cityCode`, `languageCode`, or `currencyCode`).

<details>
<summary>Example Error Response for Invalid Enum Value</summary>

```json
{
  "status": 400,
  "error": {
    "code": "E_INVALID_ARGUMENT",
    "message": "Invalid [enum_type] code: [provided_value]. [Enum_type] doesn't exist."
  }
}
```

</details>

### Other Invalid Arguments
For other types of invalid arguments, such as format issues.

<details>
<summary>Example Error Response for Other Invalid Arguments</summary>

```json
{
  "status": 400,
  "error": {
    "code": "E_INVALID_ARGUMENT",
    "message": "[specific_error_message]"
  }
}
```

</details>

## General Request Processing Errors
For any other unhandled exceptions during the request processing, the API responds with a `400 Bad Request` status and a general error message.

<details>
<summary>Example Error Response for General Errors</summary>

```json
{
  "status": 400,
  "error": {
    "code": "E_ERROR_PROCESSING_REQUEST",
    "message": "Error processing request"
  }
}
```

</details>