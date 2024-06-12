#NewOrderSingle

##Description

A **NewOrderSingle** message is sent by a FIX client to place a new order.

In response, the system sends:

* one or multiple **ExecutionReport** messages to confirm that the order was received (`OrderStatus` = 0)

* one or multiple **ExecutionReport** messages to provide the order execution result

If the order was executed in parts, then for each executed part the system sends an **ExecutionReport** message.

!!! exemp "Example"

    An order is sent to a liquidity pool with two liquidities and executed on both of them.

    **Result**: the FIX client receives the following messages:

    * two **ExecutionReport** messages with `OrdStatus` = 0 (*New*) to confirm that each part of the order was accepted.

    * one **ExecutionReport** message with `OrdStatus` = 1 (*Partially filled*) to confirm the execution of the order part on one liquidity.

    * one **ExecutionReport** message with `OrdStatus` = 2 (*Filled*) to confirm execution of the residual order part on the other liquidity.

##Parameters

|<div style="width:10px">Tag</div>    | <div style="width:100px">Tag name</div>  |   Description | Required| Data type
|-------|-------------|------------------|---------|----------
 ||[Standard Header](StandardHeader.md)| A group of tags that is provided at the beginning of every message sent between the FIX client and the system. For a NewOrderSingle message type, **MsgType**(35 ) = D.
11     |`ClOrdId`     |The order identifier provided by the FIX client.| Y| string
1     |  `Account`| The FIX platform account who placed the order. If not specified, then the platform default account is used.<br>This value must be specified in **Accounts allowed for session** in the system and belong to a group from **Groups allowed for session** in the system; otherwise, the order is rejected.| N |string
55| `Symbol` | Fix platform symbol name| Y| string
54| `Side`| Side of the order.<br> The following sides are supported: <ul><li>1 = Buy</li><li>2 = Sell</li></ul>| Y|char
60| `TransactTime`&nbsp;| Time at which this order request was initiated. <br>Time and date are represented in UTC in YYYMMDD-HH:SS.sss format.|Y|time
 38| `OrderQty`|Order quantity in base units|Y|qty
 40 | `OrdType`| Order type.<br> <ul><li>1 = Market</li><li>2 = Limit</li></ul>|Y|char
 44| `Price` | Order price.<br>Required only for Limit orders (**OrdType** = 2).|N|price
 59| `TimeInForce`| How long the order remains in effect.<br><ul><li>1 = GTC</li><li>2 = IOC</li><li>3 = FOK</li></ul>For market orders (**OrdType** = 1), only 3 and 4 values are valid.<br>For limit orders (**OrdType** = 2), all values are valid. | N| char
  10|`CheckSum`|Checksum for message content|Y|string
  
##Message example

`8=FIX.4.49=17235=D34=1049=Fix_client_Ext52=20221005-04:10:28.79956=Fix_server_Ext11=2841ff99-ed22-42b5-9cda-b533eb4965c738=1000.040=154=255=EURUSD59=460=20221005-04:10:28.79910=093`
