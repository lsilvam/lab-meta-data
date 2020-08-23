here is present the strucuture of the `json` files to record the metadata of the experiments.

The structure of the files as of current version (v1.0) has in mind that for a given `experiment` with a given number of `variables` there are associated values to them -- with some rules, to make a tiddy table with the `R` script:
1. number of entries and variables can be changed as desired
2. each experiment has to have the same variables in different entries
3. each entrie has to have the same number of values -- ideal for longitudinal logs
    - because, when generating a tiddy table all combinations are test
      - __e.g__ when if `var2` is `["0.2", "0.5"]` and `var3` is `["A", "C"]`, then `var2` and `var3` won't be paired, instead they will be combined in four observations; to pair values create another entry (as in the example below).

```json
{  
   "Experiment1_01":[
     {
       "var1" : ["A"],
       "var2" : ["2"],
       "var3" : ["0.2", "0.5"]
     }]
     ,
  "Experiment2_01":[
    {
      "var1" : ["C"],
      "var2" : ["2"],
      "var3" : ["0.3","0.5"]
    }
    ]
}
```

### what not to do
Example of paired experiment, that will not be a tiddy table -- this is an experiment with 4 observations (1*2*2), and not one experiment with 2 observations from `var2` and `var3` -- don't think of this as tables to avoid confusion. 
```json
{  
   "Experiment1_01":[
     {
       "subject" : ["A"],
       "height" : ["1.6", "1.8"],
       "weight" : ["65", "80"]
     }]
}
```