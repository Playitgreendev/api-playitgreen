# Introduction

A payment API is an API (application programming interface) that enables ecommerce businesses to seamlessly manage payments. Payment APIs have the power to optimize the payments process for both businesses and shoppers, as they can make transactions faster and more secure.

Playitgreen was built from the ground-up with a JSON API that makes it easy for developers automate manage payments .


## Who is API payment dedicated for?

Api payment is mainly dedicated for Business Owners who wants to connect their current website with green initiative via Play It Green. They can implement API Payment into their sales business model and based on that reduce their negative environmental impact.

## How API payment works within Play It Green platform?

API Payment enables a client to automatically order trees based on conditions that he will implement into api connection code developed into his website. For instance for the sale of one piece of certain product on his website, order for one tree will be generated. Orders are gathered throughout the month. On the very end of the last day of the month our system will generate the purchase order based on all orders gathered. If credit/debit card is added to the clients account within Play It Green application then payment will be processed. In case of credit/debit card not being added then system will generate a button to pay for the order by adding credit/debit card details manually.

## Authorization

All API requests require the use of a generated API key. You can find your API key, or generate a new one clicking the “Settings -> API Payments” sidebar item.

To authenticate an API request, you should provide your API key in the `Authorization: Bearer : tokenGeneratedInSettings` header.

```http
GET /api/campaigns/?api_key=12345678901234567890123456789012
```

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `api_key` | `string` | **Required**. Your Gophish API key |

## Responses

Many API endpoints return the JSON representation of the resources created or edited. However, if an invalid request is submitted, or some other error occurs, Gophish returns a JSON response in the following format:

```javascript
{
  "message" : string,
  "success" : bool,
  "data"    : string
}
```

The `message` attribute contains a message commonly used to indicate errors or, in the case of deleting a resource, success that the resource was properly deleted.

The `success` attribute describes if the transaction was successful or not.

The `data` attribute contains any other metadata associated with the response. This will be an escaped string containing JSON data.

## Status Codes

Gophish returns the following status codes in its API:

| Status Code | Description |
| :--- | :--- |
| 200 | `OK` |
| 201 | `CREATED` |
| 400 | `BAD REQUEST` |
| 404 | `NOT FOUND` |
| 500 | `INTERNAL SERVER ERROR` |


## Examples of code


