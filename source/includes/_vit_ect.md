## VIT Registration (Victoria)

> Example request

```shell
curl -H 'Authorization: lukeiamnotyourpassword' -d '{
  "documentNumber": "123456789",
  "person": {
    "firstName": "Sachin",
    "middleName": "Ramesh",
    "lastName": "Tendulkar",
    "dateOfBirth": "1973-04-23"
  },
  "trackingId": "372630f8-ccea-49a9-b682-ba11188929a9"
}' 'https://hoover.everproof.com/v1/vit'
```

> Example response

```json
{
 "approval": true,
 "status": "VERIFIED",
 "message": "TODO: Fill this in",
 "trackingId": "372630f8-ccea-49a9-b682-ba11188929a9"
}
```

This endpoint will verify an Early Childhood Teacher Registration with the Victorian Institute of Teaching.

### HTTP Request

`POST https://hoover.everproof.com/v1/vit`

### Request arguments

Argument        | Type   | Description                                                          | Required
----------------| ------ | -------------------------------------------------------------------- | -----------
documentNumber  | string | The identification number on the document or card to verify.         | Required
expiryDate      | string | The date of expiry of the document.                                  | Optional
person          | object | Possible values for person defined in the "Person" menu on the left. | Required
trackingId      | string | A value you can set that we will include in our response.            | Required

#### Person

Value       | Type                 | Description                         | Required
----------- | -------------------- | ----------------------------------- | --------
firstName   | string               | The document holder's first name    | Required
middleName  | string               | The document holder's middle name   | Optional
lastName    | string               | The document holder's last name     | Required
dateOfBirth | string (yyyy-mm-dd)  | The document holder's date of birth | Optional

### Response values

Value       | Type    | Description                         
----------- | ------- | -----------------------------
approval    | boolean | A boolean representing if the individual is permitted to teach.
status      | string  | Possible values for status defined in the "Status Attribute" menu on the left.
message     | string  | The message returned from the Victorian Institute of Teaching.
retrieved   | object  | Any extra data that we retrieve from the Victorian Institute of Teaching.
trackingId  | string  | The value that you sent with your request.
