# Background
Here are present the strucuture of the `json` files to record the metadata of the experiments.

The structure of the files as of current version (v1.0) has in mind that for a given `experiment` with a given number of `variables` there are associated values to them -- with some rules, to make a tiddy table using a `.R` script:
1. number of entries and variables can be changed as desired
2. each experiment has to have the same variables in different entries
3. each entry has to have the same number of values -- ideal for longitudinal logs
    - because, when generating a tiddy table all combinations are tested
      - *e.g*  if `var2` is `["0.2", "0.5"]` and `var3` is `["A", "C"]`, then `var2` and `var3` won't be paired, instead they will be combined in four observations; to pair values create another entry (as in the example below).

In the following somplified example: for two different experiments replicates `01`and `02` lets say that two samples (`var1`) `A` and `C` were measured at one time point (`var2`) two times (in `var3`).

```json
{  
   "Experiment01_01":[
     {
       "var1" : ["A"],
       "var2" : ["2"],
       "var3" : ["0.2", "0.5"]
     }]
     ,
  "Experiment02_01":[
    {
      "var1" : ["C"],
      "var2" : ["2"],
      "var3" : ["0.3","0.5"]
    }
    ]
}
```
## what not to do

Example of a paired experiment, that will not be a tiddy table -- this is an experiment with 2 observations (`time_point`) each with 2 measured variables  `var2` (*height*) and `var3` (*weight*). 
So far I could not find a way to make a tiddy tible using this structure, in other words, one dataframe with two rows for each time point, and columns for the four variables. 

```json
{  
   "Experiment1_01":[
     {
       "subject" : ["A"],
       "time_point" : ["d0", "d1"],
       "height" : ["1.6", "1.8"],
       "weight" : ["65", "80"]
     }]
}
```

Anyway, this kind of logging in the wet lab might result in input errors and confusions because the previous entry could be edited by mistake. Thus, using one entry for each day would make more sense because the entry is clean form the start. Thefore, this would be how 
this data could be logged: 

```json
{  
   "Experiment1_01":[
     {
       "subject" : ["A"],
       "time_point" : ["d0"],
       "height" : ["1.6"],
       "weight" : ["65"]
     }],
    "Experiment1_02": [
      {
       "subject" : ["A"],
       "time_point" : ["d1"],
       "height" : ["1.8"],
       "weight" : ["80"]
    }],     
}
```