# Fy! Chatbot API

## General
* Data is consumed and returned as [JSON](https://en.wikipedia.org/wiki/JSON).
* Date(time)s are consumed and returned using the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format, specifically `yyyy-MM-ddTHH:mm:ssZ` (UTC with zero offset).

## Authentication
Authentication requires the use of a unique chatbot API-key over HTTP Basic Auth. In practice this means using your chatbot API-key as the username and leaving the password blank.

You can make authenticated requests using a client (such as [Postman](https://learning.postman.com/docs/sending-requests/authorization/#basic-auth) or [cURL](https://curl.se/docs/manpage.html#-u)) or manually. 

To authenticate requests manually, Basic Auth requires the username and password to be separated by a colon (e.g. `my-api-key:`). This then needs to be base-64 encoded and included in the Authorization header, e.g. `Authorization: Basic bXktYXBpLWtleQ==`.

## Reference

### Endpoints
|Endpoint|Description|URL|
|---|---|---|
|[getOrder](orders.md#getorder)|Returns status for an order given order id and postcode.|`/v0/chatbot/orders?order-id={string}&postcode={string}`|