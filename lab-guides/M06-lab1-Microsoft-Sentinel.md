# Microsoft Sentinel

Microsoft Sentinel is a cloud-native solution that provides security information and event management (SIEM) and security orchestration, automation, and response (SOAR) capabilities. It helps you raise your organization's security posture by enabling you to:

-   Collect data at cloud scale across all users, devices, applications, and infrastructure, both on-premises and in multiple clouds.
-   Detect previously undetected threats and minimize false positives using Microsoft's analytics and unparalleled threat intelligence.
-   Investigate threats with artificial intelligence, and hunt for suspicious activities at scale, tapping into years of cyber security work at Microsoft.
-   Respond to incidents rapidly with built-in orchestration and automation of common tasks.

Microsoft Sentinel is based on open standards and interoperable with other Decentralized Identity solutions. It is also integrated with other Microsoft security solutions, such as Microsoft 365 Defender, Entra ID, and Defender for Cloud. By using Microsoft Sentinel, you can gain a bird's-eye view across the enterprise and protect your data against modern risks.

To use Microsoft Sentinel, you need the following requirements:

-   An active Azure subscription. If you don't have one, you can create a free account before you begin.
-   A Log Analytics workspace. This is where Microsoft Sentinel will store and analyze the data that it collects from various sources. You can create a new workspace or use an existing one.
-   The correct permissions to deploy and use Microsoft Sentinel. You need contributor permissions to the subscription in which the Microsoft Sentinel workspace resides. You also need either Microsoft Sentinel Contributor or Microsoft Sentinel Reader permissions on the resource group that the workspace belongs to. To install or manage solutions in the content hub, you need the Template Spec Contributor role on the resource group that the workspace belongs to.
-   Microsoft Sentinel is a paid service. You should review the pricing options and the Microsoft Sentinel pricing page before you start using it.

In this lab, you are a Security Operations Analyst working at a company that is implementing Microsoft Sentinel. You are responsible for setting up the Microsoft Sentinel environment to meet the company requirements to minimize costs, meet compliance regulations, and provide the most manageable environment for your security team to perform their daily job responsibilities.

## Task 1: Initialize the Microsoft Sentinel Workspace

In this task, you will create a Microsoft Sentinel workspace. A Log Analytics workspace is required for Microsoft Sentinel. This is where data is stored, retained, and analyzed for security value.

1.  Open the Edge browser.
2.  In the Edge browser, navigate to the Azure portal at +++https://portal.azure.com+++.
3.  Sign-in using the lab-provided credentials on the Resource tab.
4.  In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.
5.  Select **+ Create**.
6.  The next page, **Add Microsoft Sentinel** to a workspace will display a list of available Log Analytics workspaces to add Microsoft Sentinel. Select the button to start the "Create Log Analytics workspace" process.

The Basics tab includes the following options:

-   Subscription
-   Resource Group
-   Name
-   Region

The Name will be the name of the Microsoft Sentinel workspace. The Microsoft Sentinel name will default to the Log Analytics Workspace Name. The Region is the location where ingested data is stored. The data location impacts data governance requirements. Workspaces can't move from region to region; you will need to recreate the workspace if the region option needs to be changed.

1.  Select the **Review + Create** button and then select the Create button.
2.  The "Add Microsoft Sentinel to Workspace" screen will now appear after you've completed the previous steps.
3.  Wait for the newly created "Log Analytics Workspace" to appear in the list. This operation could take a few minutes.
4.  Select the newly created Log Analytics workspace. And select the **Add** button.
5.  The new Microsoft Sentinel workspace is now the active screen. The Microsoft Sentinel left navigation has four areas:
-   General
-   Threat management
-   Content management
-   Configuration

The Overview tab displays a standard dashboard of information about the ingested data, alerts, and incidents.

1.  Navigate around the newly created Microsoft Sentinel workspace to become familiar with the user interface options.

## Task 2: Configure log retention

It is important to configure log retention for Microsoft Sentinel because it allows you to:

-   Keep your security data for as long as you need, according to your organizational and regulatory requirements. Different data types may have different retention periods, depending on their relevance and value. For example, you may want to keep security alerts for longer than performance metrics.
-   Reduce the cost of storing and analyzing large volumes of data in your Log Analytics workspace. By archiving older, less used data, you can save on storage and query costs, while still being able to access the data when needed.
-   Optimize your security operations and investigations by having the right data available at the right time. By setting appropriate retention and archive policies for your data, you can ensure that you have the most relevant and recent data in your interactive workspace, while still being able to retrieve historical data from your archive storage.

