# PeptideMixQuant-MSMS
PeptideMixQuant-MSMS is a software that allows quantification of MS1 peak integrals of predefined peptides after validation in MS2 from LCMS tandem mass spectrometry. 

PeptideMixQuant-MSMS is distributed under the MIT license.

========== Example data file and output are provided.

## Usage

Download PeptideMixQuant-MSMS.ipynb as well as the folders data. Open PeptideMixQuant-MSMS.ipynb using Jupyter Notebook or Visual Studio Code and run all cells. Adjust peptide building blocks (example peptides = ["WR", "WD", "WN"]) and required combinations (“length”) as needed. The software will combine building blocks to create a list of “peptides” that will be used as a basis for searching and confirming mass peaks in the spectra. 

First, the software will calculate theoretical monoisotopic mass, expected fragment masses and isotope pattern of the building blocks and combinations of them (“peptides”) using pyOpenMs built-in modules. 

Afterwards it will compare m/z values from MS1 to identify monoisotopic mass of provided peptides and compare the theoretical and experimental MS2 data to confirm “peptides”.

Finally, it will cumulate all corresponding MS1 intensity values across the entire spectra and return the “sum_all_intensity” that equals the area for the respective peptide. This area is exported in a table (output .csv file) and printed in the total chromatogramm (output .png).

The software will iterate this procedure for all mzXML files stored in the “data” folder.
For convenience the output .csv files can be concatenated using provided concat-tables-csv.ipynb script.

![Figure_Readme](https://github.com/kkaygisiz/PeptideMixQuant-MSMS/blob/main/Readme.png?raw=true)

A detailed explanation of the usage and requirements of PeptideMixQuant-MSMS can be found below.

The software was developed and tested with
•	VSCode 1.96.4
•	Python 3.11.9
•	pyopenms 3.1.0
•	matplotlib 3.9.2
•	pandas 2.2.2
•	numpy 1.26.4


PeptideMixQuant-MSMS is powered by pyOpenMS, an open-source python library for mass spectrometry. 
For further documentation, please see https://pyopenms.readthedocs.io
Röst HL, Schmitt U, Aebersold R, Malmström L. pyOpenMS: a Python-based interface to the OpenMS mass-spectrometry algorithm library. Proteomics. 2014 Jan;14(1):74-7. doi: 10.1002/pmic.201300246.

## Input data: 
requires vendor free mzXML format, containing ms levels 1-2. 
You can convert common formats such as .raw, .d, .lcd for example by using the ProteoWizard msConvert (Adusumilli, R., Mallick, P. (2017). Data Conversion with ProteoWizard msConvert. In: Comai, L., Katz, J., Mallick, P. (eds) Proteomics. Methods in Molecular Biology, vol 1550. Humana Press, New York, NY. https://doi.org/10.1007/978-1-4939-6747-6_23)

## Output files:
.csv file summarizing total area of provided and found peptide sequences
.png plotting the total chromatogramm and integrated areas for provided and found peptide sequences
peptides.fasta  containing the fasta format of selected peptides
