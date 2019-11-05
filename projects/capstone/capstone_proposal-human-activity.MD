# Machine Learning Engineer Nanodegree
## Capstone Proposal
Glenn Mossy 
November 2, 2019

## Proposal - A Deep Learning Based Human Activity Recognizer.
### Domain Background
Human activity recognition (HAR) plays an important role in people’s daily life for its competence in learning profound high-level knowledge about human activity from raw sensor inputs. [1]
Human Activity Recognition has a very wide applications ranging from security-related
applications, logistics support,  location-based services and that of helping handicapped or elderly people to live more independently, rate health levels and provide safety. 

Many additional sensors, such as microphones, motion video capture, human vital signs could be later added to this project in order to capture data to provide features to the model that would improve the accuracy, and increase the number of activities that can be understood, with the ultimate goal of providing a prediction of each and every activity that the person is doing. 

Our work has a wide range of applications, including automatic customization of the mobile device’s behavior based upon a
user’s activity (e.g., sending calls directly to voicemail if a user is jogging) and generating a daily/weekly activity profile to determine if a user is performing a healthy amount of exercise. 
there are many useful applications that can be built if accelerometers can be used to recognize a user’s activity. For example, we can automatically monitor a user’s activity level and generate daily, weekly,
The topic of accelerometer-based activity recognition is not new  focused on how one can use a variety of accelerometer based devices to identify a range of user activities [4-7, 9-16, 21].
Other work has focused on the applications that can be built based on accelerometer-based activity recognition.


My interest in this field stems from my work with AT&T Public sector where I am a Senior Solutions Architect providing technical leadership on Technology Innovation initiatives for our Nations Department of Defense, DISA, Army and Cyber programs.  In this role I support multi-vendor, high risk/reward integration projects, including rapid software development and Datacenter enterprise networking and automation that enables business processes, transforms networks and provides operations automation.  I am also an adjunct instruction at Frederick Community College teaching students how to program arduino microcontrollers and sensors to interact with the physical environment. 





### Problem Statement

Human Activity Recognition or HAR for short, is the problem of predicting what a person is doing based on a trace of their movement using sensors.  The idea is that once the subject’s activity is recognized and known, an intelligent computer system can then offer assistance.

Movements are often normal indoor activities such as standing, sitting, jumping, and going up stairs. Sensors are often located on the subject such as a smartphone or vest and often record accelerometer data in three dimensions (x, y, z).

In this paper we explore the results of the ability for a model to identify a user is performing—a task or activity they are doing by use of a sensor, the accelerometer, this is refered to as activity recognition. 

It is a challenging problem because there is no clear analytical way to relate the sensor data to specific actions in a general way. It is technically challenging because of the large volume of sensor data collected (e.g. tens or hundreds of observations per second) and the classical use of hand crafted features and heuristics from this data in developing predictive models.

Classical approaches to the problem involve hand crafting features from the time series data based on fixed-size windows and training machine learning models, such as ensembles of decision trees. The difficulty is that this feature engineering requires deep expertise in the field.

Human activity recognition is the problem of classifying sequences of accelerometer data recorded by specialized harnesses or smart phones into known well-defined movements.


### Datasets and Inputs 
https://archive.ics.uci.edu/ml/datasets/Smartphone-Based+Recognition+of+Human+Activities+and+Postural+Transitions
or 
https://acadgild.com/blog/4logistic-regression-case-study-2

This project uses the dataset “Activity Recognition from Single Chest-Mounted Accelerometer Data Set” was collected and made available by Casale, Pujol et al. from the University of Barcelona in Spain. It is freely available from the UCI Machine Learning repository:

https://archive.ics.uci.edu/ml/datasets/Activity+Recognition+from+Single+Chest-Mounted+Accelerometer

The dataset is comprised of un-calibrated accelerometer data from 15 different subjects, each performing 7 activities. Each subject wore a custom-developed chest-mounted accelerometer and data was collected at 52 Hz(52 observations per second).

Data Set Information:
--- The dataset collects data from a wearable accelerometer mounted on the chest 
--- Sampling frequency of the accelerometer: 52 Hz 
--- Accelerometer Data are Uncalibrated 
--- Number of Participants: 15 
--- Number of Activities: 7 
--- Data Format: CSV

Attribute Information:
--- Data is separated by participant 
--- Each file contains the following information 
---- sequential number, x acceleration, y acceleration, z acceleration, label 
--- Labels are codified by numbers 
--- 1: Working at Computer 
--- 2: Standing Up, Walking and Going updown stairs 
--- 3: Standing 
--- 4: Walking 
--- 5: Going UpDown Stairs 
--- 6: Walking and Talking with Someone 
--- 7: Talking while Standing

### Solution Statement
Recently, deep learning methods such as recurrent neural networks and one-dimensional convolutional neural networks or CNNs have been shown to provide state-of-the-art results on challenging activity recognition tasks with little or no data feature engineering.
The solution seeks to achieve very good results with classification accuracy of human activities recognition. 


### Benchmark Model
A benchmark model is a threshold or goal that you're trying to beat with your solution. For most projects you should choose a simple model (something different than your solution). You'd train/test the benchmark model using the same data and conditions as your solution. This allows you to make a clear, objective comparison between the benchmark model and your solution.
For example, a logistic regression model might be a good benchmark model for a classification problem.



### Evaluation Metrics
The objective of this project is to predict the activity performed by the subject accurately, based on accelerometer readings, so, Validation Misclassification rate is chosen as the Assessment Measure to compare the performance of different models. 

### Project Design
To develop an activity recognition model, we will make use of the accelerometer sensor data that was collected and labeled from twenty-nine users as they performed daily activities such as walking, jogging, climbing stairs, sitting, and standing.  
This time series data was then aggregated into examples that summarize the user activity. We then used the resulting training data using supervised learning to induce a deep learning model for activity recognition.

Human Activity Recognition
2.	Problem Description
3.	Load Dataset
4.	Plot Traces for a Single Subject
5.	Plot Total Activity Durations
6.	Plot Traces for Each Subject
7.	Plot Histograms of Trace Observations
8.	Approaches to Modeling the Problem
- Our experiments first require us to collect the labeled raw accelerometer data and then transform that data into examples
- we divided the data into 10-second segments and then generated features that were based on the 200 readings contained
within each 10-second segment. 
- Next we generated informative features based on the 200 raw accelerometer readings, where each reading contained an x, y, and z value corresponding to the three axes/dimensions 
- which is subsequently used for training and testing

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

[3] Kwapisz J., Weiss G., Samuel A. Moore, S., Activity Recognition using Cell Phone Accelerometers, http://www.cis.fordham.edu/wisdm/includes/files/sensorKDD-2010.pdf, 2010


**Links**