In this task, you will change the retention period for the SecurityEvent table.

1.  In Microsoft Sentinel, select the **Settings** option under the *Configuration* area.
2.  Select **Workspace settings**.
3.  In Log Analytics workspace, select the **Tables** option under the *Settings* area.
4.  Search and select the table **SecurityEvent**, and then select the ellipsis button (...).
5.  Select **Manage Table**.
6.  Select **180 days** for *Total retention period*. Notice that *Archive period* is only 150 days, since it uses 30 days from the (default) *Interactive retention*.
7.  Select **Save** to apply the changes.

## Task 3: Connect the Microsoft Defender for Cloud data connector

You are a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You must learn how to connect log data from the many data sources in your organization. The organization has data from Microsoft 365, Microsoft 365 Defender, Azure resources, non-azure virtual machines, etc. You start connecting the Microsoft sources first.

Connecting the Microsoft Defender for Cloud data connector to Microsoft Sentinel provides you with the following benefits:

-   You can stream security alerts from Microsoft Defender for Cloud into Microsoft Sentinel, so you can view, analyze, and respond to Defender alerts, and the incidents they generate, in a broader organizational threat context.
-   You can synchronize the status of security alerts between Microsoft Defender for Cloud and Microsoft Sentinel, so that any changes made in one service are reflected in the other.
-   You can enable bi-directional sync to automatically close the original security alerts in Microsoft Defender for Cloud when you close the corresponding Microsoft Sentinel incidents that contain those alerts.
-   You can use Microsoft Sentinel's advanced capabilities, such as workbooks, analytics, hunting, and automation, to enhance your security operations and investigations based on Microsoft Defender for Cloud data.

In this task, you will connect the Microsoft Defender for Cloud data connector.

1.  In the Microsoft Sentinel left menus, scroll down to the *Content management* section and select **Content Hub**.
2.  In the *Content hub*, search for the **Microsoft Defender for Cloud** solution and select it from the list.
3.  On the *Microsoft Defender for Cloud* solution page select **Install**.
4.  When the installation completes select **Manage**
5.  **Note:** The *Microsoft Defender for Cloud* solution installs the *Microsoft Defender for Cloud* Data connector and an Analytic rule.
6.  Select the *Microsoft Defender for Cloud* Data connector and select **Open connector page**.
7.  In the *Configuration* section, under the *Instructions* tab, **select** the checkbox for the "Azure Pass - Sponsorship" subscription and slide the **Status** option to the right.
8.  **Note:** If it switches back to disconnected, please review the Learning Path 3, Exercise 1, Task 1 to assign the proper permissions to your account.
9.  The *Status* should be now **Connected** and "Bi-directional sync" should be *Enabled*.
10. Scroll down and under the *Create incidents - Recommended!* area, verify that *Create incidents automatically from all alerts generated in this connected service* is **Enabled**.

## Task 4: Connect the Azure Activity data connector

Connecting the Azure Activity data connector to Microsoft Sentinel provides you with the following benefits:

-   You can stream Azure Activity Log data into Microsoft Sentinel, so you can view, analyze, and respond to Azure subscription-level events that occur in your organization, such as Azure Resource Manager operational data, service health events, write operations taken on the resources in your subscription, and the status of activities performed in Azure.
-   You can use Microsoft Sentinel's advanced capabilities, such as workbooks, analytics, hunting, and automation, to enhance your security operations and investigations based on Azure Activity data.
-   You can correlate Azure Activity data with other data sources in Microsoft Sentinel, such as Microsoft Defender for Cloud, Azure Security Center, Azure AD Identity Protection, etc., to gain a broader organizational threat context and improve your detection and response capabilities.

In this task, you will connect the *Azure Activity* data connector.

