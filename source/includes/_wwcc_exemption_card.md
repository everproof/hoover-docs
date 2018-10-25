## Exemption Card (Queensland)

> Example request

```shell
curl -H 'Authorization: lukeiamnotyourpassword' -d '{
  "documentNumber": "123456789",
  "person": {
    "firstName": "Sachin",
    "middleName": "Ramesh",
    "lastName": "Tendulkar",
  },
  "trackingId": "372630f8-ccea-49a9-b682-ba11188929a9"
}' 'https://hoover.everproof.com/v1/wwcc/qld/exemption-card'
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

This endpoint will verify a Exemption Card with the Public Safety Business Agency in Queensland.

### HTTP Request

`POST https://hoover.everproof.com/v1/wwcc/qld/exemption-card`

### Request arguments

Argument        | Type   | Description                                                          | Required
----------------| ------ | -------------------------------------------------------------------- | -----------
documentNumber  | string | The identification number on the document or card to verify.         | Required
person          | object | Possible values for person defined in the "Person" menu on the left. | Required
trackingId      | string | A value you can set that we will include in our response.            | Required

#### Person

Value       | Type                 | Description                         | Required
----------- | -------------------- | ----------------------------------- | --------
firstName   | string               | The document holder's first name    | Required
middleName  | string               | The document holder's middle name   | Required
lastName    | string               | The document holder's last name     | Required
dateOfBirth | string (yyyy-mm-dd)  | The document holder's date of birth | Optional

### Response values

Value       | Type    | Description                         
----------- | ------- | -----------------------------
approval    | boolean | A boolean representing if the individual is permitted to work with children.
status      | string  | Possible values for status defined in the "Status Attribute" menu on the left.
message     | string  | The message returned from the Public Safety Business Agency.
retrieved   | object  | Any extra data that we retrieve from the Public Safety Business Agency.
trackingId  | string  | The value that you sent with your request.
