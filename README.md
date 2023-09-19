# Naive Bayes Classifier and NLP for Spam Email Classification

### Project Status:
ongoing

### Project Objectives:
The objectives of the project are the following.
- use the [Apache SpamAssassin Dataset (from 2005)](https://spamassassin.apache.org/old/publiccorpus/) and Bag of Words method to create a Naive Bayes Classifier  
- pre-process the data using the NLTK library for NLP

### Preprocessing steps
After importing the data into a dataframe with two columns ('email_body', 'category') several text processing steps are taken using regular Python functions, BeautifulSoup and the NLTK library:
- remove HTML (BeautifulSoup)
- lowercase
- tokenize
- remove punctuation
- remove English stop words
- stem words


### Classification

For classification, we experiment with the Bernoulli- and the Multinomial Naive Bayes Classifiers from the Scikit Learn library. The Multinomial NB Classifier consistently outperformed the Bernouilli NB Classifier.

With regards to the inclusion of stop words, three different scenarios were tested.

__Scenario 1:__  
removal of all stop words  
Accuracy: 0.9643  

|                    | Actual Spam | Actual Ham |
|--------------------|:---------------:|:---------------:|
| **Predicted Spam** |       496        |       13        |
| **Predicted Ham** |       49        |       1181        |  

In this scenario there are significantly more false negatives than false positives.
 
__Scenario 2:__  
inclusion of all stop words  
Accuracy: 0.9695  

|                    | Actual Spam | Actual Ham |
|--------------------|:---------------:|:---------------:|
| **Predicted Spam** |       501        |       9        |
| **Predicted Ham** |       44        |       1185        |  

 In this scenario the discrepancy betweeng false negatives and false positives is similar, although the overall accuracy is slightly better
 
__Scenario 3:__  
Stemming of stop words followed by removal (this caused some stop words to be removed and others to remain)  
Accuracy: 0.9718  

|                    | Actual Spam | Actual Ham |
|--------------------|:---------------:|:---------------:|
| **Predicted Spam** |       525        |       29        |
| **Predicted Ham** |       20        |       1165        |  

In this scenario we see an additional improvement in accuracy and more balance in the number of false negatives and false positives.

Since its better to incorrectly classify a spam message as non-spam than the other way around, the best-performing model in this case would be the one tested in Scenario 2, which includes all the stop words. However, it would be interesting to see how well this model generalizes.

With an accuracy of approx. 96-97% all 3 models are fairly good. Scenario 3 indicates that playing around with the removal of stop words can bring down the number of false negatives significantly - it could be worth checking whether the same stop words which reduce false negatives also increase false positives.

 