1.  In the Microsoft Sentinel left menus, scroll down to the *Content management* section and select **Content Hub**.
2.  In the *Content hub*, search for the **Azure Activity** solution and select it from the list.
3.  On the *Microsoft Defender for Cloud* solution page select **Install**.
4.  When the installation completes select **Manage**
5.  **Note:** The *Azure Activity* solution installs the *Azure Activity* Data connector, 12 Analytic rules, 14 Hunting queries and 1 Workbook.
6.  Select the *Azure Activity* Data connector and select **Open connector page**.
7.  In the *Configuration* area under the *Instructions* tab, scroll down to "2. Connect your subscriptions...", and select **Launch Azure Policy Assignment Wizard\>**.
8.  In the **Basics** tab, select the ellipsis button (...) under **Scope** and select your "Azure Pass - Sponsorship" subscription from the drop-down list and click **Select**.
9.  Select the **Parameters** tab, choose your *uniquenameDefender* workspace from the **Primary Log Analytics workspace** drop-down list. This action will apply the subscription configuration to send the information to the Log Analytics workspace.
10. Select the **Remediation** tab and select the **Create a remediation task** checkbox. This action will apply the policy to existing Azure resources.
11. Select the **Review + Create** button to review the configuration.
12. Select **Create** to finish.

You are a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You must learn how to connect log data from the many data sources in your organization. Finally, you connect a threat intelligence feed to enhance your ability to detect and prioritize known threats.

## Task 5: Creating an Analytics Rule

Analytics rules are features in Microsoft Sentinel that help security teams discover and respond to threats and anomalous behaviors across their environment. There are different types of analytics rules, such as:

-   Microsoft security rules: These rules automatically create Microsoft Sentinel incidents from the alerts generated in other Microsoft security solutions, in real time. You can use Microsoft security rules as a template to create new rules with similar logic.
-   Fusion rules: These rules use the Fusion correlation engine, with its scalable machine learning algorithms, to detect advanced multistage attacks by correlating many low-fidelity alerts and events across multiple products into high-fidelity and actionable incidents. Fusion is enabled by default.
-   Machine learning behavioral analytics rules: These rules are based on proprietary Microsoft machine learning algorithms, so you can't see the internal logic of how they work and when they run. They detect anomalous user and entity behaviors, such as abnormal logon patterns, suspicious resource access, or unusual network activities.
-   Threat intelligence rules: These rules take advantage of threat intelligence produced by Microsoft to generate high fidelity alerts and incidents with the Microsoft Threat Intelligence Analytics rule.
-   Scheduled query rules: These rules allow you to write custom queries in Kusto Query Language (KQL) to search for specific events or sets of events across your environment, alert you when certain event thresholds or conditions are reached, generate incidents for your SOC to triage and investigate, and respond to threats with automated tracking and remediation processes.

In this task, you will create an Analytics Rule.

1.  Select Analytics from the navigation menu.
2.  Select *Create incidents based on Microsoft Defender for Cloud* from the rule templates.
3.  Select **Create rule** in the connector information blade.
4.  In the Analytics rule wizard, select **Next: Automated response**, then select **Next: Review and create**.
5.  Select **save**.

## Task 6: Explore workbook templates

A Microsoft Sentinel workbook is a feature that helps you to visualize and monitor your data collected by Microsoft Sentinel, using interactive reports and dashboards. You can use workbooks to create custom queries, charts, tables, and maps based on your data sources, or use existing workbook templates that are available with packaged solutions or as standalone content from the content hub. Workbooks can help you to:

-   Gain insights into your security posture and operations across different data types and scenarios, such as Azure activity, Microsoft 365 audit logs, threat intelligence, analytics efficiency, etc.
-   Correlate and analyze data from multiple sources and locations, such as Microsoft security solutions, Azure services, Windows devices, third-party products, etc.
-   Detect and respond to threats and anomalous behaviors across your environment, using Microsoft Sentinel's advanced capabilities, such as analytics rules, hunting queries, automation playbooks, etc.

In this task, you will explore the Microsoft Sentinel workbook templates.

1.  Select **Workbooks** under the *Threat Management* left blade. The *Templates* tab is selected by default.
2.  Search for and select the **Azure Activity** template workbook. In the right pane, scroll down and select the **View template** button.
3.  Review the contents of the workbook. It shows insights of your Azure subscription operations by collecting and analyzing the data from the Activity Log.
4.  Close the workbook by selecting the **X** in the top-right corner.

## Task 7: Save and Modify a workbook template

In this task, you will save a workbook template and modify it.

