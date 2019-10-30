# Machine Learning Engineer Nanodegree
## Capstone Proposal
Glenn Mossy 
October 29, 2019

## Proposal - A Machine Learning based malware detector
_(approx. 2-3 pages)_

### Domain Background

Malware is vindictive programming and today the availablity of malevolent code writing instruments makes it simple for anyone to assemble noxious code, and consequently, malware ranges classic computer viruses to worms, to ransomware to Internet worms and botnets have become one of the major threats on the Internet today. The 2019 McAfee report https://www.mcafee.com/enterprise/en-us/assets/reports/rp-quarterly-threats-aug-2019.pdf confirms ransomware incidents increased by 118 percent during the first quarter of 2019, and the FBI recently as October 2nd, 2019 issued a high-impact alert in the increase in ransomware attacks across all sectors, https://www.ic3.gov/media/2019/191002.aspx. According to cybersecurity firm Recorded Future, which tracks the attacks, from Jan to Oct of 2019, 140 local governments, police stations and hospitals have been held hostage by ransomware attacks https://www.cnn.com/2019/10/08/business/ransomware-attacks-trnd/index.html.  Also according to the recent AT&T Cybersecurity Insights report, vol 6, malware is perceived as the top threat, https://www.business.att.com/content/dam/attbusiness/reports/cybersecurity-report-v6.pdf.  
In addition, Gartner predicts 20.4 billion devices will be installed on the internet by 2020, producing a poliferation of targets for a large and well-organized criminal market which systematically comprises all types of computers and mobile devices. Often, malware is only the precursor to an attack, not the ultimate objective. Initial intrusion leads to more sophisticated and stealthy techniques, such as “living off the land” tradecraft that uses legitimate tools already present on the target system to accomplish hostile objectives. 

Ransomware, which is a form a malware that encrypts files on a victim's computer, or mobile device making them unusable and request payment from the victim to get their data back, distribution of phishing, or spam messages or gathering of confidential data inflicting millions in financial loss and to enterprises, business, and consumers users of all types.

The malware that runs on computers each have a particular "behavoir" which are grouped together into the same malware “family”, that are know to have the same form of malicious behavior.  In order to evade detection, the creators of the malware introduce polymorphism to the malicious components, and are using innovative techniques. This means that malicious files are constantly modified and/or obfuscated using various tactics, changing the behavoir to evade detection, with a constantly increasing amount of files and malware families.  This diversity of malware renders classic security techniques, such as anti-virus scanners, ineffective and as a consequence, millions of computers and devices connected to the Internet are currently infected with malware. 
A first step in effectively analyzing and classifying malware files is to group them and identify their respective families.  Anti-malware vendors to use this grouping criteria is used as a way to detect the malicious behavoirs and develop counter-mechanisms for finding and them.  Machine learning can be applied as a countermeasure against malware to automate the detection because the stakes around cybersecurity continue to rise and human security analysts take an average of 30 minutes to triage each detected threat. So the challange is around to apply automated detection methods faster with accuracy.

My interest in this field stems from my work with AT&T Public sector where I am a Senior Solutions Architect providing technical leadership on Technology Innovation initiatives for our Nations Department of Defense, DISA, Army and Cyber programs.  In this role I support multi-vendor, high risk/reward integration projects, including rapid software development and Datacenter enterprise networking and automation that enables business processes, transforms networks and provides operations automation.

### Problem Statement
Many anti-malware defensive solutions have failed to detect the unknown malware since most of them rely on signature-based technique. This technique can detect a malware based on a pre-defined signature, which achieves poor performance when attempting to classify unseen malware that constantly evade detection using various code obfuscation techniques. 

The goal is to build a malware supervised machine learning neural network based detection model that accurately predicts types of malware using static analysis.  Where the strings descriptors from the binaries are used as the features in the model, and the model is trained on the malware (labeled 1) and the beignware (labeled 0).  
This model would help apply automated detection faster and with greater accuracy and can be optimized in a number of ways for detection accuracy. An ideal model would give detection rates for malware in which we can quality it's effectivenes by measuring the ability in acheiving a low false positive rate (FPR).  

### Datasets and Inputs 
The dataset is from virustotal.com and 1,419 sample binaries as a sample dataset, that consists of 991 (clean) benignware samples and 428 malware samples. The malware samples are representative of the kind of malware observered on the internet in 2017 and the benignware samples of what was uploaded to virustotal.com in 2017. 
A binary program file contains "strings" that can be extracted and these will provided the features for the model that will be trained on.  The string features will be assigned into the categories of beignware (0) or malware (1). These features will tokenized as the features. 

I will obtain additional datasets, but this will be the starting dataset, and then I will obtain additional datasets and add to this.
The dataset will be divided into 3 subsets:
        A training set, with 70% of the samples, used for training.
        A validation set, with 15% of the samples, used to benchmark the model at each training epoch.
        A test set, with 15% of the samples, used to benchmark the model after training.

