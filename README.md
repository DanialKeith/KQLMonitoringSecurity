# Enhancing Security with KQL Monitoring Successful User Logins and Logon Types

## Overview
The utilization of KQL (Kusto Query Language) in Azure Sentinel provides a strong tool for analyzing security events. This specific KQL query has been designed to extract data from the SecurityEvent table, focusing on successful user login attempts in Windows systems. This query is essential for identifying and investigating security incidents like unauthorized access or potential account compromises.

## Query Design and Function
### Structure of the Query
The query is structured as follows:

```
SecurityEvent
| where EventID == 4624
| where AccountType == "User" and LogonType == 2
| project TimeGenerated, Account, Computer, LogonType, IpAddress
```

This query targets entries in the SecurityEvent table where EventID is 4624, indicating a successful login event. It further narrows down the results to entries where AccountType is "User" and LogonType is 2, which signifies an interactive user login.

### Output Format
The query projects the results into a table format, displaying the following columns:

![1](https://github.com/DanialKeith/KQLMonitoringSecurity/assets/154257195/88fd1b13-d74a-49f1-a7b2-c670fbf89070)


-	TimeGenerated: The timestamp of the login event.
-	Account: The user account involved in the login.
-	Computer: The machine where the login occurred.
-	LogonType: The type of login (in this case, interactive).
-	IpAddress: The IP address from where the login was initiated.
## Analysis and Implications for Security
The data extracted by this query is instrumental for security analysts. It allows them to:
-	Trace which user logged into which computer.
-	Identify suspicious or abnormal activities based on login patterns.
-	Assess the context of each login event, such as the time and originating IP address.
  
## Detecting Patterns and Anomalies
Analyzing TimeGenerated and IPAddress fields can uncover patterns or trends, crucial for spotting potential attacks. For instance, multiple logins from the same IP address in a short span might suggest a brute-force attack.

## Conclusion: A Tool for Enhanced Cybersecurity
This KQL query is a valuable asset in the arsenal of cybersecurity monitoring strategies. It aids in detecting and examining successful logon events, contributing to the identification and response to security threats. Employing this query enhances an organization's capacity to safeguard against unauthorized access and reinforces its overall security posture.