1.  You should be back in the **Microsoft Sentinel - Workbooks - Templates** tab. Scroll down again and select the **Save** button for the *Azure Activity* workbook.
2.  Leave **East US** as the default value for *Region* and select **OK**.
3.  Select the **View saved workbook** button.
4.  Select **Edit** in the command bar to enable changes in the workbook.
5.  Scroll down to the *Caller activities over time* area, look at the color of the *Activities* column since we are going to format those columns. Select the **Edit** button below the grid.
6.  Select the **Column Settings** button, it is located to the right of the *Run Query* command bar. **Hint:** This button only appears if there is data from the KQL query.
7.  In the *Edit column settings* blade that appears, within *Columns* select **Activities**.
8.  Change the value for *Column renderer* to **Heatmap**. For *Color palette*, scroll down to select **32-color categorical**.
9.  Select **Save and Close**. Notice the change in the *Activities* column.
10. Select **Done Editing** at the bottom of the query (not the top menu).
11. Now select **Done Editing** at the top menu and select the **Save** icon.
12. Close the workbook by selecting the **X** in the top-right corner.

## Task 8: Create a hunting query

**Hunting** in Microsoft Sentinel is a process where security analysts proactively seek out undetected threats and malicious behaviors across their organization's data sources, using interactive queries, dashboards, and notebooks. Hunting in Microsoft Sentinel can help you to:

-   Gain insights into your security posture and operations across different data types and scenarios, such as Azure activity, Microsoft 365 audit logs, threat intelligence, analytics efficiency, etc.
-   Correlate and analyze data from multiple sources and locations, such as Microsoft security solutions, Azure services, Windows devices, third-party products, etc.
-   Detect and respond to threats and anomalous behaviors across your environment, using Microsoft Sentinel's advanced capabilities, such as analytics rules, automation playbooks, etc.

A **Hunt** in Microsoft Sentinel is a feature that allows you to conduct end-to-end proactive threat hunting in Microsoft Sentinel, using the Hunts tab. A Hunt can help you to:

-   Define a hypothesis based on specific MITRE techniques, potentially malicious activity, recent threats, or your own custom idea.
-   Use security-researcher-generated hunting queries or custom hunting queries to investigate your hypothesis across your data sources and locations.
-   Collect evidence, investigate user and entity behaviors, and annotate your findings using hunt-specific bookmarks.
-   Collaborate and document your findings with comments.
-   Act on your results by creating new analytic rules, new incidents, new threat indicators, and running playbooks.
-   Keep track of your new, active, and closed hunts in one place.
-   View metrics based on validated hypotheses and tangible results.

In this task, you will create a hunting query, bookmark a result, and create a Livestream.

1.  Select **Logs**
2.  Enter the following KQL Statement in the *New Query 1* space:
3.  **Important:** Please paste any KQL queries first in Notepad and then copy from there to the *New Query 1* Log window to avoid any errors.
4.  `let lookback = 2d; `
5.  `SecurityEvent `
6.  `| where TimeGenerated >= ago(lookback) `
7.  `| where EventID == 4688 and Process =~ "powershell.exe"`
8.  `| extend PwshParam = trim(@"[^/\\]*powershell(.exe)+" , CommandLine) `
9.  `| project TimeGenerated, Computer, SubjectUserName, PwshParam `
10. `| summarize min(TimeGenerated), count() by Computer, SubjectUserName, PwshParam `
11. `| order by count_ desc nulls last `
12. Review the different results. You have now identified PowerShell requests that are running in your environment.
13. Select the checkbox of the results that shows the *"-file c2.ps1"*.
14. In the middle command bar, select the **Add bookmark** button.
15. Select **+ Add new entity** under *Entity mapping*.
16. For *Entity* select **Host**, then **Hostname** and **Computer** for the values.
17. For *Tactics and Techniques*, select **Command and Control**.
18. Go back to the *Add bookmark* blade, and the select **Create**. We will map this bookmark to an incident later.
19. Close the *Logs* window by selecting the **X** in the top-right of the window and select **OK** to discard the changes.
20. Select your Microsoft Sentinel workspace again and select the **Hunting** page under the *Threat Management* area.
21. Select the **Queries** tab and then **+ New Query** from the command bar.
22. In the *Create custom query* window, for the *Name* enter **PowerShell Hunt**.
23. For the *Custom query* enter the following KQL statement:
24. `let lookback = 2d; `
25. `SecurityEvent `
26. `| where TimeGenerated >= ago(lookback) `
27. `| where EventID == 4688 and Process =~ "powershell.exe"`
28. `| extend PwshParam = trim(@"[^/\\]*powershell(.exe)+" , CommandLine) `
29. `| project TimeGenerated, Computer, SubjectUserName, PwshParam `
30. `| summarize min(TimeGenerated), count() by Computer, SubjectUserName, PwshParam `
31. `| order by count_ desc nulls last `
32. Scroll down and under *Entity mapping* select:
    1.  For the *Entity type* drop-down list select **Host**.
    2.  For the *Identifier* drop-down list select **HostName**.
    3.  For the *Value* drop-down list select **Computer**.
