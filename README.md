# Toxic Comments Classification

### Background
Today social media platforms are very prevalent and people spend most of their time on these platforms. Sometimes, people are directly or indirectly attacked on comments section of these websites which directly affect mental health of people. Hence, it is very crucial to identify such toxic comments and remove them as required.

### Contents
1. [Goal](#goal)
2. [Data Description](#data-description)
3. <a href='https://github.com/karishmachauhan/ToxicCommentsClassification/blob/main/LSTMandGRU.ipynb'>Toxic Comments Classifier Notebook</a>
4. [Outcome](#outcome)


### Goal
While identifying toxic comments from social media Machine Learning Models are bound to have a bias in the model for certain sensitive categories. For example if some abusive comments use word 'gay' a lot then it will classify even non-toxic comments as toxic which contains this word. Our goal is to minimize this unintended bias in the model while classifying the comments from Data Source:Online Hate Index Research Project at D-Lab, University of California, Berkeley.

### Data Description

After some Exploratory analysis we found out that 92 % of data belong to the non-toxic class and 7 % of data belong to the toxic class. In all subgroups, there are 77.55 % of comments have NAN values. Below word cloud shows threatening words in comments.<br>
<img src='https://github.com/karishmachauhan/ToxicCommentsClassification/blob/main/Screen%20Shot%202022-06-29%20at%207.40.47%20PM.png' alt='Word Cloud' height="300" width="400">

### Outcome
We were able to minimize the unintended bias from the comments for certain sensitive groups. We got bias accuracy for test approximately 0.92.
