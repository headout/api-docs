# Basics

## API Response Format

All APIs return a response in JSON format.

## Https

APIs run over `https`. If you specify `http`, the url will be redirected to `https` using HTTP Status 301 (Permanent Redirect).

## Versioning

### Url Prefix

All APIs are prefixed with `/api/v{version_number}`. If the current version number is `1` then the your api prefix will be `/api/v1`.
