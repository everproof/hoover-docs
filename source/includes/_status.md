# Status Attribute

These are the possible values for the status attribute in all response objects.

Status | Meaning
---------- | -------
VERIFIED    | The document was verified with the source.
NOT_FOUND   | No document was not found with the details provided.
ERROR       | The service is currently down.
EXPIRED     | The document was found and it is expired.
REVOKED     | The document has been revoked by the source and is no longer valid.
PROCESSING  | The document was found but it is being processed by the source.
