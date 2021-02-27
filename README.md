

## ![alt text](https://github.com/ArcanaBatch/CABBaGe/blob/main/Images/banner5.png)
 ![alt text](https://img.shields.io/badge/Version-2.01-brightgreen)
## CABBaGe: Classification Algorithm Based on a Bayesian method for Genomics

An application developed in Perl and Python that allows the development of classification models for genomic sequences, to improve data mining and usefulness of genomic applications.
____
### Dependencies 
|software|version|required|
|---|:---:|:---:|
VAMPhyRE|1.0 or above|yes
perl|5.30 or above|yes
python|3.8 or above|only for GUI
pillow|8.1 or above|only for GUI
pandas|1.2.0 or above|only for GUI
ttkthemes|3.1.0 or above|only for GUI

`Note: You can download VAMPhyRE from here:
http://biomedbiotec.encb.ipn.mx/VAMPhyRE/download.php`




The CABBaGe application core is built from three modules:
### Bayesian Classifier, Feature Extractor and Feature Filter (only with GUICABBaGe)

* The Bayesian Classifier, this module uses a Naive Bayes Classifier technique which is based on the so-called Bayesian theorem and is particularly suited when the dimensionality of the inputs is high. Despite its simplicity, Naive Bayes can often outperform more sophisticated classification methods. The module classifies genomic sequences into predetermined classes using a training genome matrix of known parameters (e.g. disease, host age, host sex, geographic location, drug resistance etc.)

### How to
##### **_Note:_  In order for the CABBAGE to resume operation the input format must be comma-separated values (.csv) files**
> Three files are needed: _Training.csv, MetaData.csv and Query.csv_

> The _Training.csv_ file is a Boolean table that denotes the presence or absence of a certain "feature" which can either be a gene (Pan-genome*) or a genomic region denotated by a virtual probe (Virtual Hybridization*).

> The _MetaData.csv_ file is a table that relates each of the samples form the _Training.csv_ to predefined classes.

> The _Query.csv_ file are the samples that must be classified, and they should be on the same format as in the _Training.csv_ file.


____
* The Feature Extractor; classification has the problem of high dimensionality of feature space due to the extensive information from genomic data. This high dimensionality of feature space is solved by feature selection and feature extraction methods that improve the performance of categorization. The feature selection and feature extraction techniques remove the irrelevant features from the test and reduce the dimensionality of feature space. The module accomplishes this task using a statistics test (e.g. Chi squared) extracting the most informative genes or genomic regions that make a sample belong to a particular class.

### How to
##### **_Note:_  In order for the CABBAGE to resume operation the input format must be comma-separated values (.csv) files**
> Two files are needed: _Training.csv and MetaData.csv_

> The _Training.csv_ file is a Boolean table that denotes the presence or absence of a certain "feature" which can either be a gene (Pan-genome*) or a genomic region denotated by a virtual probe (Virtual Hybridization*).

> The _MetaData.csv_ file is a table that relates each of the samples form the _Training.csv_ to predefined classes.

> Adicionally a statistical _Test_ must be chosen.
____
* The Feature Filter, this module is a tool for extracting the top n informative features extracted by the Feature Extractor module, thus the user determines the number of features to be contained in the developed clasification model.

### How to
##### **_Note:_  In order for the CABBAGE to resume operation the input format must be comma-separated values (.csv) files**
> One file is needed: _Probabilities.csv, MetaData.csv and Query.csv_

> The _Probabilities.csv_ file is the output file from the Feature Extractor module, wich is a list of all the informative features for the model.

> Adicionally an _Out File name_ must be provide as well as the _Number Of Features_ for the final model.





#### Files examples.

##### _Training.csv_

>|           | `Sample1` | `Sample2` | `Sample3` | `Sample4` |
>| ----------| ---: | ---:  | ---:  | ---: |
>| `Gene/Probe a` | 0 | 1 | 1 | 0 |
>| `Gene/Probe b` | 1 | 1 | 1 | 1 |
>| `Gene/Probe c` | 1 | 1 | 0 | 0 |
>| `Gene/Probe d` | 0 | 0 | 0 | 0 |
>| `Gene/Probe e` | 1 | 0 | 1 | 1 |
>| `Gene/Probe f` | 1 | 1 | 1 | 1 |

The `Samples` and `Gene/Probe` names should be determined by the user, the file can contain as many rows and columns as needed.

##### _MetaData.csv_

>| `Sample` | `Class` |
>| ----------| ---: | 
>| `Sample1` | A | 
>| `Sample2` | B | 
>| `Sample3` | C | 
>| `Sample4` | D | 
>| `Sample5` | E | 
>| `Sample6` | F | 

The `Samples` and `Gene/Probe` names should be determined by the user, the file can contain as many rows as needed.

##### _Query.csv_

>|           | `SampleX` | `SampleY` | `SampleZ` |
>| ----------| ---: | ---:  | ---:  |
>| `Gene/Probe a` | 1 | 1 | 1 |
>| `Gene/Probe b` | 1 | 1 | 0 |
>| `Gene/Probe c` | 1 | 0 | 0 |
>| `Gene/Probe d` | 0 | 0 | 0 |
>| `Gene/Probe e` | 1 | 0 | 0 |
>| `Gene/Probe f` | 1 | 1 | 1 |

The `Samples` and `Gene/Probe` names should be determined by the user, nonetheless the Gene/Probe must be the same as the _Training.csv_ file used. The file can contain as many rows and columns as needed.

## GUI
#### `GUICABBaGe is a wrap-up tool developed in python for an easier user experience, at  present (February 2021) is only available for Windows OS.`
This Graphic User Interface permits the users to quickly develop clasification models even if they are not familiarized with terminal commands shortening the learning curve.

### Captions
![](https://github.com/ArcanaBatch/CABBaGe/blob/main/Images/captioncabbage.png)
![](https://github.com/ArcanaBatch/CABBaGe/blob/main/Images/captioncabbage2.png)
## Example

For this example, a collection of Klebsiella sp. genomes can be found in the Example folder, here a classification for different species is made among Variicola, Quasipneumoniae and Oxitoca strains.

SCREENING PHASE
1)	Preprocess the samples found in the “Training folder” using VAMPhyRe with the following commands:

VH5cmdl –PROBEFILE vps13.txt –TARGETLIST TrainingList.txt –OUTFILE VH5outfile.txt -MISMATCHES 1 –STRAND both

VHRP -VHDATAFILE VH5outfile.txt -PROBEFILE vps13.txt -TARGETLIST TrainingList.txt -GLOBALFILE Screening

The main goal of this step is to obtain the “Screening.csv” file which contains all the information of the virtual hybridization.
2)	Use the Feature Extractor Module in CABBaGe select the “Screening.csv” as the TrainingFile and the “metadatakleb.csv” as the Meta Data File, also select the statistical test as chi-square “X2” for this example.
From this step a new folder will be created “ResultsFE” inside you will find the “Chi_SquareScreening.csv” file and the presence absence file which contains the informative value of each k-mer and the presence distribution of each one of them, respectively.

FILTERING PHASE
3)	Use the Feature Filter Module in CABBaGe select the “Chi_SquareScreening.csv” file as the Probabilities File, determine the Out File Name “Filtered” for this example and the number ok the top informative k-mers to be extracted “100” for this example.
From this step a new folder will be created “ResultsFF” inside you will find the “Filtered100.csv” file and the “FilteredVPS.txt” file both contain the information of the top 100 k-mers selected to become the classification model.
4)	Preprocess the samples found in the “Training folder” using VAMPhyRe with the following commands:
VH5cmdl –PROBEFILE FilteredVPS.txt –TARGETLIST TrainingList.txt –OUTFILE VH5Filteredoutfile.txt -MISMATCHES 1 –STRAND both
VHRP -VHDATAFILE VH5Fikteredoutfile.txt -PROBEFILE FilteredVPS.txt -TARGETLIST TrainingList.txt -GLOBALFILE Training

