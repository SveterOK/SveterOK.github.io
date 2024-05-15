#Standard header

Tag| Tag Name| Description| Required| Data Type
---|----------|-----------|----------|----------
8| `BeginString`|The FIX version number| Y| string
9| `BodyLength`| Length of the FIX message|Y|string
35| `MsgType`| Type of the message| Y|string
34| `MsgSeqNum`|A unique sequence number for the message within the current FIX session.|Y|SeqNum
49|`SenderCompID`| Message sender identifier| Y|string  
52|`SendingTime`| Time at which the message was sent.|Y|UTCTimeStamp
56|`TargetCompID`|Message receiver identifier|Y string
43|`PossDupFlag`|Indicator that the message with this sequence number is possible retransmitted|Y|boolean
122|`OrigSendingTime`|Date and time when the message was originally sent.|N|UTCTImestamp