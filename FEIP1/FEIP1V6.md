```
FEIP1 : FreeProtocolSystem
Version: 6
Language: en-US
Author: C_armX, Deisler-JJ_Sboy
Status: draft
Created date: 2021-01-30
File hash: "HEX Hash"
TXid: 
```

# FEIP1V6_FreeProtocolSystem(en-US)

## Contents
[Introduction](#Introduction)

[General rules of FEIP type protocols](#General_rules_of_FEIP_type_protocols)

[Rules specific to this protocol](#Rules_specific_to_this_protocol)

[Register](#Register)

[Unregister](#Unregister)

[Evaluate](#Evaluate)



## Introduction

```
Type: FEIP
SerialNumber: 1
ProtocolName: FreeProtocolSystem
VersionNumber: 6
Description : Register, unregister or evaluate protocols freely by writing data in OP_RETURN.
Language: en-US
Author: C_armX, Deisler-JJ_Sboy
Status : Draft
CreatedDate: 2021-01-30
```

## General rules of FEIP type protocols

1. The key data is written in OP_RETURN for public witness.

2. The max size of OP_RETURN : 4096 bytes

3. Format : Json

4. Encoding : utf-8

5. The "head" specifies the unique protocol file which defines other data.


## Rules specific to this protocol

1. Title in protocol text: type + serialNumber + "V" + versionNumber +'_' + protocolName + '(' + language + ')', e.g: FEIP1V6_FreeProtocolSystem(en-US)

2. Anyone can send a transaction to register a protocol by writing data in the format given by [Register](#register) .

3. Anyone can only unregister his/her own protocols by writing data in the format given by [Unregister](#unregister).

4. Anyone can evaluate any protocol by writing data in the format given by [Evaluate](#evaluate).


## Register
Register a protocol by send a transaction, the OP_RETURN of which contains the data as follows:

|field number|fieldname|type|lenth|content|required|
|:----|:----|:----|:----|:----|:----|
|head|type|String|4|Fixed: "FEIP"<br>Case insensitive|Y|
|head|serialNumber|int|1|Fixed: 1|Y|
|head|versionNumber|int|1|Fixed: 6|Y|
|head|protocolName:|int|18|Fixed: "FreeProtocolSystem"<br>Case insensitive|Y|
|head|fileHash|hex|32|Sha256 value of this file|Y|
|1|type|String|8|Type of the protocol being registered.|N|
|2|serialNumber|String|8|Serial number of the protocol being registered., counting from 1.|N|
|3|versionNumber|String|4|Version number of the protocol being registered. counting from 1.|N|
|4|protocolName|String|64|Name of the protocol being registered..|N|
|5|description|String|256|Short descriptionof the protocol being registered..|N|
|6|authors|String array|128|FCH addresses of the authors of the protocol being registered..|N|
|7|fileHash|hex|64|The sha256 value of the protocol file being registered..<br>|Y|
|8|language|String|5|The language of the protocol beingregistered., formated with i18n(internationalization),such as "en-US".|N|
|9|operation|String|8|Fixed: "register"<br>Case insensitive|Y|
|10|tags|String array|    |Tags about the protocol being registered.|N|
|11|preVersionHash|hex|64|“protocolFileHash” ofprevious version|N|
|12|storageProvider|String array|128|FCH addresses of storage service providers|N|

**Register Example:**
```
{
    head:{
        type: "FEIP",
        serialNumber: 1,
        versionNumber: 6,
        protocolName: "FreeProtocolSystem",
        fileHash: "/* The file hash of FEIP1V6 */"
    },
    type: FEIP,
    serialNumber: 3,
    versionNumber: 2,
    protocolNmae: "CID",
	description: "通过私钥签名交易，为相应地址及公钥定义⼀个易,于识别记忆的昵称和易于理解和检索的标签。”,
	authors: ["CY_vpAv","Deisler-JJ_Sboy",”Satoshi_Uat4“],
	fileHash: "b1e127ffdebffa0dc46a008ee9792541f4aa823550a1218b3583aa66c8da541d",
    language: "zh-CN",
    operation: "register",
    tags: [”identity“,”身份“，”基础协议“],
    preVersionHash:"921ee337239ea34a1434c91bb8221b979f2c956b512a6f1c0ef89be6d342d933",
    storageProvider:{"FJeRnehc2VvRMV3wRF2AtiXDVnaKnmnZhp","FT2fWcCEoiwiXtcxf8AxySG3waPFihMFJV"}
}
```

## Unregister
Unregister a protocol by send a transaction, the OP_RETURN of which contains the data as follows:

|field number|field name|type|lenth|content|required|
|:----|:----|:----|:----|:----|:----|
|head|type|String|4|Fixed: "FEIP"<br>Case insensitive|Y|
|head|serialNumber|int|1|Fixed: 1|Y|
|head|versionNumber|int|1|Fixed: 6||
|head|protocolName|int|18|Fixed: "FreeProtocolSystem"<br>Case insensitive|Y|
|head|fileHash|hex|32|Sha256 value of this file|Y|
|1|fileHash|hex|64|The sha256 value of the protocol file being unregistered.|Y|
|2|operation|String|8|Fixed: "unregister"<br>Case insensitive|Y|


**Unregister Example:**
```
{
	head:{
        type: "FEIP",
        serialNumber: 1,
        versionNumber: 6,
        protocolName: "FreeProtocolSystem",
        fileHash: "It can't be generated yet"
	},

	fileHash: "b1e127ffdebffa0dc46a008ee9792541f4aa823550a1218b3583aa66c8da541d",
	operation: ”unregister“
}
```

## Evaluate

|field number|field name|type|lenth|content and rules|required|
|:----|:----|:----|:----|:----|:----|
|head|type|String|4|Fixed: "FEIP"<br>Case insensitive|Y|
|head|serialNumber|int|1|Fixed: 1|Y|
|head|versionNumber|int|1|Fixed: 6|    |
|head|protocolName|int|18|Fixed: "FreeProtocolSystem"<br>Case insensitive|Y|
|head|fileHash|hex|32|Sha256 value of this file|Y|
|1|fileHash|hex|64|The sha256 value of the protocol file being evaluated.|Y|
|2|operation|String|8|Fixed: "evaluate"<br>Case insensitive|Y|
|3|evaluation|int|1|1 or -1|Y|

**Evaluate Example:**
```
{
	head:{
        type: "FEIP",
        serialNumber: 1,
        versionNumber: 6,
        protocolName:"FreeProtocolSystem",
        fileHash: "It can't be generated yet"
	},
	fileHash: "b1e127ffdebffa0dc46a008ee9792541f4aa823550a1218b3583aa66c8da541d",
	operation: "evaluate",
	evaluation: 1
}
```