33. Scroll down and under *Tactics & Techniques* select **Command and Control** and then select **Create** to create the hunting query.
34. In the *"Microsoft Sentinel - Hunting"* blade, search for the query you just created in the list, *PowerShell Hunt*.
35. Select **PowerShell Hunt** from the list.
36. Review the number of results in the middle pane under the *Results* column.
37. Select the **View Results** button from the right pane. The KQL query will automatically run.
38. Close the *Logs* window by selecting the **X** in the top-right of the window and select **OK** to discard the changes.
39. Right-click the **PowerShell Hunt** query and select **Add to livestream**. **Hint:** This also can be done by sliding right and selecting the ellipsis **(...)** at the end of the row to open a context menu.
40. Review that the *Status* is now *Running*. This will be running every 30 seconds in the background and you will receive a notification in the Azure Portal (bell icon) when a new result is found.
41. Select the **Bookmarks** tab in the middle pane.
42. Select the bookmark you just created from the results list.
43. On the right pane, scroll down and select the **Investigate** button. **Hint:** It might take a couple of minutes to show the investigation graph.
44. Explore the Investigation graph just like you did a the previous module. Notice the high number of *Related alerts* for *WINServer*.
45. Close the *Investigation* graph window by selecting the **X** in the top-right of the window.
46. Hide the right blade by selecting the **\>\>** icon and then scroll right until you see the ellipsis **(...)** icon.
47. Select **Add to existing incident**. All the incidents appear in the right pane.
48. Select one of the incidents and then select **Add**.
49. Scroll left to notice that the *Severity* column is now populated with the incident's data.

## Task 9: Access the KQL testing area

KQL stands for Kusto Query Language, which is the language used in Microsoft Sentinel to perform search, analysis, write detection rules and visualize data in Workbooks. KQL is a powerful tool to explore your data and discover patterns, identify anomalies and outliers, create statistical modeling, and more. The query uses schema entities that are organized in a hierarchy similar to SQLs: databases, tables, and columns.

KQL is also used in other Azure services, such as Azure Data Explorer, Azure Monitor Logs, Azure Resource Graph and Azure Data Explorer. KQL is inspired by famed undersea explorer Jacques Cousteau (and pronounced accordingly \\"koo-STOH\\"), and it’s designed to help you dive deep into your oceans of data and explore their hidden treasures.

The best way to get started learning KQL is to use the Must Learn KQL learning modules at ++++https://aka.ms/MustLearnKQL++++

In this task, you will access a Log Analytics environment where you can practice writing KQL statements.

1.  Go to +++https://aka.ms/lademo+++ in your browser. Login with the M365 Administrator credentials.
2.  Close the Log Analytics video pop-up window that appears.
3.  Explore the available tables listed in the tab on the left side of the screen.
4.  In the query editor, enter the following query and select the **Run** button. You should see the query results in the bottom window.
5.  `SecurityEvent`
6.  Notice that you have reached the maximum number of results (30,000).
7.  Change the *Time range* to **Last 30 minutes** in the Query Window.
8.  Next to the first record, select the **\>** to expand the information for the row.

## Task 10: Run Basic KQL Statements

In this task, you will build basic KQL statements.

**Important:** For each query, clear the previous statement from the Query Window or open a new Query Window by selecting **+** after the last opened tab (up to 25).

