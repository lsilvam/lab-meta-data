Here are the guidelines for organizing experiments from the experimental design to the publication ready figures/table.

The workflow consisits in directory with 8 folders, each one with a purpose,  listed below:

- ./00raw_data
    - this folder should contain the raw data files from the experiment, that is data without /n
    any pre-processing directly from the machine.
    - the different replicate experiments should be in here. 
    - keep in mind that "data" are any files coming from the measuring device
        - do not forget that an image from a microscope is data
    - a meta data file as `.json` should be in the folder (templates for this on GitHub/lsilvam/lab-meta-data)
    
- ./01experimental-design
    - this folder should contain the files with the experimental design. There are no restriction /n
    here since the possibility of experimental design is quite vast. 

- ./02preprocessed_data
    - this folder should contain the preprocessed files: a copy of raw files, or combination of data
    from different raw files
    - any changes to the data should be logged in the file `README-preprocessing_data.txt`
    - in this folder one file (or more) should have data in tidy format ready to export to `.csv` (for sharing)

- ./03data_analysis
    - sometimes the data analysis is quite complex, and there is a requirement to use speficic software or script that will 
    treat and analyze the data --- place all the editable files from the software here
        - *e.g.* ZenBlue, GraphPad, ImageJ, CellProfiller 
        - if the files are in another directory/folder add a shortcut here, and save the directory in the `README` file for the directories with scripts

- ./04outputs
    - this folder should contain the outputs of the analysis such **figures** and **tables**
        - tip: create different folder to save different variantions of the analysis and label with versions (that should match the result analysis as well)

- ./05short_report
    - this folder contains a Word template to write a brief report to work as a deliverable with 
    special focus in benchwork; more detailed discussion should be in the next folder

- ./06pubr
    - in this folder should be a draft of a publication ready images/tables related to this experiments
    - ./01figures
        - this folder should contain both the original figures and the publication ready figures
            - preferably as `.svg` or `.png`, or `.tiff` if used for print
    - ./02supplementary_data
        - this folder should contain supplemntary information, including the  `.csv` files corresponding to each
        figure or table presented
        - also include `.zip` of the raw data from more complex techniques like sequencing

- ./notes
    - this folder should contain any relevant notes taken during the experiment, and that includes:
        - pictures
        - scanned protocols
        - scanned labjournal
    - the files should be log in the `README-notes.txt`

Other considerations:
- everytime that is required 
    - add a `README` file to each folder
    - add a list of all the files in the folder in a `README-listFiles` 




