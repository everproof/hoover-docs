## WWCC (Western Australia)

> Example request

```shell
curl -H 'Authorization: lukeiamnotyourpassword' -d '{
  "documentNumber": "123456789",
  "person": {
    "firstName": "Sachin",
    "middleName": "Ramesh",
    "lastName": "Tendulkar"

  },
  "trackingId": "372630f8-ccea-49a9-b682-ba11188929a9"
}' 'https://hoover.everproof.com/v1/wwcc/wa'
```

> Example response

```json
{
 "approval": true,
 "status": "VERIFIED",
 "message": "Card number 123456789 for Tendulkar is valid on the date of Thursday, 25 October 2018",
 "trackingId": "372630f8-ccea-49a9-b682-ba11188929a9"
}
```

This endpoint will verify a Working with Children Check issued by the Department for Child Protection and Family Support in Western Australia.

### HTTP Request

`POST https://hoover.everproof.com/v1/wwcc/wa`

### Request arguments

Argument        | Type   | Description                                                          | Required
----------------| ------ | -------------------------------------------------------------------- | -----------
documentNumber  | string | The identification number on the document or card to verify.         | Required
expiryDate      | string | The date of expiry of the document.                                  | Optional
person          | object | Defined directly below                                               | Required
trackingId      | string | A value you can set that we will include in our response.            | Required

#### Person

Value       | Type                 | Description                         | Required
----------- | -------------------- | ----------------------------------- | --------
firstName   | string               | The document holder's first name    | Optional
middleName  | string               | The document holder's middle name   | Optional
lastName    | string               | The document holder's last name     | Required
dateOfBirth | string (yyyy-mm-dd)  | The document holder's date of birth | Optional

### Response values

Value       | Type    | Description                         
----------- | ------- | -----------------------------
approval    | boolean | A boolean representing if the individual is permitted to work with children.
status      | string  | Possible values for status defined in the "Status Attribute" section of this documentation.
message     | string  | The message returned from the Department for Child Protection and Family Support.
retrieved   | object  | Any extra data that we retrieve from the Department for Child Protection and Family Support.
trackingId  | string  | The value that you sent with your request.
