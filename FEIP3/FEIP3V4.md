```
FEIP3: CID
Version: 4
Language: en-US
Author: C_armX, Deisler-JJ_Sboy
Status: draft
Created date: 2021-02-5
File hash: "HEX Hash"
TXid: 
```

# FEIP3V4_CID(en-US)

## Contents
[Introduction](#Introduction)

[General rules of FEIP type protocols](#general_rules_of_feip_type_protocols)

[Rules specific to this protocol](#rules_specific_to_this_protocol)

[Register Example](#Register_example)

[Unregister Example](#Unregister_example)



## Introduction

```
Type: FEIP
SerialNumber: 3
ProtocolName: CID
VersionNumber: 4
Description : Register or unregister a human friendly identity for an address.
Author: C_armX, Deisler-JJ_Sboy
Language: en-US
tags: FEIP, CID, Identity, human friendly, basic protocol
preVersionHash:"921ee337239ea34a1434c91bb8221b979f2c956b512a6f1c0ef89be6d342d933"
Status : Draft
CreatedDate: 2021-02-05
```

## General rules of FEIP type protocols

1. The importent data is written in OP_RETURN for public witness.

2. The max size of OP_RETURN : 4096 bytes

3. Format : Json

4. Encoding : utf-8

5. The "head" specifies the unique protocol file which defines other data.


## Rules specific to this protocol

1. CID(Crypto Identity)：“name"+"_"+suffix, e.g. CY_vpAv.

2. Suffix：The last four letters of the address. If the new CID is the same as any CID that has been registered, increase the length of suffix until the new CID is unique, e.g. CY_kvpAv.

3. User can unregister CID by leaving all fields blank except the "head" fields.

4. Once a CID is registered by an address, it cannot be registered by other addresses, even if the CID has been unregistered.

5. An address can re-register its unregistered CID.



## OP_RETURN
The OP_RETURN of which contains the data as follows:

|field number|fieldname|type|lenth|content|required|
|:----|:----|:----|:----|:----|:----|
|head|type|String|4|Fixed: "FEIP"<br>Case insensitive|Y|
|head|serialNumber|int|1|Fixed: 3|Y|
|head|versionNumber|int|1|Fixed: 4|Y|
|head|protocolName:|String|3|Fixed: "CID"<br>Case insensitive|Y|
|head|fileHash|hex|32|Sha256 value of this file|Y|
|1|name|string|32|Nick name given by the user|N
|2|url|string|256|The URL showing the details of the CID|N
|3|noticeFee|double|16|The lowest FCH payment that the user is willing to be notified|N

## Register Example
```
Address: FPL44YJRwPdd2ipziFvqq6y2tw4VnVvpAv
CID：CY_vpAv
OP_RETURN content:

{
    head:{
        type: "FEIP",
        serialNumber: 3,
        versionNumber: 4,
        protocolName: "CID",
        fileHash: "/* The file hash of FEIP3V4 */"
    },
    name: "CY",
    tags: [“education“, ”strategic design“, ”economic model”],
    url: "https://www.zhimidaxue.com",
    noticeFee: 0.01
}
```

## Unregister Example
```

Address: FPL44YJRwPdd2ipziFvqq6y2tw4VnVvpAv

OP_RETURN content:

{
    head:{
        type: "FEIP",
        serialNumber: 3,
        versionNumber: 4,
        protocolName: "CID",
        fileHash: "/* The file hash of FEIP3V4 */"
    }
}

```
