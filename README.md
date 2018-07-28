# The Bobcat Bioinformatician’s solution to the ENCODE-DREAM challenge

A good machine learning model is primarily depending on the number of training examples and the relevance of features. Thus, we used a non-parametric algorithm, random forest, to train the models because we want to focus on increasing the training samples and selecting better features. The figure below shows an example of the feature design:

![model](https://github.com/YichaoOU/ENCODE-DREAM/blob/master/model.png)

*  DNA motifs from 6 databases were used, including CIS-BP, HOMER, HOCOMOCO, factorbook, encode-motif (Kellis lab), and Epigram. Notably, Epigram motifs are discovered from histone marks rather than TF ChIP-seq. Then motifs were ranked by a random forest classifier, top 120 TF-motifs and top 40 Epi-motifs were selected for each TF training set. 

* In vitro DNA shapes are HelT, Roll, MGW, ProT. The mean and max values were extracted using \textit{bigWigAverageOverBed} tool from UCSC. 

*  Open chromatin refers to DNase-seq. Also, the mean and max values were used.

* Gene expression information were used in three different ways: (1) the PCA algorithm was applied and the first 3 PCs (average value since two replicates per cell type) were used; (2) For each 200bp window, the expression value (TPM) of its nearest gene was used; (3) The expression values of the regulators of each TF were used.

* Finally, ten engineered features were added to the model to capture some non-linear relationship; they were: mean motif scores times the following values: mean signal of DNase, mean signal of the 4 types of DNA shape, first 3 PCs, nearest gene expression level, and average expression level of given TF-regulators. 

We only participated the conference round. Below is our performance summary:

![model](https://github.com/YichaoOU/ENCODE-DREAM/blob/master/result.png)

## Contact

Yichao Li, yl079811@ohio.edu

Lonnie Welch, welch@ohio.edu
