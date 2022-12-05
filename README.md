# Hierarchical Clustering based Tunable Coding Unit Division for Video-based Point Cloud Coding 
This is the official repository of source codes and deployment methods for the paper "Hierarchical Clustering based Tunable Coding Unit Division for Video-based Point Cloud Coding".

<b>If you have contacted TMC2 and HM, you can skip subsequent lengthy instructions and directly use the source under “mpeg-pcc-tmc2-master\dependencies\HM-16.20+SCM-8.8\source\Lib\TLibEncoder\TEncCu.cpp” to change the source of original HM and check the methods described in our paper.</b>

## Resource Link
The program versions used in the experiment are as follows (You can get their official versions through the link after quotation marks): 

1. TMC2-v18.0: https://github.com/MPEGGroup/mpeg-pcc-tmc2/tree/release-v18.0
2. HM-16.20+SCM-8.8: https://vcgit.hhi.fraunhofer.de/jvet/HM/-/tree/HM-16.20+SCM-8.8
3. HDRTools-v0.18: https://gitlab.com/standards/HDRTools/-/tree/0.18-dev

## Content Introduction
In order to reduce the size of GitHub uploaded files, only some key files are uploaded. If necessary, please download the official version in the above link and replace it with the files provided by this repository. A brief introduction to the files provided is listed below: (You can skip this section and see How to Use It)

### mpeg-pcc-tmc2-master
This folder contains TMC2-v18.0 program, please pay attention to the following points: 
1.Under the folder "/mpeg-pcc-tmc2-master/bin/Teacher_5432/PccAppEncoder.exe" is the EXE file of our method.Its threrthold is 5432 as to the paper explain.The Specific code can refer to "dependencies/HM-16.20+SCM-8.8/source/Lib/TLibEncoder/TEncCu.cpp".
2.If you want to generate a new EXE file,you can mkdir a folder naming "build" and cmake it under this folder.THe patch file for HM in "/mpeg-pcc-tmc2-master/dependencies" is already Executed and other video software sush as VTM is unnecessary.
3. The cfg files under "/mpeg-pcc-tmc2-master/cfg/sequence" has been modified according to the below shell，please ensure that the point cloud files of 8iVSLF-vox10 or owlii-vox11 officially provided by MPEG are extracted into ply folder according to the default path, if you want to use our shell.

### external
1. HDRTools-v0.18, executable file HDRConvert.exe has been generated under “/external/HDRTools-v0.18/bin”.Its role is loading 3-D point cloud file.

### __batchProcessing_AI
1. Under this folder, we provide some scripts used for running our method in "/mpeg-pcc-tmc2-masterbin/Teacher_5432/PccAppEncoder.exe". Please modify the path in the shell file according to the actual deployment of your computer. In fact, you only modify the input file path in line 7. If there is no modification after downloading this repository, run this shell after correctly deploying the input file to start the operation of the <b>sequence soldier</b>. 
2.If your operation system is windows,please run the __runme_windows1.bat.

### __statisticData && __output
1.The reconstruction results are saved in the __output folder and the console output is saved in the __statisticdata folder.

### other file folders
You need to prepare the input file and modify the path in "/__batchProcessing_AI/*.sh", output stores the __output file of the point cloud, and __statisticdata stores the console output of the point cloud. 
<br/>These three files ensure that the script provided by us can run normally on your computer. If you don't want to use the script provided by us, you can set it according to your own preferences.

## How to Use It
1.Please modify all the script files in "/__batchProcessing_AI/*.sh", replacing the "SRCDIR" with your computer ply file's path in line 7. Then running the five script files. If your operation system is windows,please run the __runme_windows1.bat.
2.You can generate a new EXE file for other thresholds, mkdir a folder naming "build" under the folder "/mpeg-pcc-tmc2-master/" and cmake it. changing the threshold in "/mpeg-pcc-tmc2-master/dependencies/HM-16.20+SCM-8.8/source/Lib/TLibEncoder/TEncCu.cpp", so a new EXE file can be generated to check the data in the paper. Incidentally，the name of the generated EXE file should corresponds to the shell file in line 14.
