# Toxic Comments Classification

### Background
Today social media platforms are very prevalent and people spend most of their time on these platforms. Sometimes, people are directly or indirectly attacked on comments section of these websites which directly affect mental health of people. Hence, it is very crucial to identify such toxic comments and remove them as required.

### Contents
1. [Goal](#goal)
2. [Data Description](#data-description)
3. <a href='https://github.com/karishmachauhan/ToxicCommentsClassification/blob/main/LSTMandGRU.ipynb'>Toxic Comments Classifier Notebook</a>
4. [Evalution Metrics](#Evalution_Metrics)
5. [Outcome](#outcome)


### Goal
While identifying toxic comments from social media Machine Learning Models are bound to have a bias in the model for certain sensitive categories. For example if some abusive comments use word 'gay' a lot then it will classify even non-toxic comments as toxic which contains this word. Our goal is to minimize this unintended bias in the model while classifying the comments from Data Source:Online Hate Index Research Project at D-Lab, University of California, Berkeley.

## Data Description
After some Exploratory analysis we found out that 92 % of data belong to the non-toxic class and 7 % of data belong to the toxic class. In all subgroups, there are 77.55 % of comments have NAN values. Below word cloud shows threatening words in comments.<br>
<img src='https://github.com/karishmachauhan/ToxicCommentsClassification/blob/main/Screen%20Shot%202022-06-29%20at%207.40.47%20PM.png' alt='Word Cloud' height="300" width="400">


### Evalution Metrics
https://medium.com/jash-data-sciences/measuring-unintended-bias-in-text-classification-a1d2e6630742

a. Subgroup AUC — This calculates AUC on only the examples from the subgroup. It represents model understanding and performance within the group itself. A low value in this metric means the model does a poor job of distinguishing between toxic and non-toxic comments that mention the identity.

b. BNSP AUC — This calculates AUC on the positive examples from the background and the negative examples from the subgroup. A low value here means that the model confuses toxic examples that mention the identity with non-toxic examples that do not.

c. BPSN AUC — This calculates AUC on the negative examples from the background and the positive examples from the subgroup. A low value in this metric means that the model confuses non-toxic examples that mention the identity with toxic examples that do not.

d. Final Metrics — We combine the overall AUC with the generalized mean of the Bias AUCs to calculate the final model score:

score=w0AUCoverall+∑a=1AwaMp(ms,a) where:

A = number of submetrics (3)

ms,a = bias metric for identity subgroup s using submetric a

wa = a weighting for the relative importance of each submetric; all four w values set to 0.25


### Outcome
We were able to minimize the unintended bias from the comments for certain sensitive groups. We got bias accuracy for test approximately 0.92.

The model has been trained for 2 epochs using an initial LR of 2e-5, a warmup of 0.1 and Adam algorithm as optimizer:


| Epoch        | Train BIAS AUC          | Test Bias AUC  |
| ------------- |:-------------:| -----:|
| 1      | 0.9018 |0.9216|
| 2       | 0.9229      |    0.9220 |
| 1a |0.9222|    0.9214 |
| 2a |  0.9229     |     0.9239 |


|subgroup	|subgroup_size|	subgroup_auc	|bpsn_auc|	bnsp_auc
|2	|homosexual_gay_or_lesbian|	735	0.870923|	0.845379	|0.971873
|6|	black	|759	|0.872285|	0.867139|	0.965666
|7	|white|	1389|	0.892541|	0.865245	|0.971977
|5	|muslim	|814|	0.917186	|0.908285	|0.964685
|0	|male	2560|	0.937628|	0.938210|	0.962053
|1	|female	|3501	|0.940882|	0.950304	|0.955416
|8	|psychiatric_or_mental_illness|	315	0.953398|	0.946439|	0.962670
|3	|christian	|1896|	0.958670|	0.948718|	0.966918
|4	|jewish	|277	|0.959537|	0.935782|	0.970816


