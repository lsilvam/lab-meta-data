---
author: Leonardo Mendes-Silva
ORC-ID: https://orcid.org/0000-0002-5989-637X
GitHub: http://github.com/lsilvam
version: 1.02
created: 20200718
last edit: 20221121
---

# structure of a `.json` file to log cell culture actions

## description

The present files shows the strucutre of the `.json` files designed to log actions done in cell culture. To maintain things simple keep in mind that every entry should be considered as an action executed on a given culture. Also, to keep the format as a standard, below are shown the accepted fields and their respective possible values. 
Each time there is a passage it is advised to create a new file for a given culture, instead of adding n-entries; this way the files are separated and the chances of losing all records are reduced in case of a mistake or bug happens -- and also, for the use of Obsidian/RoamResearch each entry being a new note makes it possible to backlink with `[[foo]]`.
Hope that with this it would be easier to track problems, or good results. 

## guidelines
### IDs

When thawing a vial to start a new culture, the identification ("ID") is the ID in the freezing vial (the label should contain the information about the cell line, passage number, and data of storing).  Example `U2OS P13 ~1M 2022.10.31 leo` that reads:  U2OS cells on Passage number 13, aproximately 1 million, where frozen on 31th of october 2022 by leo. 
- ☝ to avoid confusion the passage number is the number of the passage corresponding to the passage after cells were dissociated before freezing. This way when the cells are thawed the number is the same of that indicated in the vial.
When a field has no data to add, or it is unknown use null e.g passage:`[null]`, or confluency `[null]`

### date

Never leave a data field without entry -- if the date of the original vial(s) is not known use either the **last recorded date** or the **date of thawing** or use an **aproximated date**, but take note of that in the comments. 

### NA and nones and null

Since each field can take different values, *i.e* some fields take numbers while other takes text (or strings) it is better to avoid leaving fields in black; either use the appropriate notation `null` or `none`: `null` for fields that are numbers or `none` for other fields. For example:
- A `passage` is `null`, because the input must be an integer
- A `links_to_experiment` is `none`, because the name of the experiment is a string or an integer
- A `treatment` in `none`, because the number of posibilities are fixed but have multiple options


### lab stage

In `lab_stage` the entry `culture` means that either the medium was changed or that the cells are comming from a passage (which will be distinguishable from medium change because the `dissociation agent` will be filled, as well as the ID will have to change to consider the increased passage number).
When recording a `passage` the fields of `confluency`, `cell_count` and `viability` refer to the mother culture that is  `ID_mother`.

### special cases

If you want to consider culture splits, a new file for each culture/plate/flask needs to be created if they are going to have different ends. For eample, a passage from a T25 to three P60 would be: (1) "..._P60abc" if they will be pooled for the same experiment, but they should have their unnique `ID` if they are going to be use differently; thus, three new entries with their `ID` ending in "..._P60a" + "..._P60b" + "..._P60c", all the the same mother `ID`

patern text keys: 
    `?` -> means characters
    `##` -> means digits, always use two digits e.g. '01' (not just '1') 
    `...` -> means that other values/labels can be added to the pool, or the pool can it self be modified


## Example of possible inputs on how to insert data

ID -> id_cell_line_passage#_user_vial.no. `????_P##_???##` e.g. `20202020_cells_p01_t25`

ID_mother -> as for ID

label -> should be the same or short starment of `ID`

date -> format `YYYYMMDD` e.g. 20200718

cell_type -> `mESC` `iPSC` `...`

cell_line -> `c2koa` `e14t` `la11` `ad2` `...`

passage -> a number ## e.g. `01`; if unknown then use NA

culture_health -> `great` `good` `ok` `bad` `unknown`

confluency -> given as % -- a number in the format ##-### without % e.g. `60`

lab_stage -> `freeze` `thaw` `culture` `discarded` `experiment` `...`

culture_medium -> `DMEM` `GMEM` `DMEM_sup` `GMEM_sup` `iPSC` `mTSER` `E8` `freezing-mix` `...`

