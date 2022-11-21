---
author: Leonardo Mendes-Silva
ORC-ID: https://orcid.org/0000-0002-5989-637X
GitHub: http://github.com/lsilvam
version: 1.01
created: 20221119
last edit: 20221121
---

# structure of a `.json` file for reagents and equipment

## description

These json files have the purpose to record only the important information about reagents and equipments used in the laboratory to make it easier to: (1) troubleshoot and (2) to have a record to see when writing a document (e.g. report, paper, or thesis). Therefore, these files should be created evertytime there the (new) reagent or equipment is used. 

This was not thought to be the inventory of the laboratory.

patern text keys: 
    `?` -> means characters
    `##` -> means digits, always use two digits e.g. '01' (not just '1') 
    `...` -> means that other values/labels can be added to the pool, or the pool can it self be modified

## example of possible inputs on how to insert data

### equipment

manufacturer -> `...` brand

model -> `...` model

SN_or_ID -> `...` sometimes there is multiple units of the same equipments, so if the number of the machine matter record it here 

tag_notes -> `none` `working` `faulty` `broken ` `...`

### reagent

manufacturer -> `...` brand

model -> `...` 

lot -> `...` 

tag_notes -> `none` `expDate:YYYYMMDD` `...`

## examples

### equipment

```json
{  
  "centrifuge-01":
     {
      "manufacturer" : ["VWR"],
      "model" : ["CS4"],
      "SN_or_ID" : ["1"],
      "tag_notes":["working"]
    }
}
```
###

```json
{  
  "TRIS-01":
     {
      "manufacturer" : ["ThermoFisher"],
      "reference" : ["17926"],
      "lot" : ["VL99919199"],
      "tag_notes":["expDate:20202020"]
    }
}
```
----
version edit logs:
v1.0 --- created blank
v1.01 --- first 
