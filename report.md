# Incident Report – Phishing Attack

## Attack Summary
This incident involved a phishing attack targeting a high-privilege user (CEO). The user executed a malicious LNK file disguised as a PDF, which triggered PowerShell activity with execution policy bypass. The attacker used Base64 encoding and DNS queries to exfiltrate sensitive data to an external domain.

## Investigation
- Analyzed email content and identified suspicious URL
- URL contained typosquatting indicators (e.g., "m1crosoft")
- Verified malicious nature using security tools
- Checked Splunk logs for user interaction

## Findings
- User "Michael" clicked the malicious link
- A file was downloaded and executed
- Suspicious activity observed on the host

## Analysis
The attack successfully tricked the user into interacting with a malicious resource, resulting in potential system compromise.

## Conclusion
This incident is classified as a **True Positive** due to confirmed user interaction and execution of a malicious file.

## Recommendations
- Isolate affected host
- Reset user credentials
- Block malicious domain
- Conduct further endpoint analysis