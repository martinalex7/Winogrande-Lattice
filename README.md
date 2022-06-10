# Winogrande-Lattice

Work done at the **Lattice Research Laboratory**, on the influence 
of lexical and semantical bias among training/test sets of BERT models applied to 
**Winograd Schema**.

### Datasets description (*number of Winograd Schema inside each set*) : 

|Name of the dataset  | train | test | validation |
|:-------------------:|:-----:|:--------:|:--------:|
|    winogrande_xs    |  160  | 1767 | 1267 |
|    winogrande_s     |  640  | 1767 | 1267 |
|    winogrande_m     | 2558  | 1767 | 1267 |
|    winogrande_l     | 10234 | 1767 | 1267 |
|    winogrande_xl    | 40398 | 1767 | 1267 |

### Methodology :

**Does BERT Models applied to Winograd Schema possesses Commonsense Reasoning?**

**Is there any statistical bias among the datasets which enable the model to perform as such?**

- **Step 1:** Establish relevant **semantical** and **syntaxical metrics** in order to quantify the bias among the different sets.
  - **Potential semantical metrics** to test : 
    - Mutual Information, Conditional Mutual Information
    - Topic Modeling (with LDA)
    - Clustering (KMeans, KNN...)
    - Usual metrics applied to sklearn's Vectorizers and BERT (and other Transformers) Vectorizer, 
    - Overlap Score (BM25, *Amati (2009)* )
  - **Potential syntaxical metrics** to test : 
    - Similarity scores (*tbd*) of parsing trees
    - Similarity scores (*tbd*) of dependency trees
    - Kernel methods
    
- **Step 2:** Descriptive Statistics:  
  - Descriptive statistics on the different sets using the new metrics 
  - Observation of the influence of lemmatization on the scores
  - Implementation of the mesures on complete schema, part-sent & no-cands (*Elazar (2021)*)
  
- **Step 3:** Measure of the impact of bias on model performances:
  - Sort the Winograd Schema (WS) among the training set in ascending order according to the semantical/syntaxical bias metrics and compare the model's performances by progressively adding the most biased Winograd Schema  
  - The task of BERT models applied to Winograd Schema consist in a binary classification. For a given WS, the model return as an output the choice with the highest probability. It would be interesting to display the absolute value of the spread between the two choices' probability in order to see how sure the model is.

### Progression : 

- **Step 1** :
  - *08/06* : Tryouts on Clustering and Topic Modeling Methods `first_test.ipynb`
  - *09/06* : Tryouts on SentenceTransformers' bert-base-nli-mean-tokens model