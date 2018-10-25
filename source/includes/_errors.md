# Errors

Everproof uses conventional HTTP response codes to indicate the success or failure of an API request. In general: Codes in the 2xx range indicate success. Codes in the 4xx range indicate an error that failed given the information provided (e.g., a required parameter was omitted, etc.). 404 errors indicate that a check is not supported. Codes in the 5xx range indicate an error with Everproof’s servers (these are rare).


Response Code | Meaning
---------- | -------
200 | The request was successful (**this does not mean verification successful**)
400 | Your request was invalid (i.e., missing properties)
401 | Your API key was invalid
404 | The resource doesn't exist
500 | Error with our servers (very rare)
