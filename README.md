# Dictionarytool
tsv/yaml interconverter tools
### Modifying nodes_tsv

#### Links and link subgroups
Every link must contain one of "name", "backref", "label", "target" and "multiplicity." Failure to enter one of these fields will result in an error. If a subgroup is present, it must be listed first in each cell. A subgroup is specified using brackets. ````[name1, name2]```` is an example of an entry in the link name column that specifies the names of two links that belong to a subgroup. The names are seperated by a comma. If there is a subgroup and a nongroup link, it must be notated with the subgroup first, ````[name1, name2], name3````. 

### Modifying variables_tsv

### Forbidden characters
Only ASCII characters are allowed. 
All values are not to be placed in quotations, however quotations within a field are allowed. Example:
Valid: And the person said, "I feel great" at the end of the exam.
Invalid: "And the person said, "I feel great" at the end of the exam."
Invalid: "And the person said, I feel great at the end of the exam."

#### Terms
Entries in the terms column are references to the location of the term definition. If more than one reference is used, they are comma separated. 

#### Enums / Options with definitions
Enumerations are listed in the options column(s). Each cell should hold less than 32000 characters. Any given enum should not be split into two seperate columns, much like a word should not be split across two pages. Each enum is seperated by the pipe character "|" and is formated as ````enumName {enumDefRef1, enumDefRef2}````. The name of the enum appears first followed by the references (if any) of the enumeration definition contained as comma seperated values inside a pair of braces. 

## The tool

This tool uses native order dictionaries and therefore must be run on a python version 3.6 or above. 

### tsv2yaml

To convert tsv files to yaml files:

From the terminal enter into the folder where tsv2yaml.py is found. Run ````python tsv2yaml.py -nodes ../tsvs/nodes_dcf.tsv -var variables_dcf.tsv -out ../dcf_demo/````

Commandline arguments:
````
-noterms: Optional argument. Assign to be "t" if desired yaml will not use any term/enum references or definitions
-nodes: The location of the nodes tsv you want to use
-var: The location of the variables tsv you want to use
-out: The destination of the yaml files. Creates a new folder if it does not already exist.
````


### yaml2tsv

This tool ignores _settings', '_definitions', '_terms', 'project', 'program' yamls. 

To convert yaml files to nodes and variables tsvs:

From the terminal enter into the folder where tsv2yaml.py is found. Run 
````python yaml2tsv.py -y ../dcf_schemas/ -t ../tsvs/ -d dcf````

Commandline arguments:
````
-y: The location of the yaml files. 
-t: The destination of the output tsvs
-d: The name of the data dictionary. 
````
