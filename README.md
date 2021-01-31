
## ![alt text](https://github.com/ArcanaBatch/CABBaGe/blob/main/Images/Imagen3.png)

## CABBaGe: Classification Algorithm Based on a BAyesian method for GEnomics

An application developed in Perl and Python that allows the development of classification models for genomic sequences, to improve data mining and usefulness of genomic applications.
____
### Dependencies 
|software|version|required|
|---|:---:|:---:|
perl|5.30 or above|yes
python|3.8 or above|only for GUI
pillow|8.1 or above|only for GUI
pandas|1.2.0 or above|only for GUI
ttkthemes|3.1.0 or above|only for GUI

The application core is built from three standalone modules:
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
### CABBaGeGUI is a wrap up developed in python for an easier user experience, at  present (February 2021) is only available for windows.
This Graphic User Interface permits the users to quickly develop clasification models even if they are not familiarized with terminal commands shortening the learning curve.

### Captions
![](https://github.com/ArcanaBatch/CABBaGe/blob/main/Images/captioncabbage.png)
![](https://github.com/ArcanaBatch/CABBaGe/blob/main/Images/captioncabbage2.png)
## Example

Under development...
