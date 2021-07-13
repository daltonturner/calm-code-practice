# Lesson Notes

## Intro
This file contains lesson notes for the [Dirty Cat video series](https://calmcode.io/dirty-cat/introduction.html) at [calmcode.io](https://calmcode.io). An additonal pair of Jupyter Notebook is included at `daltonturner/calm-code-practice/dirty_cat`, which focus on the live-coding portion of the video lessons. One is the original Jupyter Notebook associated with the lesson, and one is a personal notebook with very similar code. 

This video series is aimed at teaching viewers how to deal with categorical variables when using `scikit-learn`. Categorical variables can be tricky to encode when there are more than two categories in a set of observations. 

## Count Vectors
Categorical variables with many categories can have categories which appear frequently and will likely appear in training and test sets. However, categories that appear less frequently may only appear in one or the other (training or test). This has an impact on model performance.

In this example, `ml_df['employee_position_title']` contains over eight hundred Police Officers, while the Director Office of Public Information appears only once. 

Rather than constructing features based on the entire job title and possibly omitting important information key words provide in describing job similarity (e.g. manager, officer, etc.), an alternative approach is available using `scikit-learn`. The `CountVectorizer` will take text as input, and output a sparse matrix of features.

## NGram
In order to provide robustness against spelling errors within category names, and by extension the `CountVectorizer`'s vocabulary, one can generate sub-words based on slices of the extracted words (Police: pol, oli, lic, ice). This expand's the vectorizer's vocabulary, and helps prevent miscategorization in the sparse matrix due to spelling errors, letter transposition, etc.

## Similarity
When using the sparse matrix to compare sub-words, one may ask if numeric features could be generated to tell us anything about the similarity between job titles. 

The `dirty_cat` package's `SimilarityEncoder` can do just that. Rather than just create a long list of sub-words and mapping each new sub-word to a new column in a sparse matrix, the `SimilarityEncoder` actually compares a chosen number of job titles across rows _and_ columns. 

Think Police Officer in column one and in row one. Police Manager in column two, row two, and so on. 

## Results
While the pipelines jump in complexity, they can be utilized to test various model types more rapidly and compare effectiveness across vectorizers and encoders. 

The count vectorizer with an ngram and similarity encoding using all job titles perform the best out of the models that were tested in the two pipelines. 
