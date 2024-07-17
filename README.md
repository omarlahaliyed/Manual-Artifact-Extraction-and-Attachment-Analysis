# Manual Artifact Extraction and Attachment Analysis Lab

## Objective

The Manual Artifact Extraction and Attachemnet Analysis Lab is aimed manually collect artifacts from safe phishing emails and analyze its attachemnt using phishing analysis tools. This process helps in understanding the nature of phishing attacks, identifying malicious components, and developing strategies to counteract such threats effectively.

### Skills Learned
- Phishing Email Identification
- Artifact Collection
- Attachment Analysis
- Threat Analysis

### Tools Used
- Powershell for finding hashes
- Virus Total and Talos File Reputation for file reputation
- Thunderbird for email
- Sublime text for artifact collection
- Phishtool to forensically analyze phishing emails
- Cyberchef for decoding

## Steps and Questions
### Lab Overview

In this activity, you will be manually collecting artifacts from safe phishing emails. The Mozilla Thunderbird email client can be used for viewing, as well as the Sublime Text 2 text editor for looking at the .eml files directly Manually collecting artifacts using a client and text editor, is a core skill for phishing analysis, as not all organizations will have access to tools that can automatically retrieve email, web, and file-based artifacts.

**Question 1 - Email One - What is the sending address?**

Opening the email in Sublime Text we can use the Find feature (CTRL+F) to search for “From”.

![image](https://github.com/user-attachments/assets/6d9a0cdf-79c1-4614-9136-4d65ad95473f)
