# Errors

Everproof uses conventional HTTP response codes to indicate the success or failure of an API request. In general: Codes in the 2xx range indicate success. Codes in the 4xx range indicate an error that failed given the information provided (e.g., a required parameter was omitted, etc.). 404 errors indicate that a check is not supported. Codes in the 5xx range indicate an error with Everproof’s servers (these are rare).


Response Code | Meaning
---------- | -------
500 | For server errors
404 | For not supported checks
400 | For validation errors (missing properties)
200 | For everything else