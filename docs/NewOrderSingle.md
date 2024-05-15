#NewOrderSingle

A **NewOrderSingle** message is sent by a FIX client to place a new order.

In response, the system sends:

* one or multiple **ExecutionReport** messages to confirm that the order was received (`OrderStatus` = 0)

* one or multiple **ExecutionReport** messages to provide the order execution result

If the order was executed in parts, then for each executed part the system sends an ExecutionReport message.

**Example**: an order is sent to a liquidity pool with two liquidities and executed on both of them.

Result: the FIX client receives the following messages:

* two **ExecutionReport** messages with `OrdStatus` = 0 (*New*) to confirm that each part of the order was accepted.

* one **ExecutionReport** message with `OrdStatus` = 1 (*Partially filled*) to confirm the execution of the order part on one liquidity.

* one **ExecutionReport** message with `OrdStatus` =  (*Filled*) to confirm execution of the residual order part on the other liquidity.


Tag    | Tag name    |   Description | Required| Data type
-------|-------------|------------------|---------|----------
 |[Standard Header](StandardHeader.md)| A group of tags that is provided at the beginning of every message sent between the FIX client and the system. For a NewOrderSingle message type, **MsgType**(35 ) = F.
11     |`ClOrdId`     |The order identifier provided by the FIX client| Y| string
1     |  `Account`| The FIX platform account who placed the order. If not secified, then the platform default account is used.| N |string
55| `Symbol` | Fix platform symbol name| Y| string
54| `Side`| Side of the order.| Y|char
60| `TransactTime`| Time at which this order request was initiated|time
 38| `OrderQty`|Order quantity in base units|Y|qty
 40 | `OrdType`| Order type|Y|char
 44| `Price` | Order price|N|price
 59| `TimeInForce`| How long the order remains in effect. | N| char
  10|`CheckSum`|Checksum for message content|Y|string
  
{!ver.md!}