### Solution Statement
The solution will be to create a malware detector, prove the effectiveness of our model and show that our method is able to detect unknown malicious samples well.
First, Static information will be extracted of PE file: printable strings, opcodes, import tables, informational entropy and byte n-grams. We extract some basic features using approaches which have been used in previously published works. The second stage records the strings extracted from the binary of the files and processes them by a CNN.  Finally, we train and classify the images using designed model based on CNN. 

The solution attempts to detect malicious web content by manually extracting features from HTML and Javascript, then feeds
this information to machine learning algorithms.  The solution will try several combinations of features and learning algorithms and
compare their relative merits.  Different machine learning models may be used to improve the performance of the detector. 

### Benchmark Model
One useful metric for evaluating the accuracy of a binary predictor is called the area under the curve (AUC).  The curve refers to a Receiver Operating Characteristic (ROC) curve, which plots false-positive rates on the x-axis against true-positive  on the y-axis for all possible thresholds. This ROC metric will be used to determine our detector's accuracy.  Accuracy metrics in research papers have shown various advanced techniques that achieve an AUC of typically 90% - 95% accuracy rates, but advanced methods using combined static and dynamic analysis have achieved an even higher 97% detection rate positive for malware.

### Evaluation Metrics
The metric for evaluating the accuracy of a binary predictor that will be used is called the area under the curve (AUC) and refers to a Recievier Operating Characteristic (ROC) curve. 
Our model will try to predict whether a file is malicious by using a score between 0 (benign) and 1 (malicious).  If we choose a relitively high score threshold to classify a file as malicious we'll get fewer false-positives which is good, but also fewer true-positives which is bad.  On the other hand, if we choose a low score threshold, we'll likely have a high false-positive rate which is bad, but a very high detection rate which is good. 
The sample possiblities will be represented as two points on our models ROC curve, with the first located on the left side and curve and the second near the right side.   We calculate the area under the curve and that will represent the predictive capablity and show the detectors accuracy.

So the ROC curve will measure the changes in the detector's true positive rate (the percentage of malware that it successfully detects) and the false positive rate, ( the percentage of benignware that it falsely flags as malware as the sensitivity is adjusted.  The higher the sensitivity, we will have more false positives, but a greater detection rate.  I would expect the model to be able to achieve between %90 - %95 detection rate which will be shown with an ROC curve. 

The detector will output a threat score such that the higher it's value the more likely that the file is malicious.  
Sklearns implementations of decision trees, logistic regression, k-nearest neighbors, random forest and other approaches all provide the option of computing a threat score to reflect whether a file is malware or benignware. 

### Project Design
_(approx. 1 page)_

In this final section, summarize a theoretical workflow for approaching a solution given the problem. Provide thorough discussion for what strategies you may consider employing, what analysis of the data might be required before being used, or which algorithms will be considered for your implementation. The workflow and discussion that you provide should align with the qualities of the previous sections. Additionally, you are encouraged to include small visualizations, pseudocode, or diagrams to aid in describing the project design, but it is not required. The discussion should clearly outline your intended workflow of the capstone project.

The workflow for the solution is as follows:
-1.Prepare training set and test set for malware and benign respectively
-2.Select features (which will be the printable strings) from datasets, and convert them to feature vectors
-3.Provide a hashing function to tokenize or compress the strings, this will reduce the features. 
-4.Create a generator to break the data to be trained into batches. 
-5.Explore my data.
-6.Decide on a classifier that will be used for the CNN, such as sklearn's RandomForestClassifier. 
-7.Split the data into Training and Test sets. 
-8.Train the data and valildate then and create and save the best model.
-9.Score and compute and ROC Curve.
-8.Use Test data to evaluate the performance with a ROC curve. 

**Before submitting your proposal, ask yourself. . .**

- Does the proposal you have written follow a well-organized structure similar to that of the project template?
- Is each section (particularly **Solution Statement** and **Project Design**) written in a clear, concise and specific fashion? Are there any ambiguous terms or phrases that need clarification?
- Would the intended audience of your project be able to understand your proposal?
- Have you properly proofread your proposal to assure there are minimal grammatical and
spelling mistakes?
- Are all the resources used for this project correctly cited and referenced?

References:
[1] A Deep Learning Approach to Fast, Format-Agnostic Detection of Malicious Web Content by Joshua Saxe1, Richard Harang, Cody Wild, Hillary Sanders
https://arxiv.org/pdf/1804.05020.pdf

[2]
https://www.ffri.jp/assets/files/monthly_research/MR201306_Machine_learning_for_computer_security_ENG.pdf

[3]
http://www.mlsec.org/malheur/docs/malheur-jcs.pdf
[4]
https://media.kaspersky.com/en/enterprise-security/Kaspersky-Lab-Whitepaper-Machine-Learning.pdf




