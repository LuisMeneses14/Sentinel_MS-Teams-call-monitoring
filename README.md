# Microsoft Sentinel: Microsoft Teams Calls Monitoring
📞 Microsoft Teams Call Monitoring with Azure Logic Apps & Log Analytics

This project provides an automated solution to collect and analyze Microsoft Teams call records using Azure Logic Apps and Microsoft Graph API. The data is parsed and sent to Azure Log Analytics, where advanced KQL queries extract insights such as call duration, participant identities, device information, and network metrics.

🔧 Technologies Used:

Azure Logic Apps
Microsoft Graph API
Azure Log Analytics
Kusto Query Language (KQL)
✨ Key Features:

Scheduled retrieval of Teams call records via Graph API
JSON parsing of session and segment data
Enrichment with device, network, and user metadata
Custom KQL queries for monitoring and reporting
Integration with Azure Monitor for visualization and alerting
Inspired by the Microsoft Tech Community article on Teams call monitoring, this solution expands with custom parsing logic and flexible automation (https://techcommunity.microsoft.com/blog/microsoftsentinelblog/secure-your-calls--monitoring-microsoft-teams-callrecords-activity-logs-using-az/1574600).


## 🧩 Logic App Workflow Explanation

This Logic App automates the collection and processing of Microsoft Teams call records using the following steps:

1. **Recurrence Trigger**  
   The workflow is triggered every hour using a recurrence trigger.

2. **HTTP GET Call Records**  
   It sends a GET request to the Microsoft Graph API endpoint `/communications/callRecords` to retrieve recent call records.

3. **For Each Call**  
   For each call record retrieved, the Logic App iterates through the list using a `ForEach` loop.

4. **HTTP GET Session Details**  
   Within the loop, it sends another GET request to fetch detailed session and segment information for each call.

5. **Send to Azure Log Analytics**  
   The session data is then sent to Azure Log Analytics using the Data Collector API, where it can be queried using KQL.

   The diagram below illustrates the flow of the Logic App:

   <img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/42d50f02-e46d-4b4b-98f9-e31fb00ac6df" />

