#Execution Report

## Description

A message that reports a change in the status of a FIX client order.

This type of message is sent by the system in the following cases:

* To confirm that the order as accepted by the system.
* To reject the order or its part.
* To confirm that the order was cancelled. 
* To provide execution information on accepted orders. If the order was executed in parts, then for each executed part a separate **Execution report** message is sent.
* To provide order status information.

## Parameters

Tag| Tag name| Description| Required| Data type
---|---------|------------|---------|----------
 |[Standard Header](StandardHeader.md)| A group of tags that is provided at the beginning of every message sent between the FIX client and the system. For a NewOrderSingle message type, **MsgType**(35 ) = 8.
37| `OrderID`| A unique identifier allocated by the system for the order whose execution status is being reported.| Y| string
11|`ClOrdID`| Identifier of the order whose execution status is reported provided be the FIX client. It is `ClOrdId` from the  **NewOrderSingle** message.|N|string
17|`ExecId`| The unique identifier allocated by the system to the **ExecutionReport** message.|Y|string
150| `ExecType`| The reason for sending this **ExecutionReport** message.|Y|char
39| `OrdStatus`| Current state of the order|Y|char
1|`Account`| The account on behalf of which the order was placed.|N|string

##Message example

`8=FIX.4.49=29935=834=1049=Fix_server_Ext52=20221005-04:10:29.00556=Fix_client_Ext1=90106=011=2841ff99-ed22-42b5-9cda-b533eb4965c714=017=51337=30738=1000.00000000039=040=154=255=EURUSD58=New order '2841ff99-ed22-42b5-9cda-b533eb4965c7' placed59=460=20221005-04:10:29.004150=0151=1000.00000000010=193`