# Machine Learning Engineer Nanodegree
## Capstone Proposal
Glenn Mossy 
November 2, 2019

## Proposal - A Machine Learning based malware detector
_(approx. 2-3 pages)_

### Domain Background
Malware is vindictive programming and today the availability of malevolent code writing instruments makes it simple for anyone to assemble noxious code, and consequently, malware ranges classic computer viruses to worms, to ransomware to Internet worms and botnets have become one of the major threats on the Internet today. The 2019 McAfee report https://www.mcafee.com/enterprise/en-us/assets/reports/rp-quarterly-threats-aug-2019.pdf confirms ransomware incidents increased by 118 percent during the first quarter of 2019, and the FBI recently as October 2nd, 2019 issued a high-impact alert in the increase in ransomware attacks across all sectors, https://www.ic3.gov/media/2019/191002.aspx. According to cybersecurity firm Recorded Future, which tracks the attacks, from Jan to Oct of 2019, 140 local governments, police stations and hospitals have been held hostage by ransomware attacks https://www.cnn.com/2019/10/08/business/ransomware-attacks-trnd/index.html.  Also according to the recent AT&T Cybersecurity Insights report, vol 6, malware is perceived as the top threat, https://www.business.att.com/content/dam/attbusiness/reports/cybersecurity-report-v6.pdf.  
In addition, Gartner predicts 20.4 billion devices will be installed on the internet by 2020, producing a proliferation of targets for a large and well-organized criminal market which systematically comprises all types of computers and mobile devices. Often, malware is only the precursor to an attack, not the ultimate objective. Initial intrusion leads to more sophisticated and stealthy techniques, such as “living off the land” tradecraft that uses legitimate tools already present on the target system to accomplish hostile objectives. 

Ransomware, which is a form a malware that encrypts files on a victim's computer, or mobile device making them unusable and request payment from the victim to get their data back, distribution of phishing, or spam messages or gathering of confidential data inflicting millions in financial loss and to enterprises, business, and consumers users of all types.

The malware that runs on computers each have a particular "behavior" which are grouped together into the same malware “family”, that are known to have the same form of malicious behavior.  In order to evade detection, the creators of the malware introduce polymorphism to the malicious components, and are using innovative techniques. This means that malicious files are constantly modified and/or obfuscated using various tactics, changing the behavior to evade detection, with a constantly increasing amount of files and malware families.  This diversity of malware renders classic security techniques, such as anti-virus scanners, ineffective and as a consequence, millions of computers and devices connected to the Internet are currently infected with malware. 
A first step in effectively analyzing and classifying malware files is to group them and identify their respective families.  Anti-malware vendors to use this grouping criteria is used as a way to detect the malicious behaviors and develop counter-mechanisms for finding and them.  Machine learning can be applied as a countermeasure against malware to automate the detection because the stakes around cybersecurity continue to rise and human security analysts take an average of 30 minutes to triage each detected threat. So the challenge is around to apply automated detection methods faster with accuracy.

My interest in this field stems from my work with AT&T Public sector where I am a Senior Solutions Architect providing technical leadership on Technology Innovation initiatives for our Nations Department of Defense, DISA, Army and Cyber programs.  In this role I support multi-vendor, high risk/reward integration projects, including rapid software development and Datacenter enterprise networking and automation that enables business processes, transforms networks and provides operations automation.


### Problem Statement
Many anti-malware defensive solutions have failed to detect the unknown malware since most of them rely on signature-based technique. This technique can detect a malware based on a pre-defined signature, which achieves poor performance when attempting to classify unseen malware that constantly evade detection using various code obfuscation techniques. 
The goal is to build a malware supervised machine learning neural network based detection model that accurately predicts types of malware using static analysis.  Where the strings descriptors from the binaries are used as the features in the model, and the model is trained on the malware (labeled 1) and the beignware (labeled 0).  
This model would help apply automated detection faster and with greater accuracy and can be optimized in a number of ways for detection accuracy. An ideal model would give detection rates for malware in which we can quality it's effectiveness by measuring the ability in achieving a low false positive rate (FPR).  

