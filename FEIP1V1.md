# FEIP1V1

## Introduction
General protocol and relase process of FEIPs.

## General protocol of FEIPs

### Total size
The total size of OP_RETURN is : 220 bytes.

### Field seperator
'|'

### Encoding
utf-8

### Name
"FEIP" + FEIP number + "V" + Version number

e.g.: `FEIP1V1`

### Protocol
|Field number|Field Name|Type|Length|Content|
|:--:|:--:|:--:|:----:|:------|
|1|Protocol type|string|4|Fixed: "FEIP")|
|2|FEIP number|integer|1-4|begins with 1)|
|3|Version|String|2-4|e.g.: V1(version number begins with "V1")|
|4|Body|bytes|||
 
## Release process

## Example

## Latest version
V1

## Author
freefch, Deisler-JJ, hbyscpp

## Hash
