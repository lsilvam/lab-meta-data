---
author: Leonardo Mendes-Silva
ORC-ID: https://orcid.org/0000-0002-5989-637X
GitHub: http://github.com/lsilvam
version: 1.02
created: 20201007
last edit: 202211121
---

# structure of a `.json` file to imager files

## description

The present file shows the strucutre of the `.json` files designed to log images of gels or blots aquired in one imager (e.g. Chemidoc). To maintain things simple  images aquired for an experiment should have a meta file associated; *i.e.*, for example, for quality control after western blot transfer SDS-PAGE and total protein images. Also, to keep the format as a standard below are shown the accepted fields and their respective possible values. 

For sake of simplicity it was considered to use just one template for all the aquisitions type: agarose gels, SDS-PAGE, and blots. Therefore, to clarify what to consider for the electrophoresis run settings:
- agarose gels: electrophoresis settings, only one option
- blots: transfer electrophoresis settings 
Although, there is just one file for all the possible aquisition modes it is of course possible to break this templates into three new templates for each aquisition mode, but at the time it was not deemed necessary.

patern text keys: 
    `?` -> means characters
    `##` -> means digits, always use two digits e.g. '01' (not just '1') 
    `...` -> means that other values/labels can be added to the pool, or the pool can it self be modified

## Example of possible inputs on how to insert data

date -> `YYYYMMDD` 

application -> `nucleic_acids` `protein_gels` `blots` `...`

imager_protocol -> `protocal_name` `...`

experiment_name -> `???` `...`

experiment_replicate -> `##` number of the experiment replicate

gel_percentage -> `##` `##00##` `null` given as % (percentage) of the gel e.g. `12` or if it has gradient `40012`

target_molecule -> `DNA` `RNA` `total_protein` `...` or target protein e.g. `p53`

stain_labeling -> `GreenSafe` `SafeRed` `Coomassie` `PounceauS` `HRP` `...`

run_duration -> `###` `null` expressed in minutes (min) 

run_voltage -> `###` `null` expressed in Voltage (V)

run_amperage -> `###` `null` expressed in Ampere (A)

lanes_content -> `???` free text

ladders -> label of the ladder used `Brand$product_name` `...` `none` e.g. `ThermoFisher$PageRuler` 

blocking_solution -> `##%_blokingAgent_buffer_detergent_##%"` `...` `none` e.g `5%_milk_TBS_Tween_0.1%"`

antibody_solution -> `##%_blokingAgent_buffer_detergent_##%"` `...` `none`

antibody_primary -> `brand$reference` `...` `none`

antibody_secondary -> `brand$reference` `...` `none`

antibody_primary_dilution -> `####` `null` consider diluted 1-to-x e.g `1000` or 1:1000

antibody_secondary_dilution -> `####` `null` consider diluted 1-to-x e.g `500` or 1:500

raw_file_name_gel -> `???`, `none`

raw_file_name_blot -> `???`, `none`

raw_file_name_colorimetric -> `???`, `none`

raw_file_name_loading_control -> `???`, `none`

raw_file_name_coomassie -> `???`, `none`    

comments -> free writing `???`, `none`

user -> `???` initials of the name of the person that manipulated the cells

## examples

```json
{  
    "chemidoc_(experiment01)":[
      {
        "date": ["20221031"],
        "application": ["Blot"],
        "imager_protocol" : ["HiRes"],
        "experiment_name": ["test_experiment"],
        "experiment_replicate": ["01"],
        "gel_percentage": ["9-12"],
        "target_molecule" : ["total_protein"],
        "stain_labeling": ["Coomassie"],
        "run_duration": [90],
        "run_voltage": [100],
        "run_amperage": [null],
        "lanes_content" : [
            "00ladder",
            "01control",
            "02treated"
        ],
        "ladders": ["ThermoFisher$PageRuler"],
        "blocking_solution": ["none"],
        "antibody_solution": ["none"],
        "antibody_primary":[null],
        "antibody_secondary":[null],
        "antibody_primary_dilution:":[null],
        "antibody_secondary_dilution":[null],
        "raw_file_name_gel": ["20221031_my_first_experiment.scn"],
        "raw_file_name_blot": ["none"],
        "raw_file_name_colorimetric": ["none"],
        "raw_file_name_loading_control": ["none"],  
        "comments":[""],
        "user": [""]
      }
    ]
 }
 ```
----
version edit logs:
v1.0 -- created blank
v1.01 -- edited to add material, remove line of " raw_file_name_coomassie" because it adds redundancy
v1.02 -- review and typos