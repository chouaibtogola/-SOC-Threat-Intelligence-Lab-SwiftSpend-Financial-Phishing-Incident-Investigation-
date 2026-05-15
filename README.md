# -SOC-Threat-Intelligence-Lab-SwiftSpend-Financial-Phishing-Incident-Investigation-


#    Overview

This lab simulates a real-world phishing incident investigation within SwiftSpend Financial, where multiple employees received a malicious email designed to steal corporate credentials. What initially appeared to be a routine support request quickly escalated into a potential enterprise-wide compromise after several users reported account lockouts and suspicious activity.

As part of the IT and Security Operations team, the objective is to perform a full phishing investigation by analyzing email artifacts, identifying malicious infrastructure, tracing phishing redirects, examining the phishing kit, and leveraging Cyber Threat Intelligence (CTI) tools to uncover indicators associated with the attacker.

The lab is designed to strengthen practical skills in email analysis, phishing detection, incident response, and threat intelligence correlation.

#                                                Description

##         Scenario

Employees across different departments at SwiftSpend Financial began reporting a suspicious email circulating within the organization. Initial reports highlighted unusual wording, suspicious links, and unexpected login prompts. Unfortunately, several employees had already interacted with the email and submitted their credentials before the attack was identified.

Shortly afterward, affected users reported being locked out of their accounts, raising concerns about unauthorized access and potential lateral movement within the environment. The incident was escalated to the IT Security team for immediate investigation.

As the incident responder, your role is to analyze the evidence, determine the scope of the compromise, and uncover the attacker’s methods and infrastructure.

## Investigation Objectives

Analyze phishing email samples to identify malicious indicators and artifacts
Investigate phishing URLs and understand redirection behavior
Retrieve and examine the phishing kit used by the attacker
Use Cyber Threat Intelligence (CTI) tools to gather intelligence on domains, IPs, and indicators
Identify attacker tactics, techniques, and procedures (TTPs)
Extract additional indicators of compromise (IOCs) from the phishing kit
Document findings and assess the overall impact of the attack



#                           Let us start 



<img width="1377" height="774" alt="image" src="https://github.com/user-attachments/assets/2dadf96c-c407-45fa-8178-d7ede57363be" />
Above we have a folder with a collection of potential phishing mails that 5 employees have received


let us check the last mail " Quote for Services Rendered "  that william McClean received from the malicious mail address Accounts.Payable@groupmarketingonline.icu
<img width="1913" height="822" alt="image" src="https://github.com/user-attachments/assets/39fc02e9-ffcf-4513-95a8-2af06743b8fd" />


let's check the penultimate email from the list  sent to zoe ducan by the same malicious mail
<img width="1919" height="829" alt="image" src="https://github.com/user-attachments/assets/ecc3a3f0-5fbc-4333-b4bf-d6c8cec3051c" />

if we check the attachment in the file and open it (be sure to open it in a sandbox environment ) , it is going to redirect us to a website with a root domain of kennaroads.buzz, impersonating microsoft
<img width="1886" height="815" alt="image" src="https://github.com/user-attachments/assets/554ba2a2-86b3-4999-b58b-102ef66e8d4e" />

let us do something with the link in the navbar , by going to the attacker's data directory 
<img width="1089" height="150" alt="image" src="https://github.com/user-attachments/assets/0af15a13-8221-49d4-bee0-95055321457e" />

it takes us here : 
<img width="1800" height="831" alt="image" src="https://github.com/user-attachments/assets/f9e4ef82-efc5-4888-91e8-c5228c539899" />
we notice an archived file named: Update365.zip

let us download it and try to check its hash 
<img width="1789" height="817" alt="image" src="https://github.com/user-attachments/assets/9cc5ea8e-14c9-4139-a821-b9680a4e0c1d" />


let's open a website called virus total which is known to reference to many malicious tools , files , hashes . We will paste the hash over there
<img width="1881" height="868" alt="image" src="https://github.com/user-attachments/assets/916412c9-e2b3-4048-8985-ccfa93632cbb" />

do you notice in the threat categories , that it displayed another thing for the hash 
<img width="374" height="69" alt="image" src="https://github.com/user-attachments/assets/41bbebf5-22ae-4b91-b153-efc0cea8b260" />
yes it is a trojan !!!!

when we go to the details section , we notice 49 files are contained within the archived file
<img width="1031" height="470" alt="image" src="https://github.com/user-attachments/assets/f3ba04d4-3919-449d-837b-4f103534d2c3" />

let's go back to the url and get in the archive file 
<img width="1313" height="686" alt="image" src="https://github.com/user-attachments/assets/a4632d49-d83d-43fe-b297-1c71be310b51" />

now if we go in the log.txt file , we notice that it has credentials from people who inadvertently submitted them
<img width="1812" height="739" alt="image" src="https://github.com/user-attachments/assets/283b2fdd-510c-4061-8520-291ec0939ca4" />

if we notice something michael.ascot@swiftspend.finance has submitted his credentials more times than any other user

furthermore let's download , extract the zip archive 
        This is what we find therein

  <img width="1808" height="823" alt="image" src="https://github.com/user-attachments/assets/8bb7bd66-e1a1-4204-9ff8-7569bf0d9212" />


if we go any further and open the validation folder we notice a file : submit.php
<img width="1784" height="635" alt="image" src="https://github.com/user-attachments/assets/bacf4fad-348e-4783-8199-033ca1ea6316" />

we notice within the script that credentials are sent to a specifi mail address m3npat@yandex.com
<img width="1708" height="655" alt="image" src="https://github.com/user-attachments/assets/54699800-8198-4874-b590-e636e85c6259" />

# And voila we are at the end of this small Lab
