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
  "trackingId": "372630f8-ccea-49a9-b682-ba11188929a9",
  "webhookUrl": "https://webhook.com/everproof/results"
}' 'https://hoover.everproof.com/v1/wwcc/qld/exemption-card'
```

> Example result (sent via webhook)

```json
{
 "result":{
  "approval": true,
  "status": "VERIFIED",
  "message": "TODO: Fill this in"
 },
 "timestamp": "2018-10-30T01:58:16+00:00",
 "trackingId": "372630f8-ccea-49a9-b682-ba11188929a9"
}
```

This endpoint will verify a Exemption Card with the Public Safety Business Agency in Queensland.

The endpoint will immediately respond with a `201-Accepted`. The result of the verification will be sent via POST to the webhookUrl you set in the request.

### HTTP Request

`POST https://hoover.everproof.com/v1/wwcc/qld/exemption-card`

### Request arguments

Argument        | Type   | Description                                                          | Required
----------------| ------ | -------------------------------------------------------------------- | -----------
documentNumber  | string | The identification number on the document or card to verify.         | Required
person          | object | Possible values for person defined in the "Person" menu on the left. | Required
trackingId      | string | A value you can set that we will include in our response.            | Required
webhookUrl      | string | The webhook address you want us to POST results to                   | Required 

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
result      | object  | The result of the verification
trackingId  | string  | The value that you sent with your request.
timestamp   | string  | ISO 8601 formatted datetime.

#### Result object

Value       | Type    | Description                         
----------- | ------- | -----------------------------
approval    | boolean | A boolean representing if the individual is permitted to work with children.
status      | string  | Possible values for status defined in the "Status Attribute" menu on the left.
message     | string  | The message returned from the Public Safety Business Agency.
retrieved   | object  | Any extra data that we retrieve from the Public Safety Business Agency.