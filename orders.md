# Fy! Chatbot API - Order

## Overview
<a name="overview"></a>
The Fy! Chatbot API allows to retrieve latest information about the order.

### URI scheme
* *Host:* marketplace-api.iamfy.co
* *Scheme:* HTTPS

### Content type
* Consumes: `application/json`
* Returns: `application/json`

### Operations
* [getOrder](#getorder)

----

<a name="paths"></a>
## Paths

<a name="getorder"></a>
### `GET` /v0/chatbot/orders

Returns order with specified `order-id` and `postcode` parameters.

|<!--  -->|<!--  -->|
|-|-|
|Operation|`getOrder`|
|Method|`GET`|
|Endpoint|`/v0/chatbot/orders`|
<br>

#### Parameters

|Type|Name|Description|Schema|
|-|-|-|-|
|Query|**order-id** <br>*required*|Order id.|string|
|Query|**postcode** <br>*required*|The postcode must match the postcode on the order. |string|
<br>

#### Responses

An example of a successful response from the [getOrder](#getorder) operation:

```json
{"data": {
  "orderReference": "SO-1234",
  "productName": "Flower print",
  "status": "shipped",
  "isPoD": false,
  "deliveryAddressCountry": "UK",
  "shippedOn": "2021-04-08T00:00:00.00Z",
  "courier": "dhl"
  }
}
```

|Status|Description|Schema|
|-|-|-|
|`200`|Success.|[GetOrderResponse](#getordersresponse)|
|`400`|Missing or invalid parameters.|[GetOrderResponse](#getordersresponse)|
|`403`|Access forbidden.|[GetOrderResponse](#getordersresponse)|
|`404`|Not Found.|[GetOrderResponse](#getordersresponse)
|`500`|Server error.|[GetOrderResponse](#getordersresponse)|

----

## Definitions
<a name="definitions"></a>

### GetOrderResponse
<a name="getordersresponse"></a>

```
{"data": <Order>} | <Errors>
```

<details>
  <summary>View descriptions</summary>
  
|Name|Description|Schema|
|-|-|-|
|**payload**    <br>*optional*|The payload for the getOrder operation.|[Order](#order)|
|**errors**     <br>*optional*|One or more unexpected errors which occurred during the getOrder operation.|-|

</details>

### Order
<a name="order"></a>

```
{"orderReference"         <string>
 "productName"            <string>
 "status"                 <string>
 "isPoD"                  <boolean>
 "deliveryAddressCountry" <string>
 "shippedOn"              <string>
 "courier"                <string>}
```

<details>
  <summary>View descriptions</summary>
  
|Name|Description|Schema|
|-|-|-|
|**orderReference**         <br>*required*|The reference for a specific Fy! order: an "SO-" prefix followed by a series of numbers. |string|
|**productName**            <br>*optional*|The name of the product associated with the order. |string|
|**status**                 <br>*required*|The order's current status. Available statuses:<br> - pending, <br> - acknowledged, <br> - shipped.|string|
|**isPoD**                  <br>*required*|Flag to indicate if order has PoD products or not.|boolean|
|**deliveryAddressCountry** <br>*required*|The recipient's country.|string|
|**shippedOn**              <br>*optional*|The (ISO-8601) datetime when the order was shipped.|string|
|**courier**                <br>*optional*|Courier name.|string|

</details>