1.  The following statement demonstrates the **search** operator, which searches all columns in the table for the value. In the Query Window enter the following statement and select **Run**:
2.  `search "new"`
3.  The following statement demonstrates **search** across tables listed within the **in** clause. In the Query Window enter the following statement and select **Run**:
4.  `search in (SecurityEvent,App*) "new"`
5.  Change back the *Time range* to **Last 24 hours** in the Query Window.
6.  The following statements demonstrate the **where** operator, which filters on a specific predicate. In the Query Window enter the following statement and select **Run**:
7.  **Important:** You should select **Run** after entering each query from the code blocks below.
8.  `SecurityEvent  `
9.  `| where TimeGenerated > ago(1h)`
10. **Note:** The *Time range* now shows *Set in query* since we are filtering with the TimeGenerated column.
11. `SecurityEvent  `
12. `| where TimeGenerated > ago(1h) and EventID == 4624`
13. `SecurityEvent  `
14. `| where TimeGenerated > ago(1h)`
15. `| where EventID == 4624  `
16. `| where AccountType =~ "user"`
17. `SecurityEvent  `
18. `| where TimeGenerated > ago(1h) and EventID in (4624, 4625)`
19. The following statement demonstrates the use of the **let** statement to declare *variables*. In the Query Window enter the following statement and select **Run**:
20. `let timeOffset = 1h;`
21. `let discardEventId = 4688;`
22. `SecurityEvent`
23. `| where TimeGenerated > ago(timeOffset*2) and TimeGenerated < ago(timeOffset)`
24. `| where EventID != discardEventId`
25. The following statement demonstrates the use of the **let** statement to declare a *dynamic list*. In the Query Window enter the following statement and select **Run**:
26. `let suspiciousAccounts = datatable(account: string) [`
27. `  @"NA\timadmin", `
28. `  @"NT AUTHORITY\SYSTEM"`
29. `];`
30. `SecurityEvent  `
31. `| where TimeGenerated > ago(1h)`
32. `| where Account in (suspiciousAccounts)`
33. **Tip:** You can re-format the query easily by selecting the ellipsis (...) in the Query window and select **Format query**.
34. The following statement demonstrates the use of the **let** statement to declare a *dynamic table*. In the Query Window enter the following statement and select **Run**:
35. `let LowActivityAccounts =`
36. `    SecurityEvent `
37. `    | summarize cnt = count() by Account `
38. `    | where cnt < 1000;`
39. `LowActivityAccounts | where Account contains "sql"`
40. Change the **Time range** to **Last hour** in the Query Window. This will limit our results for the following statements.
41. The following statement demonstrates the **extend** operator, which creates a calculated column and adds it to the result set. In the Query Window enter the following statement and select **Run**:
42. `SecurityEvent  `
43. `| where TimeGenerated > ago(1h) `
44. `| where ProcessName != "" and Process != "" `
45. `| extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process))`
46. The following statement demonstrates the **order by** operator, which sorts the rows of the input table by one or more columns in ascending or descending order. The **order by** operator is an alias to the **sort by** operator. In the Query Window enter the following statement and select **Run**:
47. `SecurityEvent  `
48. `| where TimeGenerated > ago(1h) `
49. `| where ProcessName != "" and Process != "" `
50. `| extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process)) `
51. `| order by StartDir desc, Process asc`
52. The following statements demonstrate the **project** operator, which selects the columns to include in the specified order. In the Query Window enter the following statement and select **Run**:
53. `SecurityEvent  `
54. `| where TimeGenerated > ago(1h) `
55. `| where ProcessName != "" and Process != "" `
56. `| extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process)) `
57. `| order by StartDir desc, Process asc `
58. `| project Process, StartDir`
59. The following statements demonstrate the **project-away** operator, which selects the columns to exclude from the output. In the Query Window enter the following statement and select **Run**:
60. `SecurityEvent  `
61. `| where TimeGenerated > ago(1h) `
62. `| where ProcessName != "" and Process != "" `
63. `| extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process)) `
64. `| order by StartDir desc, Process asc `
65. `| project-away ProcessName`

## Task 11: Analyze Results in KQL with the Summarize Operator

In this task, you will build KQL statements to aggregate data. **Summarize** groups the rows according to the **by** group columns, and calculates aggregations over each group.

