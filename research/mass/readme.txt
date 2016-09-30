%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%%%% General Information %%%%%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

Title:        The Mass Estimation Package
Version:      1.0.0
Date:         2010-05-01
Requirements: MATLAB (>=7.4 R2007a), libsvm
Author:       Guang-Tong Zhou
Description:  This package includes the MATLAB code for mass estimation.
Maintainer:   Guang-Tong Zhou <zhouguangtong@gmail.com>
References:   K. M. Ting, G.-T. Zhou, F. T. Liu and S. C. Tan, Mass Estimation and Its Applications, In: Proceedings of the 16th ACM SIGKDD Conference on Knowledge Discovery and Data Mining (KDD'10), 989-998, Washington, DC, 2010.

Attention 1:  This package is free for academic usage. You can run it at your own risk. For other purposes, please contact Dr. Kai Ming Ting.
Attention 2:  This package was developed by Guang-Tong Zhou. Please feel free to contact him for any problem concerning the code.

This package is also available at https://sourceforge.net/projects/mass-estimation/.


%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%%%%%%%%%% Usage %%%%%%%%%%%%%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Installation
1.1 Download the [mass estimation package] (261Kb) and unzip it to a separate directory.
1.2 Run 'Code/Run_Example_all.m' to obtain simulation results.
1.3 Build libsvm with 'Library/libsvm/make.m' (for regression tasks only).
(Notice: we used windows plateform in our experiments. To instal libsvm on other plateforms, please see the libsvm instruction.)

2. Content-based image retrieval

2.1. Download the retrieval data:
     corel100.mat - 100 classes COREL data
     This MATLAB data file is composed of two matrices:
     (1) "Data": n*d data matrix; "n" is the number of images; "d" is the dimension;
     (2) "Labels": n*k label matrix; "k" is the number of categories; Labels(i,j)=1 if image_i in category j; otherwise, Labels(i,j)=-1;
2.2. Place the MATLAB data files in directory 'Data/Retrieval/'.
2.3. Run 'Code/Run_Retrieval_all.m' to receive the retrieval results, which will be saved in directory 'Results/Retrieval/'.


3. Regression

3.1. Download the regression data:
     coil.mat        - the tic data set; (available at http://archive.ics.uci.edu/ml/datasets/Insurance+Company+Benchmark+(COIL+2000))
     wine_white.mat  - the wine_white data set; (available at http://archive.ics.uci.edu/ml/datasets/Wine+Quality)
     quake.mat       - the earthquake data set; (converted from WEKA quake data in "datasets-numeric.jar", http://www.cs.waikato.ac.nz/ml/weka/)
     wine_red.mat    - the wine_red data set; (available at http://archive.ics.uci.edu/ml/datasets/Wine+Quality)
     compressive.mat - the concrete data set; (available at http://archive.ics.uci.edu/ml/datasets/Concrete+Compressive+Strength)
     Each MATLAB data file is composed of two matrices:
     (1) "Data": n*d data matrix;  "n" is the number of instances; "d" is the dimension;
     (2) "Labels": n*1 vector of regression values;
3.2. Place the MATLAB data files in directory 'Data/Regression/'.
3.3. Run 'Code/Run_Regression_all.m' to get the regression results, which will be saved in directory 'Results/Regression/'.


4. Anomaly detection

4.1. Download the anomaly detection data:
     http.mat     - the Http data set; (available at http://archive.ics.uci.edu/ml/datasets/KDD+Cup+1999+Data)
     cover.mat    - the ForestCover data set; (available at http://archive.ics.uci.edu/ml/datasets/Covertype)
     mulcross.mat - the Mulcross data set; (available at http://personal.gscit.monash.edu.au/~kmting/Mass)
     smtp.mat     - the Smtp data set; (available at http://archive.ics.uci.edu/ml/datasets/KDD+Cup+1999+Data)
     shuttle.mat  - the Shuttle data set; (available at http://archive.ics.uci.edu/ml/datasets/Statlog+(Shuttle))
     Each MATLAB data file is composed of two matrices:
     (1) "Data": n*d data matrix; "n" is the number of instances; "d" is the dimension;
     (2) "ADLabels": n*1 vector of anomaly labels; ADLabels(i)=1 if instance_i is anomaly; otherwise, ADLabels=0;
     (More information about the anomaly detection data sets can be found in the file 'anomalydata.pdf'.)
4.2. Place the MATLAB data files in directory 'Data/Anomaly/'.
4.3. Run 'Code/Run_Anomaly_all.m' to see the anomaly detection results, which will be saved in directory 'Results/Anomaly/'.



%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%%%%%%% Architecture %%%%%%%%%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%


%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%% 1. Code/ - codes file %%%%%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1.1. Mass Estimation:

MassEstimate.m - estimate mass for a data set;
MassUnit.m     - calculate mass of a single point;
MassTrain.m    - practial mass estimation: training;
MassPredict.m  - practial mass estimation: prediction;


1.2. Retrieval:

Run_Retrieval_all.m          - obtain the retrieval results;
Retrieval_randidx.m          - randomly generate indics for query and feedbacks;
Main_Retrieval_Dist.m        - calculate squared Euclidean distance matrix (original space);
Main_Retrieval_Graph.m       - calculate L1-norm graph matrix for MRBIR (original space);
Main_Retrieval_MassDist.m    - calculate squared Euclidean distance matrix (mass space);
Main_Retrieval_MassGraph.m   - calculate L1-norm graph matrix for MRBIR (mass space);
Main_Retrieval_MassMRBIR.m   - main function for MRBIR' method;
Main_Retrieval_MRBIR.m       - main function for MRBIR method;
Main_Retrieval_MassQsim.m    - main function for Qsim' method;
Main_Retrieval_Qsim.m        - main function for Qsim method;
Main_Retrieval_MassIR.m      - main function for InstR' method;
Main_Retrieval_InstRank.m    - main function for InstR method;
Main_Retrieval_ttest_query.m - main function for t-test on retrieval with one query;
Main_Retrieval_ttest.m       - main function for t-test on retrieval in relevance feedback;
CBIR_MRBIR.m                 - MRBIR method for retrieval in relevance feedback;
CBIR_Query_MRBIR.m           - MRBIR method for retrieval with one query;
CBIR_Qsim.m                  - Qsim method for retrieval in relevance feedback;
CBIR_InstSim.m               - InstR method for retrieval in relevance feedback; 
Measure_BEP.m                - measure retrieval performance using BEP;
Measure_effectiveness.m      - measure retrieval performance using effectiveness;
Measure_avePrecision.m       - measure retrieval performance using average precision;
Measure_TopPrecision.m       - measure retrieval performance using top-N precision;
Measure_PRGraph.m            - measure retrieval performance using PR-graph;


1.3. Regression:

Run_Regression_all.m          - obtain the regression results;
Regression_randidx.m          - randomly generate indics for training and testing;
Main_Regression_RandMassSVR.m - main function for SVR' method;
Main_Regression_SVR.m         - main function for SVR method;
Measure_MSE.m                 - measure regression performance using MSE;
Measure_SCC.m                 - measure regression performance using SCC;


1.4. Anomaly Detection:

Run_Anomaly_all.m       - obtain the anomaly detection results;
Main_Anomaly_RandMass.m - main function for MassAD method;
Main_Anomaly_IFMass.m   - main function for iForest method;
IsolationForest.m       - build an iForest model;
IsolationTree.m         - build an isolation tree model;
IsolationEstimation.m   - estimation path length on an iForest model;
IsolationMass.m         - estimation path length on an isolation tree model;
Measure_AUC.m           - measure anomaly detection performance using AUC;


1.5. Miscellaneous:

Run_Example_all.m - obtain figures for some simulation examples;
KDE.m             - kernel density estimation;
ConstKernels.m    - construct kernels;
cvpartitionidx.m  - randomly partion;
min2d.m           - find minimum in a 2-D matrix;
min3d.m           - find minimum in a 3-D matrix;
MinMax_Norm.m     - min-max normalize data to interval [0, 1];



%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%%% 2. Data/ - data file %%%%%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

2.1. Data/Anomaly/ - data for anomaly detection:

cover.mat    - ForestCover data set;
http.mat     - Http data set;
mulcross.mat - Mulcross data set;
shuttle.mat  - Shuttle data set;
smtp.mat     - Smtp data set;


2.2. Data/Example/ - data for simulation examples:

bimodal.mat  - bimodal data;
cluster.mat  - cluster data;
normal.mat   - normal data;
skew.mat     - skew data;
trimodal.mat - trimodal data;
uniform.mat  - uniform data;


2.3. Data/Regression/ - data for regression:

coil.mat        - tic data set;
compressive.mat - concrete data set;
quake.mat       - earthquake data set;
wine_red.mat    - wine_red data set;
wine_white.mat  - wine_white data set;


2.4. Data/Retrieval/ - data for CBIR;

corel100.mat - COREL data set;



%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%% 3. Library/ - library file %%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

3.1. Library/libs/ - distance calculation functions:

dist2.m  - calculate squared Euclidean distance;
distm.m  - calculate mahalanobis distance;
EuDist.m - calculate squared Euclidean distance (slower than dist2.m but requires less memory);


3.2. Library/libsvm/ - libsvm package:

Chih-Chung Chang and Chih-Jen Lin, 
LIBSVM : a library for support vector machines, 2001. 
Software available at http://www.csie.ntu.edu.tw/~cjlin/libsvm.



%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%% 4. Local/ - local file %%%%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

4.1. Local/Anomaly/ - local files for anomaly detection (currently no use)


4.2. Local/Regression/ - local files for regression:

randidx_***.mat - randomly generated indices for training and testing;
(need to run ../Code/Run_Regression_all.m)


4.3. Local/Retrieval/ - local files for CBIR:

pnidx_***.mat        - randomly generated indices for query and feedbacks;
dist_***.mat         - precalculated squared Euclidean distance matrix (original space);
graph_l1_***.mat     - precalculated L1-norm graph matrix for MRBIR (original space);
massdist_***.mat     - precalculated squared Euclidean distance matrix (mass space);
massgraph_l1_***.mat - precalculated L1-norm graph matrix for MRBIR (mass space);
(need to run ../Code/Run_Retrieval_all.m)



%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%% 5. Results/ - results file %%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

5.1. Results/Anomaly/ - anomaly detection results:

Results_RandMass_***.mat - anomaly detection results of MassAD;
Results_IFMass_***.mat   - anomaly detection results of iForest;
Results_Anomaly.mat      - statistcal comparison of the results, 
                           AUC, runtime, t-test, win/draw/loss counts;
(need to run ../Code/Run_Anomaly_all.m)


5.2. Results/Regression/ - regression results:

Results_RMepSVR_***.mat - regression results of SVR';
Results_SVR_***.mat     - regression results of SVR;
Results_Regression.mat  - statistcal comparison of the results, 
                          MSE, SCC, runtime, t-test, win/draw/loss counts;
(need to run ../Code/Run_Regression_all.m)


5.3. Results/Retrieval/ - retrieval results:

Results_MassMRBIR_***.mat - retrieval results of MRBIR';
Results_MRBIR_***.mat     - retrieval results of MRBIR;
Results_MassQsim_***.mat  - retrieval results of Qsim';
Results_Qsim_***.mat      - retrieval results of Qsim;
Results_MassIR_***.mat    - retrieval results of InstR';
Results_InstRank_***.mat  - retrieval results of InstR;
Results_Retrieval.mat     - statistcal comparison of the results, 
                            BEP, effectiveness, runtime, t-test, win/draw/loss counts;
(need to run ../Code/Run_Retrieval_all.m)