After this process you will have the final “Training.csv” file which represents the classification model for this example.

CLASSIFICATION PHASE
5)	Preprocess the samples found in the “Validation folder” using VAMPhyRe with the following commands:
VH5cmdl –PROBEFILE FilteredVPS.txt –TARGETLIST ValidationList.txt –OUTFILE VH5valoutfile.txt -MISMATCHES 1 –STRAND both
VHRP -VHDATAFILE VH5valoutfile.txt -PROBEFILE FilteredVPS.txt -TARGETLIST ValidationList.txt -GLOBALFILE Query
In this step we preprocess the genomes to be classified using the filtered k-mers previously obtained. At the end we have a “Query.csv” file with the presence absence information from the virtual hybridization.
6)	Use the Bayesian Classifier Module in CABBaGe select the “Training.csv” as the Training File the “metadatakleb.csv” as the Meta Data File and the “Query.csv” as the query file.
In this step a new folder will be created “ResultsBC” inside you will find two files the “Probabilities.csv” file and the “Prediction.csv” file in the latter you can find the classification made for the validation samples which should be as follows:

>| Sample | Class |	     Probability
>| NZ_CP017849.1 | 	Class variicola |	      6.39E+43
>| NZ_CP054254.1 | 	Class variicola |	      6.48E+61
>| NZ_CP018307.1 | 	Class variicola |	      2.27E+65
>| NZ_LR134235.1 | 	Class variicola	|      4.23E+67
>| NZ_CP048379.1 | 	Class variicola |	      6.70E+90
>| NZ_CP023478.1 | 	Class quasipnemoniae |	 4.91E+122
>| NZ_CP026368.1 | 	Class quasipnemoniae |	 6.11E+122
>| NZ_CP063902.1 | 	Class quasipnemoniae |	 6.27E+124
>| NZ_CP012252.1 | 	Class quasipnemoniae |	 5.40E+126
>| NZ_CP029437.1 | 	Class quasipnemoniae |	 2.16E+127
>| NZ_CP026275.1 | 	Class oxytoca |	        1.78E+131
>| NZ_LR134333.1 | 	Class oxytoca |	        1.28E+132
>| NZ_CP020358.1 | 	Class oxytoca |	        4.11E+132
>| NZ_CP026285.1 | 	Class oxytoca |	        3.37E+133
>| NZ_CP026269.1 | 	Class oxytoca |	        8.91E+133

Under development...
