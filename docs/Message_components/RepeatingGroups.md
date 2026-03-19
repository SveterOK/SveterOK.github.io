# Repeating groups


Some messages contain **repeating tag groups**.

A repeating tag group consists of repeating sets of tags and starts with a tag that specifies the number of repeating sets. 

!!! exemp "Example"

    There is a `NoPositions` repeating group, which consists of the `NoPositions` tag that specifies the number of repeating sets of `PosType`, `LongQty`, and `ShortQty` tags. If `NoPositions` = 2, then in a FIX message, the `NoPositions` repeating group looks as follows:

    `NoPositions=2 PosType=1 LongType=1 ShortType=1 PosType=1 LongType=1 ShortType=1`
 
    In a FIX message description a tag that repeats is marked as 'Repeating tag'.    

