---
 author:Leonardo Mendes-Silva
 ORC-ID: https://orcid.org/0000-0002-5989-637X
 GitHub: http://github.com/lsilvam
version: 1.0
created: 20201114
last edit: 20221115
---

# structure of a `.json` file for microscopy files

## description

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
blocking_solution -> `##%_blokingAgent_buffer_detergent_##%"` `...` `none`
antibody_solution -> `##%_blokingAgent_buffer_detergent_##%"` `...` `none`
slide_id -> `???` `...` 
biological_group -> `control` `treated_a` `treated_b`  `...`
raw_files_comment_zStackYN -> `outputFile-thisIsaComment-YesOrNo` e.g `snap0001-perfectColony-N`
tag_notes -> `focus on red channel` `focus on green channel` `focus on blue channel` `...`
comments -> free writing `???`, `none`
user -> `???` initials of the name of the person that manipulated the cells
microscope_issues -> free writing `???` log detected issues during aquisition

## examples

```json


```



---
version edit logs:
v1.0 --- first edit