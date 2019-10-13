# Machine Learning Engineer Nanodegree
## Capstone Proposal
Glenn Mossy 
October 11, 2019

## Proposal - Automatic Malware Analysis using Machine Learning 
_(approx. 2-3 pages)_

### Domain Background
_(approx. 1-2 paragraphs)_

In this section, provide brief details on the background information of the domain from which the project is proposed. Historical information relevant to the project should be included. It should be clear how or why a problem in the domain can or should be solved. Related academic research should be appropriately cited in this section, including why that research is relevant. Additionally, a discussion of your personal motivation for investigating a particular problem in the domain is encouraged but not required.

Malware which is vindictive programming, today the availablity of malevolent code writing instruments make it simple for anyone to assemble noxious code, and consequently, malware ranging from classic computer viruses to Internet worms and bot networks have become one of the major threats on the Internet today and has gone mainstream. The 2019 McAfee report https://www.mcafee.com/enterprise/en-us/assets/reports/rp-quarterly-threats-aug-2019.pdf confirms ransomware incidents increased by 118 percent during the first quarter of 2019, and the FBI recently as October 2nd, 2019 issued a high-impact alert in the increase in ransomware attacks across all sectors, state and local governments, and other infrastructure targets https://www.ic3.gov/media/2019/191002.aspx. In addition, Gartner predicts 20.4 billion devices will be installed on the internet by 2020, producing a poliferation of targets for large and well-organized criminal market which systematically comprises computers and mobile devices. Malware looms as a primary feature of the threat landscape and according to the recent AT&T Cybersecurity Insights report, vol 6, malware is perceived as the top threat, https://www.business.att.com/content/dam/attbusiness/reports/cybersecurity-report-v6.pdf.  Often, malware is only the precursor to an attack, not the ultimate objective. Initial intrusion leads to more sophisticated and stealthy techniques, such as “living off the land” tradecraft that uses legitimate tools already present on the target system to accomplish hostile objectives. 

Malware which ranges from viruses to worms, to ransomware which is a form a malware that encrypts files on a victim's computer, or mobile device making them unusable and request payment from the victim to get their data back, distribution of phishing, or spam messages or gathering of confidential data inflicting millions in financial loss and to enterprises of all types, business users, and consumer users on enterprise systems, desktop, mobile, and IoT devices.  

The malware that runs on computers each have a particular "behavoir" which are grouped together into the same malware “family”, that are know to have the same form of malicious behavior.  In order to evade detection, the creators of the malware introduce polymorphism to the malicious components, and are using innovative techniques. This means that malicious files are constantly modified and/or obfuscated using various tactics, changing the behavoir to evade detection, with a constantly increasing amount of files and malware families.  This diversity of malware renders classic security techniques, such as anti-virus scanners, ineffective and as a consequence, millions of computers and devices connected to the Internet are currently infected with malware. 
A first step in effectively analyzing and classifying malware files is to group them and identify their respective families.  Anti-malware vendors to use this grouping criteria is used as a way to detect the malicious behavoirs and develop counter-mechanisms for finding and them.  Machine learning can be applied as a countermeasure against malware to automate the detection because the stakes around cybersecurity continue to rise and human security analysts take an average of 30 minutes to triage each detected threat. So the challange is around to apply automated detection methods faster with accuracy.

My interest in this field stems from my work with AT&T Public sector where I am a Senior Solutions Architect providing technical leadership on Technology Innovation initiatives for our Nations Department of Defense, DISA, Army and Cyber programs.  In this role I support multi-vendor, high risk/reward integration projects, including rapid software development and Datacenter enterprise networking and automation that enables business processes, transforms networks and provides operations automation.

### Problem Statement
_(approx. 1 paragraph)_

In this section, clearly describe the problem that is to be solved. The problem described should be well defined and should have at least one relevant potential solution. Additionally, describe the problem thoroughly such that it is clear that the problem is quantifiable (the problem can be expressed in mathematical or logical terms) , measurable (the problem can be measured by some metric and clearly observed), and replicable (the problem can be reproduced and occurs more than once).

