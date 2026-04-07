# SOC Simulation Lab – Phishing to Data Exfiltration Attack

## Overview

This project documents a full Security Operations Center (SOC) simulation where a phishing attack led to system compromise and data exfiltration. The lab demonstrates real-world attack techniques and how they are detected, analyzed, and responded to using SIEM and Sysmon logs.

## Objectives

* Analyze phishing-based initial access
* Investigate endpoint activity using Sysmon logs
* Correlate events across an attack chain
* Differentiate between true positives and false positives
* Identify Indicators of Compromise (IOCs)
* Recommend remediation actions

## Attack Summary

The attack began with a phishing email containing a malicious ZIP attachment. Once opened, the attacker leveraged PowerShell to execute malicious scripts, access internal network shares, stage sensitive data, and exfiltrate it using DNS queries.

## Key Attack Stages

1. Initial Access – Phishing email with ZIP attachment
2. Execution – Malicious .lnk file launches PowerShell
3. Persistence & Control – PowerShell used for command execution
4. Lateral Access – Network share mapped using net.exe
5. Data Staging – Files copied using Robocopy
6. Cleanup – Network drive removed
7. Exfiltration – DNS tunneling via nslookup

## Tools & Techniques Observed

* PowerShell abuse
* Living-off-the-Land binaries (LOLBins)
* DNS-based data exfiltration
* Social engineering (phishing)
* File masquerading (.lnk disguised as .pdf)

## Files in this Repository

* report.md → Detailed incident analysis
* iocs.md → Indicators of Compromise

## Key Takeaways

* Phishing remains a critical entry point for attackers
* Legitimate system tools can be abused for malicious activity
* DNS traffic can be used for covert exfiltration
* Proper alert triage is essential to reduce false positives
