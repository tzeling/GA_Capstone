
# GA Capstone - Classifying Adverse Event Seriousness using NLP

## Executive Summary
An adverse event (AE) is a harmful or negative outcome that occurs when a patient has been provided with medical care or treatment). This project aims to build a model to classify serious and non-serious AE. In the data cleaning section, duplicates were removed, null values were either imputed or dropped and the target column of 'serious' was created. Through EDA, we found symptom_text to be the most predicitve text column out of all and will be used for modelling.

A total of 4 models were evaluated - (i) Logistic Regression; (ii) Naive Bayes - Multinomal; (iii) Random Forest Classifier; (iv) Ada Boost Classifier; and (v) Support Vector Machine (SVM). 2 different train-test split were chosen: 10/90 and 80/20 train/test respectively. Modelling was done with and without Synthetic Minority Oversampling Technique (SMOTE), and the model that met the target was Logistic Regression utilizing TF-IDF vectorizer with 80/20 split without SMOTE. This model yielded test accuracy of 0.904, train accuracy of 0.914 and F1 score of 0.709.

In conclusion, the model was successful in meeting the requirements from the problem statement. Our recommendation is to implement the model as a preliminary screening tool for all incoming AE reports, to get an initial seriousness classification. This would help to enable serious reports to get expedited and processed more quickly, enabling signal detection to occur more efficiently.

## Problem Statement
As a data scientist in a consultant firm to the Health Authority in Singapore, we have been tasked to help create a model to differentiate between serious and non-serious AE from reports obtained from various sources.

The following models will be tested as potential candidates:
* Logistic Regression
* Naive Bayes - Multinomial
* Random Forest Classifier
* Ada Boost Classifier
* Support Vector Machine (SVM)

A successful model is defined as having an accuracy and F1 score of at least 0.7.

## Background
An AE is a harmful or negative outcome that occurs when a patient has been provided with medical care or treatment ([source](https://www.ncbi.nlm.nih.gov/books/NBK558963/)).

With every new drug or vaccine that comes into the market, there is a need for health authorities worldwide to be on the look out for any signals indicating the product is unsafe for the general population. A major source of these signals is through the submission of spontaneous AE reports from anyone (e.g. patients, healthcare professionals, social media, etc.) ([source](https://cioms.ch/wp-content/uploads/2018/03/WG8-Signal-Detection.pdf)).

Generally companies and authorities would want to detect a spike in serious AE. This labelling of severity in companies are generally done manually, which increase the risk of human misclassification and is time consuming. An AE is classified as serious if the patient outcome is one of the following ([source](https://www.fda.gov/safety/reporting-serious-problems-fda/what-serious-adverse-event)):
* Death
* Life-threatening
* Hospitalisation (initial or prolonged)
* Disability or Permanent Damage
* Congenital Anomaly or Birth Defect
* Other Serious (Important Medical Events (IME))

Since not all reporters have the expertise to determine whether an AE is serious, there is a need to create a system to quickly and accurately identify potential serious AE to ensure timely response which may include advisories or drug recall by the health authority of pharmaceutical company.

The dataset is taken from Vaccine Adverse Event Reporting System ([VAERS](https://vaers.hhs.gov/index.html)). VAERS is a national warning system in US to detect possible safety problems in US-licensed vaccines, and anyone can report an AE to VAERS ([source](https://vaers.hhs.gov/about.html)).

## Datasets
Please retrieve data files from the following link: https://drive.google.com/drive/folders/1iUyIj7jbuFzSfmWsy6I7uqgP-DxUI0CU?usp=sharing
* `VAERSDATA.CSV`: Patient information, general AE description and fields
* `VAERSVAX.CSV`: Information on vaccine
* `VAERSSYMPTOMS.CSV`: Information on symptoms

## Data Dictionary
The following table describes the different features in the data. A guide of how to intepret the original dataset can also be found at the following [link](https://vaers.hhs.gov/docs/VAERSDataUseGuide_en_September2021.pdf).

| Feature | Type | Description |
|---:|---:|---:|
| symptom_text | object | Description of symptoms experienced by patient |
| serious | int | non-serious or serious |

## Conclusion & Recommendations
Overall, the chosen model is succesful in meeting the requirements by the problem statement. With a test accuracy of 0.904, train accuracy of 0.914 and F1 score of 0.709. The difference between the train and test accuracy of 0.01 indicates that the model is not overfitted to the training dataset. The 5-fold cross-validated score of 0.902 shows that the test score is a reliable measure of the model performance.

#### Recommendations
Since our model is able to accurately classify serious AE, it could be implemented as a preliminary screening tool for all incoming AE reports, to get an initial seriousness classification. This would help to enable serious reports to get expedited and processed more quickly, enabling signal detection to occur more efficiently.

## Future Improvements
#### Obtain further data to expand scope of model
Since there is a low rate of reporting AE in Singapore, it would be helpful to look into expanding this model to be able to classify between an AE report vs non-AE report. With such a model, it would be possible to try to obtain AE reports from retrospectively looking at electronic medical reports to sieve out potential AE instead of relying passively for people to report cases.

#### Use of deep learning techniques through neural networks
As neural networks are able to learn and model non-linear and complex relationships, it could possibly be used to classify reports more efficiently as it would be able to distinguish nuance difference through optimisation of the layers.

#### Incorporate use of non-text columns into model
The use of non-text data could be included into training of the model to help produce a more robust model.
