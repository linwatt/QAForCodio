In previous query examples filtering by property always used exact matching.
```
query("TextView text:'Terminator'")
```
This means find the TextView where the text matches exactly "Terminator". This will not match views with "Terminator2" or event with some additional spaces like " Terminator ".
![](.guides/img/PartialMatching.png)
This is a list of popular robots. Each row has a TextView where the text has the following parts:
1) sequence number (eg."21.")
2) name (eg."Optimus")

Let's start with finding the "Optimus" element
```
 query("TextView text:'Optimus'")
```
The console returns:
```
[]
```
The result is empty because it is looking for exact matches and our TextView contains "Optimus Prime". Instead, we want to match the TextView that contains "Optimus" in the text.

We can use the following syntax:
```
query("TextView {text CONTAINS 'Optimus'}")
```

Other common operations include:
- BEGINSWITH  
prefix, e.g., "label {text BEGINSWITH 'Cell 1'}"
- ENDSWITH 
suffix, e.g., "label {text ENDSWITH '10'}"
- CONTAINS 
substring, e.g., "label {text CONTAINS 'ell'}"
- LIKE
wildcard searches, e.g., "label {text LIKE 'C*ll'}"

