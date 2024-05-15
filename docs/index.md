# Application messages


Some  of the application messages contain **repeating tag groups**.

A repeating tag group consists of repeating tag sets and starts with a tag that specifies the number of repeating sets. 

For example, there is a **NoPositions** repeating group, which consists of the **NoPositions** tag that specifies the number of repeating tag sets and **PosType**, **LongQty**, and **ShortQty** tags that repeat. If **NoPositions** = 2, then in a FIX message,the **NoPositions** repeating group looks as follows:

**NoPositions**=2 PosType LongType ShortType PosType LongType ShortType
 
In the FIX message descriptions, a tag that repeats in a repeating group is marked as 'Repeating tag'.