1.  The following statement demonstrates the **count()** function, which returns a count of the group. In the Query Window enter the following statement and select **Run**:
2.  `SecurityEvent  `
3.  `| where TimeGenerated > ago(1h) and EventID == 4688  `
4.  `| summarize count() by Process, Computer`
5.  The following statement demonstrates the **count()** function, but in this example, we name the column as *cnt*. In the Query Window enter the following statement and select **Run**:
6.  `SecurityEvent  `
7.  `| where TimeGenerated > ago(1h) and EventID == 4624  `
8.  `| summarize cnt=count() by AccountType, Computer`
9.  The following statement demonstrates the **dcount()** function, which returns an approximate distinct count of the group elements. In the Query Window enter the following statement and select **Run**:
10. `SecurityEvent  `
11. `| where TimeGenerated > ago(1h)`
12. `| summarize dcount(IpAddress)`
13. The following statement is a rule to detect Invalid password failures across multiple applications for the same account. In the Query Window enter the following statement and select **Run**:
14. `let timeframe = 30d;`
15. `let threshold = 1;`
16. `SigninLogs`
17. `| where TimeGenerated >= ago(timeframe)`
18. `| where ResultDescription has "Invalid password"`
19. `| summarize applicationCount = dcount(AppDisplayName) by UserPrincipalName, IPAddress`
20. `| where applicationCount >= threshold`
21. The following statement demonstrates the **arg_max()** function, which returns one or more expressions when the argument is maximized. The following statement will return the most current row from the SecurityEvent table for the computer SQL10.NA.contosohotels.com. The \* in the arg_max function requests all columns for the row. In the Query Window enter the following statement and select **Run**:
22. `SecurityEvent  `
23. `| where Computer == "SQL10.na.contosohotels.com"`
24. `| summarize arg_max(TimeGenerated,*) by Computer`
25. The following statement demonstrates the **arg_min()** function, which returns one or more expressions when the argument is minimized. In this statement, the oldest SecurityEvent for the computer SQL10.NA.contosohotels.com will be returned as the result set. In the Query Window enter the following statement and select **Run**:
26. `SecurityEvent  `
27. `| where Computer == "SQL10.na.contosohotels.com"`
28. `| summarize arg_min(TimeGenerated,*) by Computer`
29. The following statements demonstrate the importance of understanding results based on the order of the *pipe*. In the Query Window enter the following queries and run each query separately:
    1.  **Query 1** will have Accounts for which the last activity was a login. The SecurityEvent table will first be summarized and return the most current row for each Account. Then only rows with EventID equals 4624 (login) will be returned.
    2.  `SecurityEvent  `
    3.  `| summarize arg_max(TimeGenerated, *) by Account `

        `| where EventID == 4624  `

    4.  **Query 2** will have the most recent login for Accounts that have logged in. The SecurityEvent table will be filtered to only include EventID = 4624. Then these results will be summarized for the most current login row by Account.
    5.  `SecurityEvent  `
    6.  `| where EventID == 4624  `

        `| summarize arg_max(TimeGenerated, *) by Account`

30. **Note:** You can also review the "Total CPU" and "Data used for processed query" by selecting the "Query details" link on the lower right and compare the data between both statements.
31. The following statement demonstrates the **make_list()** function, which returns a *list* of all the values within the group. This KQL query will first filter the EventID with the where operator. Next, for each Computer, the results are a JSON array of Accounts. The resulting JSON array will include duplicate accounts. In the Query Window enter the following statement and select **Run**:
32. `SecurityEvent  `
33. `| where TimeGenerated > ago(1h)`
34. `| where EventID == 4624  `
35. `| summarize make_list(Account) by Computer`
36. The following statement demonstrates the **make_set()** function, which returns a set of *distinct* values within the group. This KQL query will first filter the EventID with the where operator. Next, for each Computer, the results are a JSON array of unique Accounts. In the Query Window enter the following statement and select **Run**:
37. `SecurityEvent  `
38. `| where TimeGenerated > ago(1h)`
39. `| where EventID == 4624  `
40. `| summarize make_set(Account) by Computer`

## Task 12: Create visualizations in KQL with the Render Operator

In this task, you will use generate visualizations with KQL statements.

1.  The following statement demonstrates the **render** operator (which renders results as a graphical output), using a **barchart** visualization. In the Query Window enter the following statement and select **Run**:
2.  `SecurityEvent  `
3.  `| where TimeGenerated > ago(1h)`
4.  `| summarize count() by Account`
5.  `| render barchart`
6.  The following statement demonstrates the **render** operator visualizing results with a time series. The **bin()** function rounds all values in a timeframe and groups them, used frequently in combination with **summarize**. If you have a scattered set of values, the values are grouped into a smaller set of specific values. Combining the generated results and pipe them to a **render** operator with a **timechart** provides a time series visualization. In the Query Window enter the following statement and select **Run**:
7.  `SecurityEvent  `
8.  `| where TimeGenerated > ago(1h)`
9.  `| summarize count() by bin(TimeGenerated, 1m)`
10. `| render timechart`
