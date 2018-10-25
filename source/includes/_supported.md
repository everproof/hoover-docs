# Verification endpoints

## Supported verifications

> Example request

```shell
curl "https://hoover.everproof.com/v1/"
  -H "Authorization: lukeiamnotyourpassword"
```

> Example response

```json
[
  {
    "title": "Working with Children Check (VIC)",
    "provider": "Department of Justice & Regulation (VIC)",
    "url": "https://api.everproof.com/v1/wwcc/vic/"
  }
]
```

This endpoint will return a list of all documents that we are able to verify. The response will also include the URL that you use to access those verifications. This gives you the flexibility to programatically check the URL to use to verify a document, meaning that if we ever change URLs you should not be impacted.

### HTTP Request

`GET https://hoover.everproof.com/v1/`