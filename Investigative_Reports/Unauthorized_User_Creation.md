# Incident Report: Unauthorized User Creation

Date: Dec 18th, 2025

Severity: High

### Analysis:

At 18:23 PST, Splunk alerted on Event ID 4720. A user named "hacker2" was created on host "Win11-Client-01" by user: "cholbrook-da". 

A few minutes later, Event ID 4732 fired. After checking the logs it was confirmed the user "hacker" was added to "Domain Admins". 

### Conclusion:
These findings indicate a successful privilege esclation. The account was immediately disabled and investigation into the root cause is ongoing.
