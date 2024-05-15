#Execution Report

A message that reports a change in the status of a FIX client order.

This type of message is sent by the system in the following cases:

* To confirm that the order as accepted by the system.
* To reject the order or its part.
* To confirm that the order was cancelled. 
* To provide execution information on accepted orders. If the order was executed in parts, then for each executed part a separate **Execution report** message is sent.
* To provide order status information.

Tag| Tag name| Description| Required| Data type
---|---------|------------|---------|----------
 |[Standard Header](StandardHeader.md)| A group of tags that is provided at the beginning of every message sent between the FIX client and the system. For a NewOrderSingle message type, **MsgType**(35 ) = 8.
37| `OrderID`| A unique identifier allocated by the system for the order whose execution status is being reported. Y| string
11|`ClOrdID`| Identifier of the order whose execution status is reported provided be the FIX client. It is `ClOrdId` from the  **NewOrderSingle** message.|N|string
17|`ExecId`| The unique identifier allocated by the system to the **ExecutionReport** message.|Y|string
150| `ExecType`| The reason for sending this **ExecutionReport** message.|Y|char
39| `OrdStatus`| Current state of the order|Y|char
1|`Account`| The account on behalf of which the order was placed.|N|string
