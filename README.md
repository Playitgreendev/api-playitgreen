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
### Products type

| Product Code     | Description       |
|:-----------------|:------------------|
| `PLAY1TREEAPI`   | 1 Trees Planted   |
| `PLAY2TREEAPI`   | 2 Trees Planted   |
| `PLAY3TREEAPI`   | 3 Trees Planted   |
| `PLAY4TREEAPI`   | 4 Trees Planted   |
| `PLAY5TREEAPI`   | 5 Trees Planted   |
| `PLAY6TREEAPI`   | 6 Trees Planted   |
| `PLAY7TREEAPI`   | 7 Trees Planted   |
| `PLAY8TREEAPI`   | 8 Trees Planted   |
| `PLAY9TREEAPI`   | 9 Trees Planted   |
| `PLAY10TREEAPI`  | 10 Trees Planted  |
| `PLAY50TREEAPI`  | 50 Trees Planted  |
| `PLAY100TREEAPI` | 100 Trees Planted |
| `PLAY150TREEAPI` | 150 Trees Planted |
| `PLAY200TREEAPI` | 200 Trees Planted |
| `PLAY250TREEAPI` | 250 Trees Planted |
| `PLAY300TREEAPI` | 300 Trees Planted |
| `PLAY350TREEAPI` | 350 Trees Planted |
| `PLAY400TREEAPI` | 400 Trees Planted |
| `PLAY450TREEAPI` | 450 Trees Planted |
| `PLAY500TREEAPI` | 500 Trees Planted |


### Buy trees

```http
POST /api/buy_trees
```

#### Request

| Parameter     | Type     | Description                                 |
|:--------------|:---------|:--------------------------------------------|
| `quantity`    | `number` | **Required**. Number of Trees you want buy  |
| `productCode` | `string` | **Required**. Specify the product code      |
| `referenceNo` | `string` | **Required**. Provide reference number      |

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

| Status Code | Description             |
|:------------|:------------------------|
| 200         | `OK`                    |
| 400         | `BAD REQUEST`           |
| 404         | `NOT FOUND`             |
| 500         | `INTERNAL SERVER ERROR` |


## Examples of code


### curl 
```
curl --location --request POST 'https://url_api/api/buy_trees' \
--header 'Authorization: Bearer testBeared' \
--header 'Content-Type: application/json' \
--data-raw '{
"quantity": 1, 
"productCode":"PLAY1TREEAPI",
"referenceNo":"X12345"
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
$request->setBody('{\n	"quantity":1,\n"productCode":"PLAY1TREEAPI",\n"referenceNo":"X12345"\n}');
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
.body("{\n    \"quantity\": 1, \"productCode\":\"PLAY1TREEAPI\", \"referenceNo\":\"X12345\" \n}")
.asString();
```
