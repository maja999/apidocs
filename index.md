---
title: "About CryptoExchange API"
keywords: CryptoExchange API
sidebar: mydoc_sidebar
permalink: index.html
summary: With CryptoExchange API, clients can quickly enable fiat-to-crypto exchange in their own applications. Following versions of the API will enable crypto-to- fiat, other usful actions and features.
---

​
# About CryptoExchange API
​
With CryptoExchange API, clients can quickly enable fiat-to-crypto exchange in their own applications. Following versions of the API will enable crypto-to- fiat, other usful actions and features.
​<br><br>
​

# Background
​
TBD
​<br><br>​
​

# Available actions
​
Several actions are available to enable buying crypto currencies. Expected sequence of actions is displayed on following diagram:
​<br><br>
​
<div class="mermaid">

sequenceDiagram
Customer ->> API_Client: Enter crypto
Note right of API_Client: Orders will be <br/>fetched only for<br/> current customer
API_Client ->> API: Get orders
API -x API_Client: All orders
API_Client -x Customer: Show orders
Customer ->> API_Client: Buy crypto
API_Client ->> API: Generate address
Note right of API_Client: If there is address <br/> already, this step <br/> is skipped 
API -x API_Client: New address
API_Client ->> API: Get rates
API -x API_Client: Latest rates
API_Client -x Customer: Show buy form
Customer ->> API_Client: Place order
API_Client ->> API: Place order
API -x API_Client: Order details
API_Client -x Customer: Order details
API_Client ->> API: Get order status
API -x API_Client: Order status
API_Client -x Customer: Update order status

</div>
​

## Client configuration
​
This actions returns configuration made while onboarding client. It includes basic trading limits and can be modified only by API administrator. Following versions will include configuration for enhanced security.
​<br><br>


## Latest rates
​
Via this action, API client can get latest rates and show estimated amout to customer before placing order.
​<br><br>​


## Creating new address
​
To be able to place buy order, customer needs to have valid crypto address. With this action, API client can create one on behalf of the customer. However, it is strongly recommended to create and manage addresses on API client side, or even on customer device. Wallet address can be created using many of available Wallet applications that can be installed directly on customer's mobile device.
​​<br><br>


## Validating an address
​
In case when customer already has an address and enters it manually, address needs to be validated. API client can perform address validation using this action.
​​<br><br>


## Address balance
​
API client may want to display current address balance to the customer and this action can serve that purpose.
​​<br><br>


## Placing buy order
​
This action enables actual placing of buy order. Required inputs are: crypto currency, desired amount and destination address. Once the order is placed, our order ID is returned (UUID) that can be later used to get order details.
​​<br><br>


## Getting order status
​
To get current status and other order details, use order ID (UUID) returned in Place order action response. Time needed for transfer to take place depends on many factors, such as currency, fee, moment of placing order etc.
​<br><br>

## Listing all orders for customer
​
API customer can use this action to get list of all orders for given customer. In future API versions, different filters will be enabled.