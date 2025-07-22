# Sentinel_teams-call-monitoring
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
