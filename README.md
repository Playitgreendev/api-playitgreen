# Introduction

A payment API is an API (application programming interface) that enables ecommerce businesses to seamlessly manage payments. Payment APIs have the power to optimize the payments process for both businesses and shoppers, as they can make transactions faster and more secure.

Playitgreen was built from the ground-up with a JSON API that makes it easy for developers automate manage payments .


## Who is API payment dedicated for?

Api payment is mainly dedicated for Business Owners who wants to connect their current website with green initiative via Play It Green. They can implement API Payment into their sales business model and based on that reduce their negative environmental impact.

## How API payment works within Play It Green platform?

API Payment enables a client to automatically order trees based on conditions that he will implement into api connection code developed into his website. For instance for the sale of one piece of certain product on his website, order for one tree will be generated. Orders are gathered throughout the month. On the very end of the last day of the month our system will generate the purchase order based on all orders gathered. If credit/debit card is added to the clients account within Play It Green application then payment will be processed. In case of credit/debit card not being added then system will generate a button to pay for the order by adding credit/debit card details manually.

## Authorization

All API requests require the use of a generated API key. You can find your API key, or generate a new one clicking the “Settings -> API Payments” sidebar item.

To authenticate an API request, you should provide your API key in the `Authorization: Bearer tokenGeneratedInSettings` header.


## Methods
### Buy trees

```http
POST /api/buy_trees
```

#### Request

| Parameter | Type     | Description                                |
| :--- |:---------|:-------------------------------------------|
| `quantity` | `number` | **Required**. Number of Trees you want buy |

#### Response

Playitgreen returns a success JSON response in the following format

```javascript
{
  "orderId" : number,
  "productInOrderId" : number
}
```

The `orderId` attribute describe order id. Order id is the same within the billing month. 

The `productInOrderId` attribute describe product id in order. Usefful if you want find concreate sub order. 


## Status Codes

Playitgreen returns the following status codes in its API:

| Status Code | Description |
| :--- | :--- |
| 200 | `OK` |
| 400 | `BAD REQUEST` |
| 404 | `NOT FOUND` |
| 500 | `INTERNAL SERVER ERROR` |


## Examples of code


### curl 
```
curl --location --request POST 'https://url_api/api/buy_trees' \
--header 'Authorization: Bearer testBeared' \
--header 'Content-Type: application/json' \
--data-raw '{
"quantity": 1
}'
```
### php
```
require_once 'HTTP/Request2.php';
$request = new HTTP_Request2();
$request->setUrl('https://url_api/api/buy_trees');
$request->setMethod(HTTP_Request2::METHOD_POST);
$request->setConfig(array(
'follow_redirects' => TRUE
));
$request->setHeader(array(
'Authorization' => 'Bearer testBeared',
'Content-Type' => 'application/json'
));
$request->setBody('{\n    "quantity": 1\n}');
try {
$response = $request->send();
if ($response->getStatus() == 200) {
echo $response->getBody();
}
else {
echo 'Unexpected HTTP status: ' . $response->getStatus() . ' ' .
$response->getReasonPhrase();
}
}
catch(HTTP_Request2_Exception $e) {
echo 'Error: ' . $e->getMessage();
}
```
### java unirest
```
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://url_api/api/buy_trees")
.header("Authorization", "Bearer testBeared")
.header("Content-Type", "application/json")
.body("{\n    \"quantity\": 1\n}")
.asString();
```
