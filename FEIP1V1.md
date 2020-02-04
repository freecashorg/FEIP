# FEIP1V1

## Introduction
General protocol and relase process of FEIPs.

## General protocol of FEIPs

### Protocol
|Field number|Field Name|Type|Length|Content|
|:--:|:--:|:--:|:----:|:------|
|1|Protocol type|bytes|4|Fixed: 0x46,0x45,0x49,0x50(utf-8 of "FEIP")|
|2|FEIP number|bytes|1-4|0x31 (utf-8 of "1")|
|3|Version|bytes|2-4|e.g.: V1(version number begins with "V1")|
|4|Body|bytes|||

### Total size
The total size of OP_RETURN is : 220 bytes.

### Field seperator
'|'

### Encoding
utf-8

### Name
FEIP + FEIP numbser + V + Version

## Release process

## Example

## Latest version
V1

## Author
freefch, Deisler-JJ, hbyscpp

## Hash
