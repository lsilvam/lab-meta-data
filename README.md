# lab metadata

This repository contains different template folders with READMES, and also  `json` files that I created to keep my experimental data organized.
More information about each one in its respective folder "README" file.

## usage

Everytime there is new data from an experiment create a `json` file in the folder of that experiment, and then populate it with the relevant information.
The idea of using `.json` is that it makes it easier to edit a `.json` file in a simple text editor compared to a table. Especially  when there are different obervations for the same sample. Thus the focus in taking notes in the lab can be in the observation and not in writing the same notes with the sample name over and over again. Lastly, `.json` files can be easily edited in in small vertical windows without breaking its structure; unlike tables or `.csv`.

Naming files:
1. pattern "YYYYMMDD_fooo_n0#"
   1. where `foo` is the label of the experiment (or anything else that makes sense for the file to be named)
      1. I used to put the name of the technique, for example, `YYYMMDD_bradford_n01`
         1. if I recorded the experiments continously then it would be something as `..._bradford01_...`
   2. If I found a conflict in name, which is very rare, I would add `_a,b,c...z` to the filename
      1. this way the files would maintain there continous labeling  `..._bradford01a...`
   3. when it is applied, each replicate of the experiment is numbered `..._n0#`
      1. if all replicates are objects in the json file rename to something relatable to the experiment, 
         1. for example `run01` for PCRs or `observation01` for microscopy 

More about the background on using `.json` files [here](02_templates_as_.json/00-template-backbone/00README_json.md)

Jump to:
- [cell culture](02_templates_as_.json/01-template-cell_culture/00README-metadata_cell_culture.md)
- [gel and blots imager](02_templates_as_.json/02-template-chemidoc/00README-metadata_chemidoc.md) 
- [microscopy](02_templates_as_.json/03-template-microscopy/00README-metadata_microscopy.md)
- [reagent and equipment](02_templates_as_.json/04-template-lab_reagent_and_equipment/00README-metadata_reagents_and_equipment.md)

# disclaimer
These are files that I created to help me maintain my information organized and sharable with future me. Most likely there is a better way to do this. Anyway if you find them useful feel free to used/edit them.