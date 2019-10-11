# Machine Learning Engineer Nanodegree
## Capstone Proposal
Glenn Mossy 
October 11, 2019

## Proposal - Automatic Malware Analysis using Machine Learning 
_(approx. 2-3 pages)_

### Domain Background
_(approx. 1-2 paragraphs)_

In this section, provide brief details on the background information of the domain from which the project is proposed. Historical information relevant to the project should be included. It should be clear how or why a problem in the domain can or should be solved. Related academic research should be appropriately cited in this section, including why that research is relevant. Additionally, a discussion of your personal motivation for investigating a particular problem in the domain is encouraged but not required.

Malicious software, referred to as malware, is one of the major threats on the Internet today.
A plethora of malicious tools, ranging from classic computer viruses to Internet worms
and bot networks, targets computer systems linked to the Internet. Proliferation of this
threat is driven by a criminal industry which systematically comprises networked hosts
for illegal purposes, such as distribution of spam messages or gathering of confidential
data.  (
Today it has gone
mainstream, with creators selling their
products to a broad and eager customer base
that ranges from nation states to hacktivists.
Luckily, most malware variants are known —
meaning the majority of attacks can be blocked
with appropriate safeguards in place.
Malware: 90% of U.S. organizations had at
least one malware-related incident during
the past 12 months3.
Ransomware: 63% of organizations were
confronted with at least one ransomware
incident over the past 12 months4.

reference rising criminal industry numbers here)
https://www.business.att.com/content/dam/attbusiness/reports/vol4-threatlandscape.pdf
https://www.business.att.com/content/dam/attbusiness/infographics/the-cybersecurity-disconnect-infographic.pdf
https://www.business.att.com/content/dam/attbusiness/infographics/cdn-zero-trust-security-model-infographic.pdf

https://www.slideshare.net/CiscoSecurity/malware-infographic-48723818
https://www.kaspersky.com/resource-center/infographics/vulnerable-software
https://www.symantec.com/blogs/feature-stories/cyber-security-predictions-2019-and-beyond
https://www.carbonblack.com/wp-content/uploads/2018/01/cb-threat-report-infographic-2017.pdf


The increasing amount
and diversity of malware render classic security techniques, such as anti-virus scanners,
ineffective and, as a consequence, millions of hosts in the Internet are currently infected
with malicious software
(reference rising criminal industry numbers here)
Type of malware
https://www.google.com/search?rlz=1C1CHBF_enUS782US782&biw=1536&bih=807&tbm=isch&sxsrf=ACYBGNTbi9KWmMnUhuYRqK8BKDVg9vflKA%3A1570767009452&sa=1&ei=oQCgXbOhG4_v_Qb7qrTgDA&q=malware+infographic&oq=malware+infog&gs_l=img.3.0.0l2.20162.23345..25164...2.0..0.84.1017.15......0....1..gws-wiz-img.......0i67j0i10j0i30j0i8i30j0i24.UhQKNMOcSuk#imgrc=RZLM1xGwb1_2qM:

The stakes around cybersecurity continue to rise in a world of devices, cloud technology, and growing networks. Because of this, AI is being applied to previously unsolvable problems within the areas of cyber defense and cyber resilience. Human security analysts take 30 minutes to triage each detected threat. Security breaches can to go undetected for months or years. AI and deep learning provide ways to keep citizens

My interest in this field stems from my work with AT&T Public sector where I am a Senior Solutions Architect providing technical leadership on Technology Innovation initiatives for our Nations Department of Defense, DISA, Army and Cyber programs.  In this role I support multi-vendor, high risk/reward integration projects, including rapid software development and Datacenter enterprise networking and automation that enables business processes, transforms networks and provides operations automation.

### Problem Statement
_(approx. 1 paragraph)_

In this section, clearly describe the problem that is to be solved. The problem described should be well defined and should have at least one relevant potential solution. Additionally, describe the problem thoroughly such that it is clear that the problem is quantifiable (the problem can be expressed in mathematical or logical terms) , measurable (the problem can be measured by some metric and clearly observed), and replicable (the problem can be reproduced and occurs more than once).

