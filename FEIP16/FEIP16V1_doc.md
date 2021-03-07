```
FEIP16: Evaluation
Version: 1
Language: en-US
Author: C_armX, Deisler-JJ_Sboy，Free_Cash
Status: draft
Created date: 2021-02-5
LastModifiedDate：2021-03-06
File hash: "unkonw now"
TXid: 
```

# FEIP16V1_Evaluation(en-US)

## Contents
[Introduction](#introduction)

[General rules of FEIP type protocols](#general-rules-of-feip-type-protocols)

[Rules specific to this protocol](#rules-specific-to-this-protocol)

[Example of positive evaluation](#example-of-positive-evaluation)

[Example of negative evaluation](#example-of-negative-evaluation)


## Introduction

```
ProtocolType: FEIP
SerialNumber: 16
ProtocolName: Evaluation
VersionNumber: 1
Description : Evaluate an CID to increase/decrease its reputation.
Author: C_armX, Deisler-JJ_Sboy，Free_Cash
Language: en-US
Tags: FEIP, Evaluation, Reputation, basic protocol
PreVersionHash:"unkonw"
```

## General rules of FEIP type protocols

1. Write important data in OP_RETURN for public witness.

2. The max size of OP_RETURN : 4096 bytes

3. Format : Json

4. Encoding : utf-8


## Rules specific to this protocol

1. FEIP16 provides a way for an CID to evaluate other CIDs.
2. Making evaluation consumes CoinDays.
3. The evaluation can be Positive or Negative, and The measure unit of an evaluation is CoinDays. For example: "100 CoinDays Negative evaluation" can be marked as "-100CD",and "88 CoinDays positive evaluation" can be marked as "88CD" or "+88CD".
4. The quantity of an evaluation is the CoinDays consumed in the transaction.
5. The evaluator should put the address of evaluatee at first output.

## OP_RETURN
The OP_RETURN of which contains the data as follows:

|field number|fieldname|type|lenth|content|required|
|:----|:----|:----|:----|:----|:----|
|1|type|String|4|Fixed: "FEIP"<br>Case insensitive|Y|
|2|sn|int|1|Serial number<br>Fixed: 16|Y|
|3|version|int|1|Fixed: 1|Y|
|4|name|String|3|Fixed: "Evaluation"<br>Case insensitive|N|
|5|hash|hex|32|Sha256 value of this protocol file|N|
|6|data.sign|char|Fixed: 1|"+" or "-"|Y|
|7|data.tags|string array|||N|


## Example of positive evaluation
```

Input address: FPL44YJRwPdd2ipziFvqq6y2tw4VnVvpAv
First output address: FS2AWq1dgdhCpNTwqfBbMBBJGNNj1LSboy

OP_RETURN content:
{
    "type": "FEIP",
    "sn": 16,
    "version": 1,
    "Name": "Evaluation",
    "Hash": "unkonw",
    "data":{
        "sign": "+",
        "tags": ["efficient","energetic"]
        }
}

```

## Example of negative evaluation
```

Input address: FPL44YJRwPdd2ipziFvqq6y2tw4VnVvpAv
First output address: FS2AWq1dgdhCpNTwqfBbMBBJGNNj1LSboy

OP_RETURN content:

{
    "type": "FEIP",
    "sn": 3,
    "version": 4,
    "Name": "Evaluation",
    "Hash": "unkonw",
    "data":{
        "sign": "-",
        "tags": ["inefficient","lazy"]
        }
}

```