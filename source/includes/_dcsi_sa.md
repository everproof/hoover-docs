## DCSI (South Australia)

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
}' 'https://hoover.everproof.com/v1/wwcc/sa'
```

> Example response

```json
{
 "approval": true,
 "status": "VERIFIED",
 "message": "Valid for 3 years from the determination date unless revoked by the screening unit.",
 "retrieved": {
     "attainedDate": "2016/10/24",
     "expiryDate": "2019/10/24"
 },
 "trackingId": "372630f8-ccea-49a9-b682-ba11188929a9"
}
```

This endpoint will verify a DCSI Screening conducted by the Department for Communities and Social Inclusion in South Australia.

### HTTP Request

`POST https://hoover.everproof.com/v1/wwcc/sa`

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
middleName  | string               | The document holder's middle name   | Required
lastName    | string               | The document holder's last name     | Required
dateOfBirth | string (yyyy-mm-dd)  | The document holder's date of birth | Required

### Response values

Value       | Type    | Description                         
----------- | ------- | -----------------------------
approval    | boolean | A boolean representing if the individual is permitted to work with children.
status      | string  | Possible values for status defined in the "Status Attribute" section of this documentation.
message     | string  | The message returned from the Department for Communities and Social Inclusion.
retrieved   | object  | Any extra data that we retrieve from the Department for Communities and Social Inclusion.
trackingId  | string  | The value that you sent with your request.
