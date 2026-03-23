# SOC Phishing Investigation (TryHackMe - Phishing Unfolding)

## Overview
This project documents a phishing investigation conducted in a simulated SOC environment. The objective was to analyze alerts and determine whether they represented true or false positives based on user interaction and impact.

## Tools Used
- TryHackMe SOC Simulator

## Scenario
Multiple alerts were generated involving phishing emails containing malicious URLs. The task was to investigate each alert, identify indicators of compromise, and classify them accordingly.

## Key Findings
- Identified phishing attempts using typosquatting domains
- Detected user interaction with malicious links
- Observed execution of a malicious file leading to system compromise
- Correlated multiple alerts into a single incident involving one user

## Outcome
- Alerts without user interaction were classified as False Positives
- Alerts with confirmed interaction were classified as True Positives
- Repeated alerts were identified as part of the same incident

## Skills Demonstrated
- Phishing analysis
- Log investigation using Splunk
- Alert triage and classification
- Incident correlation

## Lessons Learned
- SOC decisions are based on impact, not just detection
- Not all alerts indicate an active incident
- Correlating alerts is critical in identifying real threats

## Note on Alert Classification

All True Positive alerts involving confirmed user interaction were correctly identified during the investigation.

A small number of alerts were initially misclassified due to the distinction between phishing attempts and successful phishing activity. This highlighted an important SOC concept: alerts are classified based on confirmed impact rather than intent.

This experience reinforced the importance of verifying user interaction (e.g., link clicks, file execution) before classifying an alert as a True Positive.

## SOC Simulation

https://tryhackme.com/soc-sim/public-summary/d5e8a2d68758883764ce294689a03fb5d0136e9d70f9671e45aed41661c15acd96456150b0a0c5bfee36d077017a8ffc