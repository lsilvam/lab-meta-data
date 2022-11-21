---
 author:Leonardo Mendes-Silva
 ORC-ID: https://orcid.org/0000-0002-5989-637X
 GitHub: http://github.com/lsilvam
version: 1.0
created: 20201114
last edit: 20221121
---

# structure of a `.json` file for microscopy files

## description

The present files shows the strucutre of the `.json` files designed to log experiment data of images aquired using a microscope.To maintain things simple consider images aquired during a microspcopy session to be in just one file. Also, to keep the format as a standard below are shown the accepted fields and their respective possible values. 

 For sake of simplicity it was considered that images from the same sample (same slide area) should be saved in the same object, and to identify the slide area there is the variable `slide_id`. 
 For example, one slide can have two cover slips each with one sample for the control and another for the treated. In this case the metadata file would have two objects for each cover slip that correspond to each treatement.

 To take note of the filename for each image follow the pattern `outputFile-thisIsaComment-StackYesOrNo`. The idea is that by doing this it is easier to take note when we are at the microscope aquiring images, and the `-` allows for easy split should we need to make a table with this data. Thus, for each image, since most softwares by deafault save continuos numbering in the files the `outpuFile` usually is something like `foo03...foo10`. Then in `thisIsaComment` is intended to give a comment on the image aquired. For example, I usually write the size of the colony. Lastly, the `StackYesorNo` is to mention if the file is a stack of images. 
 - side note: this last item could be replace with other possible ways of aquiring images. For example, it could be: Snap, Stack, Tile, Projection, etc. But since for my use case I only used stacks, it was simpler.

The ideia of this metadata files is that the file can be prepared in advance of the microscopy session, so that only the `raw_files_comment_zStackYN` needs to be filled---mostly to save time and to avoid forgetting important aquisitions. 

patern text keys: 
    `?` -> means characters
    `##` -> means digits, always use two digits e.g. '01' (not just '1') 
    `...` -> means that other values/labels can be added to the pool, or the pool can it self be modified

## example of possible inputs on how to insert data

date -> `YYYYMMDD` 

time -> `HHMMSS` 

microscope -> `brand$model` 

aquisition_mode -> `RL` `FL` `PC` 

fluorophores_channels -> `DAPI` `A488` `A594` `...`

exposure_GainMaster -> `auto` `###` 

light_intensity -> `min` `max` `auto` `...`

objective -> `4x` `10x` `20x` `40x` `63x` `100x`

zoom -> `1.4` `#.#`

frame_dim -> `###x###`

links_to_experiment -> `???` `...`

target_molecule -> `???` `...`

antibody_primary_ref -> `brand$ref`

antibody_secondary_ref -> `brand$ref`

antibody_primary_dilution -> `250` `500` `1000` `2500` `5000` `...`

antibody_secondary_dilution -> `250` `500` `1000` `2500` `5000` `...`

blocking_solution -> `##%_blokingAgent_buffer_detergent_##%"` `...` 
`none`

antibody_solution -> `##%_blokingAgent_buffer_detergent_##%"` `...` `none`

slide_id -> `???` `...` 

biological_group -> `control` `treated_a` `treated_b`  `...`

raw_files_comment_zStackYN -> `outputFile-thisIsaComment-StackYesOrNo` e.g `snap0001-perfectColony-N`

tag_notes -> `focus on red channel` `focus on green channel` `focus on blue channel` `none` `...`

comments -> free writing `???`, `none`

user -> `???` initials of the name of the person that manipulated the cells

microscope_issues -> free writing `???` log detected issues during aquisition

## examples

```json
{  
    "Experiment1_n01_obs01":[
        {
        "date": ["20202020"],
        "time": ["2400"],
        "microscope" : ["Zeiss$ImagerZ2"],
        "aquisition_mode": ["RL"],
        "fluorophores_channels": ["DAPI","A488"],
        "exposure_GainMaster": ["auto"],
        "light_intensity": ["auto"],
        "objective":["20"],
        "zoom":["1"],
        "frame_dim": ["512x512"],
        "links_to_experiment":["exp_example"],
        "target_molecule": ["DNA", "BRAC1"],
        "antibody_primary_ref":["ThermoFisher$????"],
        "antibody_secondary_ref":["Sigma$????"],
        "antibody_primary_dilution":["500"], 
        "antibody_secondary_dilution":["5000"],
        "blocking_solution": ["5%_BSA_TBS_Tween20_0.1%"],
        "antibody_solution": ["1%_BSA_TBS_Tween20_0.1%"],
        "slide_id" : ["slide01a"],
        "biological_group": ["control"],
        "raw_files_comment_zStackYN": [
            "snap01-foo-N",
            "snap02-foo-N",
            "snap03-foo-N"
        ],
        "tag_notes" : ["none"],
        "comments" : ["none"],
        "user" : ["LS"],
        "microscope_issues": ["none"]
        }
    ] ,
    "Experiment1_n01_obs02":[
        {
        "date": ["20202020"],
        "time": ["2415"],
        "microscope" : ["Zeiss$ImagerZ2"],
        "aquisition_mode": ["RL"],
        "fluorophores_channels": ["DAPI","A488"],
        "exposure_GainMaster": ["auto"],
        "light_intensity": ["auto"],
        "objective":["20"],
        "zoom":["1"],
        "frame_dim": ["512x512"],
        "links_to_experiment":["exp_example"],
        "target_molecule": ["DNA", "BRAC1"],
        "antibody_primary_ref":["ThermoFisher$????"],
        "antibody_secondary_ref":["Sigma$????"],
        "antibody_primary_dilution":["500"], 
        "antibody_secondary_dilution":["5000"],
        "blocking_solution": ["5%_BSA_TBS_Tween20_0.1%"],
        "antibody_solution": ["1%_BSA_TBS_Tween20_0.1%"],
        "slide_id" : ["slide01b"],
        "biological_group": ["treated"],
        "raw_files_comment_zStackYN": [
            "snap04-foo-N",
            "snap05-foo-N",
            "snap06-foo-N"
        ],
        "tag_notes" : ["none"],
        "comments" : ["none"],
        "user" : ["LS"],
        "microscope_issues": ["software restart necessary between snap04 and snap05"]
        }
    ]
}

```

---
version edit logs:
v1.0 --- first edit
v1.01 --- review and typos