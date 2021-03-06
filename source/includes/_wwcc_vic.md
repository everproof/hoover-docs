## WWCC (Victoria)

> Example request

```shell
curl -H 'Authorization: lukeiamnotyourpassword' -d '{
  "documentNumber": "123456789",
  "person": {
    "firstName": "Sachin",
    "middleName": "Ramesh",
    "lastName": "Tendulkar"
  },
  "trackingId": "372630f8-ccea-49a9-b682-ba11188929a9",
  "webhookUrl": "https://webhook.com/everproof/results"
}' 'https://hoover.everproof.com/v1/wwcc/vic'
```

> Example result (sent via webhook)

```json
{
 "result": {
  "approval": true,
  "status": "VERIFIED",
  "message": "Working with Children Check number 123456789 (Employee) 
              for Sachin Ramesh TENDULKAR is current. This person 
              may engage in child related work and their card expires 
              on 25 Mar 2025.",
  "retrieved": {
      "cardType": "Employee",
      "expiryDate": "2025-03-25",
  }
 },
 "timestamp": "2018-10-30T01:58:16+00:00",
 "trackingId": "372630f8-ccea-49a9-b682-ba11188929a9"
}
```

This endpoint will verify a Working With Children Check issued by the Department of Justice and Regulation in Victoria.

The endpoint will immediately respond with a `201-Accepted`. The result of the verification will be sent via POST to the webhookUrl you set in the request.

### HTTP Request

`POST https://hoover.everproof.com/v1/wwcc/vic`

### Request arguments

Argument        | Type   | Description                                                          | Required
----------------| ------ | -------------------------------------------------------------------- | -----------
documentNumber  | string | The identification number on the document or card to verify.         | Required
expiryDate      | string | The date of expiry of the document.                                  | Optional
person          | object | Defined directly below                                               | Required
trackingId      | string | A value you can set that we will include in our response.            | Required
webhookUrl      | string | The webhook address you want us to POST results to                   | Required 

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
result      | object  | The result of the verification
trackingId  | string  | The value that you sent with your request.
timestamp   | string  | ISO 8601 formatted datetime.

#### Result object 

Result       | Type    | Description                         
----------- | ------- | -----------------------------
approval    | boolean | A boolean representing if the individual is permitted to work with children.
status      | string  | Possible values for status defined in the "Status Attribute" section of this documentation.
message     | string  | The message returned from the Department of Justice and Regulation.
retrieved   | object  | Any extra data that we retrieve from the Department of Justice and Regulation.