### Datasets and Inputs 
There will be two different datasets having different sizes and distributions of benign and malicious files. The first dataset is from virustotal.com and total of 1,419 sample binaries as a sample dataset consisting of 991 (clean) beignware samples and 428 malware samples.  The malware samples will be representative of the kind of malware observed on the internet in 2017 and the beignware samples of what was uploaded to virustotal.com in 2017.  One unfortunate aspect of the field of malware detection is that there is no available public dataset for various reasons. The dataset easily obtainable from public is often not of a sufficient quality, so previous studies could not compare performance (i.e., accuracy) across works because of different data characteristics and labelling procedures. It is inevitably hard to compare our performance with other state-of-the-art studies for the same reason. We compare our network with some comparative machine-learning methods and CNN models with different settings. 
A binary program file contains "strings" that can be extracted and these will allow for collection of the features for the model that will be trained on. These strings can be called "feature vectors". "A feature vector is an n-dimensional vector that contains essential information that describes the characteristics of an object. For example, it can be an object’s numerical features or a list of numbers taken from the output of a neural network layer.  These feature vectors will be assigned into the categories of beignware (0) or malware (1). These features will tokenized as the features using the techniques explained in the solution statement.

I will obtain additional datasets, but this will be the starting dataset, and then I will obtain additional datasets and add to this.
The dataset will be divided into 3 subsets:
        A training set, with 70% of the samples, used for training.
        A validation set, with 15% of the samples, used to benchmark the model at each training epoch.
        A test set, with 15% of the samples, used to benchmark the model after training.

### Solution Statement

A challenge is to detect malware that has just been freshly released in the to wild of the internet, these are called "zero-day attacks".  Although signature based detection techniques are being used widely, they are not effective against “zero-day attacks” and various “obfuscation” techniques. Signature based techniques are also hopeless against new attacks. So, there is a growing need for fast, automated, and efficient detection techniques that can also detect zero-day attacks.

The solution presented in this paper will be to create an offline or "static" malware detector, then prove the effectiveness of our model and show that our method is able to detect unknown malicious samples to a good degree of accuracy. Offline detection means that this method cannot be directly deployed on a network to detect malicious code in real time. 
First, Static information will be extracted of the PE, html, or script files: printable strings, opcodes, import tables, informational entropy, byte n-grams (i.e., n consecutive bytes), or feature vectors. These basic features will be extracted using approaches which have been used in previously published works. The second stage records the feature vectors extracted from the binary of the files and prepares them to be processed by a convolutional neural network (CNN).  Finally, we train and classify the images using designed model based on CNN. The solution will try several combinations of features and learning algorithms and compares their relative merits.  Different machine learning models may be used to improve the performance of the detector. 

### Benchmark Model
One useful metric for evaluating the accuracy of a binary predictor is called the area under the curve (AUC).  The curve refers to a Receiver Operating Characteristic (ROC) curve, which plots false-positive rates on the x-axis against true-positive on the y-axis for all possible thresholds. This ROC metric will be used to determine our detector's accuracy.  Accuracy metrics in research papers have shown various advanced techniques that achieve an AUC of typically 90% - 95% accuracy rates, but advanced methods using combined static and dynamic analysis have achieved an even higher 97% detection rate positive for malware.

### Evaluation Metrics
The metric for evaluating the accuracy of a binary predictor that will be used is called the area under the curve (AUC) and refers to a Receiver Operating Characteristic (ROC) curve. 
Our model will try to predict whether a file is malicious by using a score between 0 (benign) and 1 (malicious).  If we choose a relatively high score threshold to classify a file as malicious we'll get fewer false-positives which is good, but also fewer true-positives which is bad.  On the other hand, if we choose a low score threshold, we'll likely have a high false-positive rate which is bad, but a very high detection rate which is good. 
The sample possibilities will be represented as two points on our models ROC curve, with the first located on the left side and curve and the second near the right side.   We calculate the area under the curve and that will represent the predictive capability and show the detectors accuracy.
So the ROC curve will measure the changes in the detector's true positive rate (the percentage of malware that it successfully detects) and the false positive rate, (the percentage of beignware that it falsely flags as malware as the sensitivity is adjusted.  The higher the sensitivity, we will have more false positives, but a greater detection rate.  I would expect the model to be able to achieve between 90% - 95% detection rate which will be shown with an ROC curve. 
The detector will output a threat score such that the higher it's value the more likely that the file is malicious.  
Sklearns implementations of decision trees, logistic regression, k-nearest neighbors, random forest and other approaches all provide the option of computing a threat score to reflect whether a file is malware or benignware.

### Project Design
_(approx. 1 page)_