extra_supplements -> `2i` `LIF-esgro` `LIF-peptrotech` `LIF-peptrotech` `none` `...`

dissociation_agent -> `trypsin` `accutase` `tryple` `dispase` `mechanic` `none` `...`

cell_count -> cells counted after dissociation or seed from frozen vial, expressed as .10^6 -- `NA` when unkown

viability -> given as % -- a number in the format ##-### without % e.g. `90`

treatment -> `puromycin` `none` `...`

links_to_experiment -> `experiment_name/ID` `none`

mycoplasma_free ->  `yes` `no` `unknown`

tag_notes -> `contamination` `spontaneous_differentiation` `other_issue_see_notebook` `faulty_incubator` `accident` `problems_with_freezing`  `sent_to_collaborator` `sent_to_cell_bank` `handover` `none` `...`

user -> `???` initials of the name of the person that manipulated the cells

comments -> free writing , `none`

picture_filepicture_file_name_name -> if relevant add the name of a file `file_name.jpeg` `none`


## examples
### one entry 

Example of a culture that is  only being maintained with few to none intermediate interventions (for example, medium changes)

```json
{
    "entry01":[
    {
        "ID" : ["20200103_e14t_p02"],
        "ID_mother" : ["20200101_e14t_p01"],
        "label" : ["e14t_p02_t25"],
        "date" : ["20200103"],
        "cell_type" :  ["mESC"],
        "cell_line": ["e14t"],
        "passage" : ["02"],
        "culture_health" : ["good"],
        "lab_stage" : ["culture"],
        "culture_medium" : ["DMEM_sup"],
        "extra_supplements": ["2i"],
        "dissociation_agent" : ["trypsin"],
        "cell_count" : ["1"],
        "viability" : ["90"],
        "treatment" : ["puromycin"],
        "links_to_experiment" : ["experiment_name"],
        "mycoplasma_free" : ["unknown"],
        "tag_notes" : ["none"],
        "user" : ["glados"],
        "comments" : ["the cake is a lie"],
        "picture_file_name": ["file_name.jpeg"]
    }]
}
```
### two entries for same culture

Example for cell culture structure for n-entries for the same flask/culture.
When you want to prepare for an experiment (for example, after a passage the culture might need an antibiotic selection)

```json
{
    "entry01":[
        {
            "ID" : [""],
            "ID_mother" : [""],
            "label" : [""],
            "date" : [""],
            "cell_type" :  [""],
            "cell_line" : [""],
            "passage" : [""],
            "culture_health" : [""],
            "confluency": [""],
            "lab_stage" : [""],
            "culture_medium" : [""],
            "extra_supplements" : [""],
            "dissociation_agent" : [""],
            "cell_count" : [""],
            "viability" : [""],
            "treatment" : [""],
            "links_to_experiment" : [""],
            "mycoplasma_free" : [""],
            "tag_notes" : [""],
            "user" : [""],
            "comments" : [""],
            "picture_file_name": [""]
        }],
    "entry0n":[
        {
            "ID" : [""],
            "ID_mother" : [""],
            "label" : [""],
            "date" : [""],
            "cell_type" :  [""],
            "cell_line" : [""],
            "passage" : [""],
            "culture_health" : [""],
            "confluency": [""],
            "lab_stage" : [""],
            "culture_medium" : [""],
            "extra_supplements" : [""],
            "dissociation_agent" : [""],
            "cell_count" : [""],
            "viability" : [""],
            "treatment" : [""],
            "links_to_experiment" : [""],
            "mycoplasma_free" : [""],
            "tag_notes" : [""],
            "user" : [""],
            "comments" : [""],
            "picture_file_name" : [""]
        }]
}
```

----
version edit logs:
V1.0 -- the examples shown here come from routine tasks in the **Stem Cell Biology Lab** @ Universidade do Algarve -- Centre for Biomedical Research
V1.01 -- review text, replace `NA` for `null`
V1.02 -- typos