Many anti-malware defensive solutions have failed to detect the unknown malware since most of them rely on signature-based technique. This technique can detect a malware based on a pre-defined signature, which achieves poor performance when attempting to classify unseen malware that constantly evade detection using various code obfuscation techniques. 

The goal is to build a model that predicts ...
This model would help apply automated detection methods faster and with greater accuracy.



### Datasets and Inputs
_(approx. 2-3 paragraphs)_

In this section, the dataset(s) and/or input(s) being considered for the project should be thoroughly described, such as how they relate to the problem and why they should be used. Information such as how the dataset or input is (was) obtained, and the characteristics of the dataset or input, should be included with relevant references and citations as necessary It should be clear how the dataset(s) or input(s) will be used in the project and whether their use is appropriate given the context of the problem.

The dataset provided by ..  includes ....  The training set contains more than ....  The testing set contains.   ...


### Solution Statement
_(approx. 1 paragraph)_

In this section, clearly describe a solution to the problem. The solution should be applicable to the project domain and appropriate for the dataset(s) or input(s) given. Additionally, describe the solution thoroughly such that it is clear that the solution is quantifiable (the solution can be expressed in mathematical or logical terms) , measurable (the solution can be measured by some metric and clearly observed), and replicable (the solution can be reproduced and occurs more than once).

The solution is classification models capable of predicting the families that the malware belongs too.  





### Benchmark Model
_(approximately 1-2 paragraphs)_

In this section, provide the details for a benchmark model or result that relates to the domain, problem statement, and intended solution. Ideally, the benchmark model or result contextualizes existing methods or known information in the domain and problem given, which could then be objectively compared to the solution. Describe how the benchmark model or result is measurable (can be measured by some metric and clearly observed) with thorough detail.

### Evaluation Metrics
_(approx. 1-2 paragraphs)_

In this section, propose at least one evaluation metric that can be used to quantify the performance of both the benchmark model and the solution model. The evaluation metric(s) you propose should be appropriate given the context of the data, the problem statement, and the intended solution. Describe how the evaluation metric(s) are derived and provide an example of their mathematical representations (if applicable). Complex evaluation metrics should be clearly defined and quantifiable (can be expressed in mathematical or logical terms).

### Project Design
_(approx. 1 page)_

In this final section, summarize a theoretical workflow for approaching a solution given the problem. Provide thorough discussion for what strategies you may consider employing, what analysis of the data might be required before being used, or which algorithms will be considered for your implementation. The workflow and discussion that you provide should align with the qualities of the previous sections. Additionally, you are encouraged to include small visualizations, pseudocode, or diagrams to aid in describing the project design, but it is not required. The discussion should clearly outline your intended workflow of the capstone project.

Steps
-1.Prepare training set and test set for malware and benign respectively
-2.Select features from datasets, and convert them to feature vectors
-  •Basically, the task of expert about applied field
-  •Select features based on each own experience and knowledge
-  •Extracted API calls log recorded by Cuckoo Sandbox
-3.Train by feature vectors added label(malware or benign)
-4.Classify the test set by extracting FV from them
-   Keras for machine learning framework
-----------

**Before submitting your proposal, ask yourself. . .**

- Does the proposal you have written follow a well-organized structure similar to that of the project template?
- Is each section (particularly **Solution Statement** and **Project Design**) written in a clear, concise and specific fashion? Are there any ambiguous terms or phrases that need clarification?
- Would the intended audience of your project be able to understand your proposal?
- Have you properly proofread your proposal to assure there are minimal grammatical and
spelling mistakes?
- Are all the resources used for this project correctly cited and referenced?

References:
[1]
https://www.ffri.jp/assets/files/monthly_research/MR201306_Machine_learning_for_computer_security_ENG.pdf

[2]
http://www.mlsec.org/malheur/docs/malheur-jcs.pdf