In this final section, summarize a theoretical workflow for approaching a solution given the problem. Provide thorough discussion for what strategies you may consider employing, what analysis of the data might be required before being used, or which algorithms will be considered for your implementation. The workflow and discussion that you provide should align with the qualities of the previous sections. Additionally, you are encouraged to include small visualizations, pseudocode, or diagrams to aid in describing the project design, but it is not required. The discussion should clearly outline your intended workflow of the capstone project.

The solution will first process the datasets by mapping information in the files to "strings" that can be extracted and collected, and then features created for the strings, and the feature vectors will be processed by tokenizing, and the data will be sorted into batches.  Exploratory analysis will be done on the datasets to understand if we can classify and group the malware into "families".  

The solution then proposes a convolutional neural network designed to take a byte sequence of non-executables as an input using collection of the features for the model to train on. The solution will take test data and predict whether the given sequence has malicious actions or not. An evaluation of the prediction will be done to score the results.  It will be illustrated as to how design the network according to the characteristics of the input data and provide discussion about the experiments using the manually labelled dataset. The project's experimental results will attempt to show if the proposed network outperforms several representative machine-learning models with different settings. The approach may use only a certain type of files, but it is expected that this approach can be applicable to other types of data if they contain byte streams.

The workflow for the solution is as follows:
# Collect
1. Prepare training set and test set for malware and benign respectively
2. Select features (which will be the printable strings) from datasets, and convert them to feature vectors
# Extract
3. Provide a hashing function to tokenize or compress the strings, this will reduce the features. 
4. Extract all the feature vectors. 
5. Create a generator to break the data to be trained into batches. 
# Explore
 7. Explore my data to show the distribution information of the dataset. Work will be done to classify the files into malware families
 using a classifier from sklearn such as DecisionTrees,RandomForestClassifier or SVM. 
 
# Train
8. Decide on a classifier that will be used for the CNN.
9. Split the data into Training and Test sets.
10. Train the data and validate then and create and save the best model.
# Test
11. Test the trained model.  First take and scan the Test data file, and collect it's features, get the feature vector, and then test the feature vector against the trained classifier model obtaining the class prediction.  The classifier outputs the class prediction {benign, malicious} of the test file. 
# Evaluate
12. Finally, use the Test data results to evaluate the performance with a ROC curve. The raw classifier output (i.e., probability distribution) will be used to compute the average accuracy, false positive and false negative rate, and Receiver Operating Characteristic (ROC) graphs Score and compute and ROC Curve.

**Before submitting your proposal, ask yourself. . .**

- Does the proposal you have written follow a well-organized structure similar to that of the project template?
- Is each section (particularly **Solution Statement** and **Project Design**) written in a clear, concise and specific fashion? Are there any ambiguous terms or phrases that need clarification?
- Would the intended audience of your project be able to understand your proposal?
- Have you properly proofread your proposal to assure there are minimal grammatical and
spelling mistakes?
- Are all the resources used for this project correctly cited and referenced?

**References:**
[1]   Saxe J., Harang R., Wild C., Sanders H., A Deep Learning Approach to Fast, Format-Agnostic Detection of Malicious Web Content by  https://arxiv.org/pdf/1804.05020.pdf, arXiv:1804.05020v1 [cs.CR] 13 Apr 2018

[2]

[3] Rieck K., Trinius P., Willems C., and Holz T., Automatic Analysis of Malware Behavior using Machine Learning
http://www.mlsec.org/malheur/docs/malheur-jcs.pdf, Journal of Computer Security, IOS Press, http://www.iospress.nl, 2011

[4] Kaspersky lab, https://media.kaspersky.com/en/enterprise-security/Kaspersky-Lab-Whitepaper-Machine-Learning.pdf, 2019

[5] Masud M.M., Khan L., Thuraisingham B., https://personal.utdallas.edu/~bxt043000/Publications/Conference-Papers/DAS/C82_A_Hybrid_Model_to_Detect_Malicious_Executables.pdf, IEEE Communications Society, 2007

**Links**
McAfee report https://www.mcafee.com/enterprise/en-us/assets/reports/rp-quarterly-threats-aug-2019.pdf, 2019 
https://www.ic3.gov/media/2019/191002.aspx
https://www.cnn.com/2019/10/08/business/ransomware-attacks-trnd/index.html
https://www.business.att.com/content/dam/attbusiness/reports/cybersecurity-report-v6.pdf
