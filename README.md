# Salmonid_MHC_classifier
IPD-MHC classifier for Salmonids


## Dependencies
Muscle, emboss (transep and water tools) which can installed with Conda as below
```bash
$ conda install muscle emboss
```

Uses os, sys, subprocess, Bio and ete3 packages in python.
First three packages are available within python while the last two can be installed with Conda as below
```bash
$ conda install -c conda-forge biopython ete3 
```

Current version uses already downloaded data from IPD-MHC and the folder 'data' from github has to be downloaded and placed at the same place as the python file. This will change soon when the API access for IPD-MHC becomes publically available.

## Initiation
```bash
$ python salmonid_mhc_classifier.py [input.fa] [output_folder] [report.txt] [Db_name]
```  

input.fa: Sequences in fasta format  
output_folder: Folder for output data
report.txt: Name for the output report file  
Db_name: SASA-DAA, SASA-DAB, SASA-UAB  

## Execution
Output files are saved to the [output_folder] as specified in the 
Each fasta record in the [input.fa] will be processed one at a time  
  Output: NAME.fa  
  
Nucleotide record is translated into peptide  
  Output: NAME.aa  
  
Nucleotide record is aligned with the relevant [Db_name] using muscle  
  Output: NAME_muscle_output.tree.txt and NAME_muscle_output.aln.txt  
  
Muscle tree is converted to png using ete3  
  Output: NAME_muscle_output.tree.png  
  
Sibligns in two neighbouring clades are extracted using ete3
  Output: Detail in [report.txt]  
  
Local alignment in performed between the query and each of the siblings at nucleotide and peptide level using Water  
  Output NAME_SIBLINGS_water_nt.txt and aa_txt  
  
Sequence similarity and identity information from Water are included in the report  
  Output: Detail in [report.txt]  
  
## Output
Example output is provide in the folder output_example
