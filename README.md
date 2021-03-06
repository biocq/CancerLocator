
# **CancerLocator**  
A tool for cell-free DNA based cancer diagnosis and tissue-of-origin prediction.

## Prerequisites  
Java 1.8  
Apache Commons Math (if you want to build the source)


## Usage
java -jar CancerLocator.jar config_file

    config_file is a configuration file in Java Properties format.
    
    Options in the configuration file:
    trainFile: the traning file, only methylation values needed
    testMethyFile: the testing file with methylation values
    testDepthFile: the testing file with number of CpG measurements for each cluster
    typeMappingFile: the file used to map sample types to prediction classes
    resultFile: the output file
    thetaStep: the interval of theta values used in the inference
    methylationRangeCutoff: methylation range cutoff used for feature filtering
    logLikelihoodRatioCutoff: the cutoff of log-likelihood ratio used in prediction
    nThreads: number of threads


## File Instruction  

All the input and output files are tab delimited. trainFile, testMethyFile and testDepthFile must have the same number of columns. 

_trainFile_:   
    Each line represents a training sample. The first column is the sample type and the remaining columns are methylation values (beta values) of the features.  

_testMethyFile_:  
    Each line represents a training sample. The first column is the sample ID and the remaining columns are methylation values (beta values) of the features.

_testDepthFile_:  
    Each line represents a training sample. The first column is the sample ID and the remaining columns are CpG counts on reads aligned to these clusters.

_typeMappingFile_:  
    Column 1: the sample types  
    Column 2: corresponding classes in the prediction  
    For example, the following two lines in this file indicates that both LUAD and LUSC samples would be considered as lung cancer in the prediction.  
    LUAD    lung cancer  
    LUSC    lung cancer  

_resultFile_:  
    Column 1: sample ID  
    Column 2: likelihood ratio in logarithmic scale  
    Column 3: predicted blood tumor burden (i.e. theta value)  
    Column 4: predicted sample calss (normal or one of the cancer tissues)  
 

## Example

The examples of all the files needed to run CancerLocator are provided under the "example" folder.  

To run the example:  
Linux/OSX:  
./run_example.sh

Windows:  
run_example.cmd


## Reference

[__CancerLocator: non-invasive cancer diagnosis and tissue-of-origin prediction using methylation profiles of cell-free DNA__](http://genomebiology.biomedcentral.com/articles/10.1186/s13059-017-1191-5)  
Genome Biology, March 2017 18:53. DOI:10.1186/s13059-017-1191-5  
_Shuli Kang, Qingjiao Li, Quan Chen, Yonggang Zhou, Stacy Park, Gina Lee, Brandon Grimes, Kostyantyn Krysan, Min Yu, Wei Wang, Frank Alber, Fengzhu Sun, Steven M. Dubinett*, Wenyuan Li*, Xianghong Jasmine Zhou*_ (* Joint corresponding author)


## Contact

XJZhou@mednet.ucla.edu
