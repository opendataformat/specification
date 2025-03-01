Generating Open Data Format with R
================

-   [Generating ODF from CSV](#generating-odf-from-csv)
-   [Generating ODF from dataframe](#generating-odf-from-dataframe)

Author: Xiaoyao Han, Tom Hartl, Claudia Saalbach, Knut Wenzig  
Affiliation: DIW Berlin  
Created: 2024-08-12  
Version: v1.0.0  
Last modified: 2024-08-12
Licence: This repository is issued under a CC by licence
(<https://creativecommons.org/licenses/by/4.0/>)

------------------------------------------------------------------------
This section demonstrates how to generate data files in the Open Data Format (ODF) using R. 
The first approach is to generate four CSV files following the specification of the internal Open Data Format. 
The second approach is to enrich an R data.frame with the metadata in accordance with the ODF specification directly in R.


## Generating ODF from CSV

An easy way to generate data files in the Open Data Format is to go through
four CSV files in the Internal Open Data Format. The `opendataformat.tools` 
package in R offers a function to generate an ODF zip-file from the four CSVs.
The advantage using this approach is that CSV files containing data and 
metadata can be easily generated by any data provider who has structured 
metadata in a machine-readable format.

The requirements and structure of the CSV files for generating ODF and 
examples can be found on GitLab.

Once the four CSV files are provided the ODF can be generated using the 
`convert_opendf()`-command from the opendataformat.tools package.

## Generating ODF from enriched dataframe

A second approach is to enrich a tibble data.frame in R with metadata according to  
the ODF specification and in line with the internal specification of the opendf 
package for storing metadata.

Therefore, metadata has to be assigned to the attributes of the tibble and 
the variables.
The dataset metadata is stored in the attributes of the dataset.
The dataset has the attributes `languages` with a vector of metadata languaguages 
available.
Further, the dataset metadata includes the fields/attributes `study`, `name`, 
`label_lang` and `description_lang` for each language (lang), and `url`. 
The ODF allows multilingual labels and descriptions by using the *lang* suffix. 
This suffix holds the language code defined by the ISO 639-1 
(<https://de.wikipedia.org/wiki/Liste_der_ISO-639-1-Codes>). For example, if a 
description is specified in English and in German, there will be both a 
attribute `description_en` and a attribute `description_de`. 

The variable metadata includes the fields/attributes `label_lang` and 
`description_lang` for each language (lang), `type` (character or numeric), 
and `url`. 
Additionally, the value labels are stored in teh `labels_lang` attribute which 
is a vector with the labelled values and the value labels in the namespace 
of each value.

