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

**Question 2 - Email One - What is the recipient address?**

For this question we'll look for the “To” field and its value.

![image](https://github.com/user-attachments/assets/6b82178a-5755-4530-91a4-05158ddfbe8f)

**Question 3 - Email One - What is the subject line?**

For this question we'll look for the “Subject” field and its value.

![image](https://github.com/user-attachments/assets/e1cee0e4-f5d6-4576-a583-8f10cb17f38d)

**Question 4 - Email One - What is the date and time the email was received? (Retrieve this via text editor. Format: DD MonthName YYYY XX:XX:XX)**

For this question we'll look for the “Date” field and its value.

![image](https://github.com/user-attachments/assets/8262a200-bc22-432f-b5b9-de303e343178)

**Question 5 - Email One - What is the sending server IP address?**

For this question we'll search for the “X-Sender-IP” field and its value.

![image](https://github.com/user-attachments/assets/554f5e31-774f-4603-a9c0-223894edf4e9)

**Question 6 - Email One - What is the hostname of this IP address? (Reverse DNS Lookup)**

Taking the IP from the previous question we'll open the site https://whois.domaintools.com and perform a search. We can see the resolved hostname below.

![image](https://github.com/user-attachments/assets/1b609d06-88dc-4ce2-965e-de6fc863a28f)

**Question 7 - Email One - What is the full URL hyperlinked within this email?**

The easiest way to retrieve this artifact is to (carefully) right-click the hyperlink when viewing the file in an email client, and select ‘Copy Hyperlink’ (or a similar option).

![image](https://github.com/user-attachments/assets/a2b9a2ae-c65a-444d-b3ca-15f04911d450)

**Question 8 - Email One - What is the root domain of the URL?**

To find this we can either right-click the link in the email and select ‘copy link location’ and paste it into a program such as Notepad to see the URL text, or search for ‘http’ or ‘https’ in the email file until we find the right link. The ‘root domain’ essentially means the domain name of the URL, not including the specific resource. For this email, the URL is hxxps://www.thiswouldbeamalicioussite.com/index/2020/j411/NetflixLogin.php? (we're replaced https with hxxps to stop it from becoming hyperlinked), so the root domain is ‘thiswouldbeamalicioussite.com’.

![image](https://github.com/user-attachments/assets/873f6f68-0c74-497b-aa69-72d2f826b31a)
![image](https://github.com/user-attachments/assets/bf9b6f06-5884-44d7-ad43-d53283522d89)
![image](https://github.com/user-attachments/assets/ca720036-154a-4ee3-9fc5-9d20c84fa55f)

**Question 9 - Email Two - What is the sending address?**

Same as before, we'll use Find and search for “From”.

![image](https://github.com/user-attachments/assets/75a52786-5982-44b9-9853-7f6219c60e0f)

**Question 10 - Email Two - What is the recipient address?**

Searching for the “To” field and value.

![image](https://github.com/user-attachments/assets/f1cd808e-c64c-455b-a783-a7e3f7223621)

**Question 11 - Email Two - What is the subject line?**

Searching for the “Subject” field and value.

![image](https://github.com/user-attachments/assets/4e902c91-a2df-45c8-be16-67f7de7ef32d)

**Question 12 - Email Two - What is the date and time the email was received?**

(Retrieve this via text editor. Format: DD MonthName YYYY XX:XX:XX)
Searching for the “Date” field and value.

![image](https://github.com/user-attachments/assets/321f51e4-9167-4316-8f91-f8b3e111300c)

**Question 13 - Email Two - What is the sending server IP address?**

Searching for the “X-Sender-IP” field and value.

![image](https://github.com/user-attachments/assets/d40cb651-2c54-40bd-8ab2-68145c6c4681)

**Question 14 - Email Two - What is the hostname of the sending server IP? (Reverse DNS Lookup)**

Using the IP from the previous question, we'll submit it to https://whois.domaintools.com.

![image](https://github.com/user-attachments/assets/83f42b39-ea14-4482-bebe-e91a3e82e3ca)

**Question 15 - Email Two - What is the full file name? (name + extension)**

There are two ways we can get the file name. From within the text editor we can search for “filename”.
 
 ![image](https://github.com/user-attachments/assets/a0243b98-057e-4d63-bd40-171a06525ded)

And within an email client we can see the attachment name somewhere in the interface. The location and style will vary depending on the client, but Outlook for example will show the attachment details at the top of the email. In Thunderbird, we see this at the bottom.

![image](https://github.com/user-attachments/assets/698f0bf7-0e00-4d78-9fc1-4c723eaf341b)

**Question 16 - Email Two - What are the MD5 and SHA256 hashes of the attached file? (Format: MD5 SHA256)**

In Thunderbird we can right-click the attachment and click Save-As, then save it to the Desktop. We'll then open a PowerShell window and use the Get-FileHash cmdlet to retrieve the MD5 and SHA256 hashes. As SHA256 is the default hashing algorithm we don't need to state it, however we must do this for MD5.
 
 ![image](https://github.com/user-attachments/assets/8ac0d1d8-e530-4ebf-b13d-0681295936d5)

### Investigating Attachment

**Question 1 - What is the name of the file that was attached to a phishing email?**

Looking in folder for Lab 3 on the Desktop we can find the file. Right-clicking it we can go to Properties and copy the filename. We also need the file extension, which we can see on this panel is ‘.html’.

![image](https://github.com/user-attachments/assets/4af105c7-f344-4fb7-b6d1-9c16f189380f)

**Question 2 - What is the SHA256 hash value of this file?**

We can hold shift and right-click in the folder that contains the file to select ‘Open PowerShell Window Here’. Then we'll use the command Get-FileHash MICRO (then pressing the Tab key to auto-complete the filename).

![image](https://github.com/user-attachments/assets/47ea4011-316f-4665-b715-00ffd7c33659)

**Question 3 - What is the file size in KB?**

We can get this value by right-clicking the file, clicking Properties, then looking at the Size property.

![image](https://github.com/user-attachments/assets/b4d51627-d513-46d2-b6b6-8fd802ad5f8f)

**Question 4 - Open the file - What company is the presented web page trying to impersonate?**

Based on the Website Title property and the design, this web page is imitating Microsoft's Outlook / Office365 login portal (even though the logo image isn't loading, because the lab has no internet connection).

![image](https://github.com/user-attachments/assets/e2a9c9c3-30df-4c4a-8134-d72597cdd957)

**Question 5 - Based on the email address that has been auto filled, what recipient was this phishing email targeting?**

We can see that the email is already set in the web page as contact@securityblue.team.

![image](https://github.com/user-attachments/assets/278ecb3d-af49-4395-942f-39fcd73e934b)

**Question 6 - Right-click the web page within Chrome and select View Source. Press CTRL+A to select all of the text, then CTRL+C to copy it. Open up CyberChef from the folder on the Desktop and paste the text into the 'Input' box in the top right. Drag 'URL Decode' from the left-hand panel into the 'Recipe' tab to decode it. Search for "logo" - what is the filename of the Microsoft logo used?**

Putting the source code in CyberChef with the URL Decode operation, we can see the contents of the web page clearly.

![image](https://github.com/user-attachments/assets/7712c1b5-9e87-4ec1-be4f-91b865d17005)

Using CTRL+F we can search for ‘logo’ and find the URL and filename we need to answer this question.

![image](https://github.com/user-attachments/assets/07e46822-7089-4cb6-b412-5a03dcc8c5f4)

**Question 7 - Open Developer Tools (see instructions if you're unsure) and go to the Network tab. Enter in the password 'test' and click Sign in. Click on the off.php entry - what is the request URL being used to send the email and password to the web server?**

Opening Developer Tools then going to the Network tab, we can see any network activity on a website. Submitting the password ‘test’ will result in the following URL being visited on a malicious domain, which is how the attacker receives the credentials. Copying this value will give us the answer for the question. Notice how the email and password are in this URL!

![image](https://github.com/user-attachments/assets/55b9c25d-62ad-46ec-aba6-7da335b70968)



