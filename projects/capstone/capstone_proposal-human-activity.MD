# Machine Learning Engineer Nanodegree
## Capstone Proposal
Glenn Mossy 
November 2, 2019

## Proposal - A Machine Learning based malware detector
### Domain Background
Human activity recognition (HAR) plays an important role in people’s daily life for its competence in learning profound high-level knowledge about human activity from raw sensor inputs. [1]

My interest in this field stems from my work with AT&T Public sector where I am a Senior Solutions Architect providing technical leadership on Technology Innovation initiatives for our Nations Department of Defense, DISA, Army and Cyber programs.  In this role I support multi-vendor, high risk/reward integration projects, including rapid software development and Datacenter enterprise networking and automation that enables business processes, transforms networks and provides operations automation.

### Problem Statement

Human Activity Recognition or HAR for short, is the problem of predicting what a person is doing based on a trace of their movement using sensors.  The idea is that once the subject’s activity is recognized and known, an intelligent computer system can then offer assistance.

Movements are often normal indoor activities such as standing, sitting, jumping, and going up stairs. Sensors are often located on the subject such as a smartphone or vest and often record accelerometer data in three dimensions (x, y, z).

It is a challenging problem because there is no clear analytical way to relate the sensor data to specific actions in a general way. It is technically challenging because of the large volume of sensor data collected (e.g. tens or hundreds of observations per second) and the classical use of hand crafted features and heuristics from this data in developing predictive models.

Classical approaches to the problem involve hand crafting features from the time series data based on fixed-size windows and training machine learning models, such as ensembles of decision trees. The difficulty is that this feature engineering requires deep expertise in the field.

Human activity recognition is the problem of classifying sequences of accelerometer data recorded by specialized harnesses or smart phones into known well-defined movements.


### Datasets and Inputs 


### Solution Statement
Recently, deep learning methods such as recurrent neural networks and one-dimensional convolutional neural networks or CNNs have been shown to provide state-of-the-art results on challenging activity recognition tasks with little or no data feature engineering.

### Benchmark Model




### Evaluation Metrics


### Project Design
The solution will first process the datasets by mapping information in the files to "strings" that can be extracted and collected, and then features created for the strings, and the feature vectors will be processed by tokenizing, and the data will be sorted into 1.


Human Activity Recognition
2.	Problem Description
3.	Load Dataset
4.	Plot Traces for a Single Subject
5.	Plot Total Activity Durations
6.	Plot Traces for Each Subject
7.	Plot Histograms of Trace Observations
8.	Approaches to Modeling the Problem
  

The solution then proposes a convolutional neural network designed to take a

The workflow for the solution is as follows:
#### Collect
1. Prepare training set and test set for malware and benign respectively
2. Select features (which will be the printable strings) from datasets, and convert them to feature vectors
#### Extract
3. Provide a hashing function to tokenize or compress the strings, this will reduce the features. 
4. Extract all the feature vectors. 
5. Create a generator to break the data to be trained into batches. 
#### Explore
6. Explore my data to show the distribution information of the dataset. Work will be done to classify the files into malware families
 using a classifier from sklearn such as DecisionTrees,RandomForestClassifier or SVM. 
#### Train
7. Decide on a classifier that will be used for the CNN.
8. Split the data into Training and Test sets.
9. Train the data and validate then and create and save the best model.
#### Test
10. Test the trained model.  First take and scan the Test data file, and collect it's features, get the feature vector, and then test the feature vector against the trained classifier model obtaining the class prediction.  The classifier outputs the class prediction {benign, malicious} of the test file. 
#### Evaluate
11. Finally, use the Test data results to evaluate the performance with a ROC curve. The raw classifier output (i.e., probability distribution) will be used to compute the average accuracy, false positive and false negative rate, and Receiver Operating Characteristic (ROC) graphs Score and compute and ROC Curve.

**References:**
[1] Jindong Wang, Yiqiang Chen, Shuji Hao, Xiaohui Peng, Lisha Hu, Deep Learning for Sensor-based Activity Recognition: A Survey, https://arxiv.org/abs/1707.03502, arXiv:1707.03502v2 [cs.CV],  14 Dec 2017

[2] Mohammad Abu Alsheikh and Ahmed Selim and Dusit Niyato Linda Doyle and Shaowei Lin and Hwee-Pink Tan, Deep Activity Recognition Models with Triaxial Accelerometers, https://arxiv.org/abs/1511.04664, arXiv:1511.04664v2 [cs.LG],  25 Oct 2016 https://arxiv.org/pdf/1511.04664.pdf

**Links**

