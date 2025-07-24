# Microsoft Sentinel: Microsoft Teams Calls Monitoring
### 📞 Microsoft Teams Call Monitoring with Azure Logic Apps & Log Analytics

This project automates the collection and analysis of Microsoft Teams call records using Azure Logic Apps, Microsoft Graph API, and Azure Log Analytics. It helps security and operations teams monitor external calls, detect anomalies, and enrich call data for investigation or reporting.

### 🔧 Technologies Used:

Azure Logic Apps
Microsoft Graph API
Azure Log Analytics
Kusto Query Language (KQL)


### 🚀 What This Project Does:

Collects Teams call records every hour via a Logic App.
Retrieves detailed session and segment data using Microsoft Graph API.
Sends enriched data to Azure Log Analytics.
Parses and analyzes the data using KQL queries.
Detects suspicious or external calls using detection logic.

### 🧠 How to Use:

- Collect Microsoft Teams CallRecords.
- Deploy the Logic App using the JSON file.
- Configure authentication for Microsoft Graph API.
- Set up Azure Log Analytics and connect it to the Logic App.
- Use the KQL queries to parse and analyze the data.
- Optionally, create Sentinel Analytics Rules based on the detection queries.

### 📚 References:

> ℹ️ This implementation is inspired by the approach described in the [Microsoft Sentinel blog on monitoring Teams CallRecords](https://techcommunity.microsoft.com/t5/microsoft-sentinel-blog/secure-your-calls-monitoring-microsoft-teams-callBefore Logic App) but uses a custom Logic App and KQL logic tailored for external call detection.


## 🛰️ Collecting Microsoft Teams CallRecords Activity Data

This project uses the Microsoft Graph CallRecords API to collect and analyze Teams call activity in near real-time. The API provides detailed metadata about peer-to-peer and group calls, including sessions and media segments. This enables security teams to monitor external communication patterns and detect anomalies such as frequent or short-duration calls.

Unlike traditional audit logs, CallRecords data is retrieved via webhook subscriptions, allowing for more timely and granular insights into Teams usage.

Before deploying the Logic App that ingests Teams call data, make sure the following steps are completed:

1. **Register an Azure AD Application**
   - Go to **Azure Active Directory > App registrations**.
   - Create a new app to authenticate with Microsoft Graph.
   - Save the **Application (client) ID** and **Directory (tenant) ID**.

2. **Assign Microsoft Graph API Permissions**
   - Under **API permissions**, add:
     - `CallRecords.Read.All` (Application)
   - Grant **admin consent** for the tenant.

3. **Create a Client Secret**
   - Under **Certificates & secrets**, generate a new client secret.
   - Store it securely — it will be used by the Logic App to authenticate.

4. **(Optional) Restrict Access**
   - Use conditional access or security groups to limit the app’s scope.

Once these steps are complete, you can deploy the Logic App to subscribe to call records and forward them to Log Analytics for analysis.

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

   <img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/3d718bf2-129b-4667-ab37-cdfbd3b3c60c" />