Malicious software or malware has grown rapidly and many anti-malware defensive solutions have failed to detect the unknown malware since most of them rely on signature-based technique. This technique can detect a malware based on a pre-defined signature, which achieves poor performance when attempting to classify unseen malware with the capability to evade detection using various code obfuscation techniques. This growing evasion capability of new and unknown malwares needs to be countered by analyzing the malware dynamically in a sandbox environment, since the sandbox provides an isolated environment for analyzing the behavior of the malware. In this paper, the malware is executed on to the cuckoo sandbox to obtain its run-time behavior. At the end of the execution, the cuckoo sandbox reports the system calls invoked by the malware during execution. However, this report is in JSON format and has to be converted to MIST format to extract the system calls. 

### Datasets and Inputs
_(approx. 2-3 paragraphs)_

In this section, the dataset(s) and/or input(s) being considered for the project should be thoroughly described, such as how they relate to the problem and why they should be used. Information such as how the dataset or input is (was) obtained, and the characteristics of the dataset or input, should be included with relevant references and citations as necessary It should be clear how the dataset(s) or input(s) will be used in the project and whether their use is appropriate given the context of the problem.

Malware is the raw-material associated with many cybercrime-related activities. Cuckoo is a lightweight solution that performs automated dynamic analysis of provided Windows binaries. It is able to return comprehensive reports on key API calls and network activity.
Each analysis is launched in a fresh and isolated virtual or physical machine. The main components of Cuckoo’s infrastructure are an Host machine (the management software) and a number of Guest machines (virtual or physical machines for analysis).
The Host runs the core component of the sandbox that manages the whole analysis process, while the Guests are the isolated environments where the malware samples get actually safely executed and analyzed.


### Solution Statement
_(approx. 1 paragraph)_

In this section, clearly describe a solution to the problem. The solution should be applicable to the project domain and appropriate for the dataset(s) or input(s) given. Additionally, describe the solution thoroughly such that it is clear that the solution is quantifiable (the solution can be expressed in mathematical or logical terms) , measurable (the solution can be measured by some metric and clearly observed), and replicable (the solution can be reproduced and occurs more than once).

Incremental analysis of malware behavior. By combining clustering and classification,
we devise an incremental approach to behavior-based analysis capable of processing
the behavior of thousands of malware binaries on a daily basis. This incremental
analysis significantly reduces the run-time and memory overhead of batch analysis
methods, while providing accurate discovery of novel malware.


Steps
1.Prepare training set and test set for malware and benign respectively
2.Select features from datasets, and convert them to feature vectors
  •Basically, the task of expert about applied field
  •Select features based on each own experience and knowledge
  •Extracted API calls log recorded by Cuckoo Sandbox
3.Train by feature vectors added label(malware or benign)
4.Classify the test set by extracting FV from them
  • Keras for machine learning framework


### Benchmark Model
_(approximately 1-2 paragraphs)_

In this section, provide the details for a benchmark model or result that relates to the domain, problem statement, and intended solution. Ideally, the benchmark model or result contextualizes existing methods or known information in the domain and problem given, which could then be objectively compared to the solution. Describe how the benchmark model or result is measurable (can be measured by some metric and clearly observed) with thorough detail.

### Evaluation Metrics
_(approx. 1-2 paragraphs)_

In this section, propose at least one evaluation metric that can be used to quantify the performance of both the benchmark model and the solution model. The evaluation metric(s) you propose should be appropriate given the context of the data, the problem statement, and the intended solution. Describe how the evaluation metric(s) are derived and provide an example of their mathematical representations (if applicable). Complex evaluation metrics should be clearly defined and quantifiable (can be expressed in mathematical or logical terms).

### Project Design
_(approx. 1 page)_

In this final section, summarize a theoretical workflow for approaching a solution given the problem. Provide thorough discussion for what strategies you may consider employing, what analysis of the data might be required before being used, or which algorithms will be considered for your implementation. The workflow and discussion that you provide should align with the qualities of the previous sections. Additionally, you are encouraged to include small visualizations, pseudocode, or diagrams to aid in describing the project design, but it is not required. The discussion should clearly outline your intended workflow of the capstone project.

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


