---
description: "Role definitions - predefined roles"
title: "Role definitions - predefined roles | Microsoft Docs"
ms.date: 02/04/2021
ms.service: reporting-services
ms.subservice: security


ms.topic: conceptual
helpviewer_keywords: 
  - "security [Reporting Services], defaults"
  - "default security"
  - "role-based security [Reporting Services], defaults"
ms.assetid: 6b46db51-7c30-467d-a251-50f50647fe21
author: maggiesMSFT
ms.author: maggies
---
# Role definitions - predefined roles

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installs with predefined roles that you can use to grant access to report server operations. Each predefined role describes a collection of related tasks. You can assign groups and user accounts to predefined roles to provide immediate access to report server operations.  
  
## How to use predefined roles  
  
1. Review the predefined roles to determine whether you can use them as is. If you need to adjust the tasks or define additional roles, you should do this before you begin assigning users to specific roles. To create or edit custom roles use SQL Server Management Studio. For more information, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](../../reporting-services/security/role-definitions-create-delete-or-modify.md).
  
2. Identify which users and groups require access to the report server, and at what level. Most users should be assigned to the **Browser** role or the **Report Builder** role. A smaller number of users should be assigned to the **Publisher** role. Very few users should be assigned to **Content Manager**.  

3. When you are ready to assign user and group accounts to specific roles, use the web portal. For more information, see [Grant User Access to a Report Server](../../reporting-services/security/grant-user-access-to-a-report-server.md).  
  
##  <a name="bkmk_rolelist"></a> Predefined role definitions  
 Predefined roles are defined by the tasks that it supports. You can modify these roles or replace them with custom roles.  
  
 *Scope* defines the boundaries within which roles are used. Item-level roles provide varying levels of access to report server items and operations that affect those items. Item-level roles are defined on the root node (Home) and all items throughout the report server folder hierarchy. System-level roles authorize access at the site level. Item and system-level roles are mutually exclusive but are used together to provide comprehensive permissions to report server content and operations.  
  
 The following table describes the predefined scope of the roles:  
  
|Predefined role|Scope|Description|  
|---------------------|-----------|-----------------|  
|[Content Manager Role](#bkmk_content)|Item|May manage content in the Report Server. This includes folders, reports, and resources.|  
|[Publisher Role](#bkmk_publisher)|Item|May publish reports and linked reports to the Report Server.|  
|[Browser Role](#bkmk_browser)|Item|May view folders, reports, and subscribe to reports.|  
|[Report Builder Role](#bkmk_reportbuilder)|Item|May view report definitions.|  
|[My Reports Role](#bkmk_myreports)|Item|May publish reports and linked reports; manage folders, reports, and resources in a users My Reports folder.|  
|[System Administrator Role](#bkmk_systemadministrator)|System|View and modify system role assignments, system role definitions, system properties, and shared schedules, in addition to create role definitions, and manage jobs in Management Studio.|  
|[System User Role](#bkmk_systemuser)|System|View system properties, shared schedules, and allow use of Report Builder or other clients that execute report definitions.|  
  
##  <a name="bkmk_content"></a> Content manager role  
 The **Content Manager** role is a predefined role that includes tasks that are useful for a user who manages reports and Web content, but doesn't necessarily author reports or manage a Web server or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance. A content manager deploys reports, manages report models and data source connections, and makes decisions about how reports are used. All item-level tasks are selected by default for the **Content Manager** role definition.  
  
 The **Content Manager** role is often used with the **System Administrator** role. Together, the two role definitions provide a complete set of tasks for users who require full access to all items on a report server. Although the **Content Manager** role provides full access to reports, report models, folders, and other items within the folder hierarchy, it doesn't provide access to site-level items or operations. Tasks such as creating and managing shared schedules, setting server properties, and managing role definitions are system-level tasks that are included in the **System Administrator** role. For this reason, we recommend that you create a second role assignment at the site level that provides access to shared schedules.  
  
### Content manager tasks  
 The following table lists the tasks that are included in the **Content Manager** role:  
  
|Task|Description|  
|----------|-----------------|  
|Comment on reports|Create, view, edit, and delete comments on reports.| 
|Consume reports|Reads report definitions.|  
|Create linked reports|Create linked reports that are based on a non-linked report.|  
|Manage all subscriptions|View, modify, and delete any subscription for reports and linked reports, regardless of who owns the subscription. This task supports the creation of data-driven subscriptions. It also supports the editing and execution of [scheduled refresh for Power BI (.pbix) files in Power BI Report Server](/power-bi/report-server/configure-scheduled-refresh).|  
|Manage comments|Delete other users' comments on reports.| 
|Manage data sources|Create and delete shared data source items, view, and modify data source properties and content.|  
|Manage folders|Create, view, and delete folders, and view and modify folder properties.| 
|Manage individual subscriptions|Create, view, modify, and delete user-owned subscriptions to reports and linked reports. This task also supports the editing and execution of [scheduled refresh for Power BI (.pbix) files in Power BI Report Server](/power-bi/report-server/configure-scheduled-refresh).|  
|Manage models|Create, view, and delete models, and view and modify model properties.|  
|Manage report history|Create, view, and delete report history, view report history properties, and view, and modify settings that determine snapshot history limits and how caching works.|  
|Manage reports|Add and delete reports, modify report parameters, view and modify report properties, view and modify data sources that provide content to the report, view and modify report definitions, and set security policies at the report level.|  
|Manage resources|Create, modify, and delete resources, and view and modify resource properties.|  
|Set security for individual items|Define security policies for reports, linked reports, folders, resources, and data sources. For more information, see [Securable Items](../../reporting-services/security/securable-items.md).|  
|View data sources|View shared data source items in the folder hierarchy.|  
|View folders|View folder contents and navigate through the folder hierarchy.|  
|View models|View models in the folder hierarchy, use models as data sources for a report, and run queries against the model to retrieve data.|  
|View reports|Run reports and view report properties.|  
|View resources|View resources and resource properties.|  
  
### Customizing the content manager role  
 This role is intended for trusted users who have overall responsibility for managing and maintaining report server content. You can remove tasks from this definition, but doing so may introduce ambiguity into what can be managed. For example, removing the "View reports" task from this role definition would prevent a **Content Manager** from viewing report contents and therefore be unable to verify changes to parameter and credential settings.  
  
 The **Content Manager** role is used in default security.  
  
##  <a name="bkmk_publisher"></a> Publisher role  
 The **Publisher** role is a built-in role definition that includes tasks that enable users to add content to a report server. This role is predefined for your convenience. It is not used until you create role assignments that include it. This role is intended for users who author reports or models in Report Designer or Model Designer and then publish those items to a report server.  
  
> [!CAUTION]  
> Permission to publish items to a report server should be granted only to trusted users. The Publisher role grants wide-ranging permissions that allow users to upload any type of file to a report server. If an uploaded report or HTML file contains malicious script, any user who clicks on the report or HTML document will run the script under his or her credentials.  
  
 Report definitions can include script and other elements that are vulnerable to HTML injection attacks when the report is rendered in HTML at run time. If a published report contains malicious script, any user who runs that report will accidentally cause the script to run when the report is opened. If the user has elevated permissions, the script will run with those permissions.  
  
 To reduce the risk of users accidentally running malicious scripts, limit the number of users who have permission to publish content, and make sure that users only publish documents and reports that come from trusted sources. If you are not sure whether a report definition is safe to publish, you should open the .rdl file in a text editor and search for script tags. Malicious script can be hidden in expressions and URLs (for example, a URL in a navigation action).  
  
### Publisher tasks  
 The following table lists the tasks that are included in the **Publisher** role:  
  
|Task|Description|  
|----------|-----------------|  
|Create linked reports|Create linked reports and publish them to a report server folder.|  
|Manage comments|Delete other users' comments on reports.| 
|Manage data sources|Create and delete shared data source items, view and modify data source properties and content.|  
|Manage folders|Create, view, and delete folders; view and modify folder properties.|  
|Manage models|Create, view, and delete report models; view and modify report model properties.|  
|Manage reports|Add and delete reports, modify report parameters, view and modify report properties, view and modify data sources that provide content to the report, view, and modify report definitions.|  
|Manage resources|Create, modify, and delete resources; view and modify resource properties.|  
  
### Customizing the publisher role  
 You can modify the **Publisher** role to suit your needs. For example, you can remove the "Create linked reports" task if you do not want users to be able to create and publish linked reports, or you can add the "View folders" task so that users can navigate through the folder hierarchy when selecting a location for a new item.  
  
 At a minimum, users who publish reports from Report Designer need the "Manage reports" task to be able to add a report to the report server. If the user must publish reports that use shared data sources or external files, you should also include "Manage data sources" and "Manage resources." If the user also requires the ability to create a folder as part of the publishing process, you must also include "Manage folders."  
  
##  <a name="bkmk_browser"></a> Browser role  
 The **Browser** role is a predefined role that includes tasks that are useful for a user who views reports but does not necessarily author or manage them. This role provides basic capabilities for conventional use of a report server. Without these tasks, it may be difficult for users to use a report server.  
  
 The **Browser** role should be used with the **System User** role. Together, the two role definitions provide a complete set of tasks for users who interact with items on a report server. Although the **Browser** role provides view access to reports, report models, folders, and other items within the folder hierarchy, it does not provide access to site-level items such as shared schedules, which are useful to have when creating subscriptions. For this reason, we recommend that you create a second role assignment at the site level that provides access to shared schedules.  
  
### Browser tasks  
 The following table describes the tasks that are included in the **Browser** role:  
  
|Task|Description|  
|----------|-----------------|  
|Comment on reports|Create, view, edit, and delete comments on reports.| 
|Manage individual subscriptions|Create, view, modify, and delete user-owned subscriptions to reports and linked reports, and create schedules in support of those subscriptions.| 
|View folders|View folder contents and navigate the folder hierarchy.| 
|View models|View models in the folder hierarchy, use models as data sources for a report, and run queries against the model to retrieve data.| 
|View reports|Run a report and view report properties.|  
|View resources|View resources and resource properties.|  
   
### Customizing the browser role  
 You can modify the **Browser** role to suit your needs. For example, you can remove the "Manage individual subscriptions" task if you do not want to support subscriptions, or you can remove the "View resources" task if you do not want users to see collateral documentation or other items that might be uploaded to the report server.  
  
 At a minimum, this role should support both the "View reports" task and the "View folders" tasks to support viewing and folder navigation. You should not remove the "View folders" task unless you want to eliminate folder navigation. Likewise, you should not remove the "View reports task" unless you want to prevent users from seeing reports. These kinds of modifications suggest the need for a custom role definition that is applied selectively for a specific group of users.  
  
##  <a name="bkmk_reportbuilder"></a> Report Builder role  
 The **Report Builder** role is a predefined role that includes tasks for loading reports in Report Builder as well as viewing and navigating the folder hierarchy. To create and modify reports in Report Builder, you must also have a system role assignment that includes the "Execute report definitions" task, required for processing reports locally in Report Builder.  
  
### Report Builder tasks  
 The following table describes the tasks that are included in the **Report Builder** role:  
  
|Task|Description|  
|----------|-----------------|  
|Comment on reports|Create, view, edit, and delete comments on reports.| 
|Consume reports|Reads report definitions.|  
|Manage individual subscriptions|Create, view, modify, and delete user-owned subscriptions to reports and linked reports, and create schedules in support of those subscriptions.|  
|View folders|View folder contents and navigate the folder hierarchy.|  
|View models|View models in the folder hierarchy, use models as data sources for a report, and run queries against the model to retrieve data.|  
|View reports|Run a report and view report properties.|  
|View resources|View resources and resource properties.|  
  
### Customizing the Report Builder role  
 You can modify the **Report Builder** role to suit your needs. The recommendations are generally the same as for the **Browser** role: remove the "Manage individual subscriptions" task if you do not want to support subscriptions, remove the "View resources" task if you do not want users to see resources, and keep "View reports" task and the "View folders" tasks to support viewing and folder navigation.  
  
 The most important task in this role definition is "Consume reports", which allows a user to load a report definition from the report server into a local Report Builder instance. If you do not want to support this task, you can delete this role definition and use the **Browser** role to support general access to a report server.  
  
##  <a name="bkmk_myreports"></a> My Reports role  
 The **My Reports** role is a predefined role that includes a set of tasks that are useful for users of the My Reports feature. This role definition includes tasks that grant administrative permissions to users over the My Reports folder that they own.  
  
 Although you can choose another role to use with the My Reports feature, it is recommended that you choose one that is used exclusively for My Reports security. For more information, see [Secure My Reports](../../reporting-services/security/secure-my-reports.md).  
                          
### My Reports tasks  
 The following table lists tasks that are included in the **My Reports** role:  
  
|Task|Description|  
|----------|-----------------|  
|Comment on reports|Create, view, edit, and delete comments on reports.| 
|Create linked reports|Create linked reports that are based on reports that are stored in the user's My Reports folder.|  
|Manage comments|Delete other users' comments on reports.| 
|Manage data sources|Create and delete shared data source items, view, and modify data source properties and content.|  
|Manage folders|Create, view, and delete folders, and view and modify folder properties.|  
|Manage individual subscriptions|Create, view, modify, and delete subscriptions for reports and linked reports.|  
|Manage report history|Create, view, and delete report history, view report history properties, and view, and modify settings that determine snapshot history limits and how caching works.|  
|Manage reports|Add and delete reports, modify report parameters, view, and modify report properties, view and modify data sources that provide content to the report, view and modify report definitions, and set security policies at the report level.|  
|Manage resources|Create, modify, and delete resources, and view. and modify resource properties.|  
|View data sources|View shared data source items in the folder hierarchy.|  
|View folders|View folder contents.|  
|View reports|Run reports that are stored in the user's My Reports folder and view report properties.|  
|View resources|View resources and resource properties.|  
  
### Customizing the My Reports role  
 You can modify this role to suit your needs. However, it is recommended that you keep the "Manage reports" task and the "Manage folders" task to enable basic content management. In addition, this role should support all view-based tasks so that users can see folder contents and run the reports that they manage.  
  
 Although the "Set security for individual items" task is not part of the role definition by default, you can add this task to the **My Reports** role so that users can customize security settings for subfolders and reports.  
  
##  <a name="bkmk_systemadministrator"></a> System administrator role  
 The **System Administrator** role is a predefined role that includes tasks that are useful for a report server administrator who has overall responsibility for a report server, but not necessarily for the content within it.  
  
 To create a role assignment that includes this role, use the Site Settings page in the web portal, or use the right-click commands on the report server node in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 The **System Administrator** role does not convey the same full range of permissions that a local administrator might have on a computer. Rather, the **System Administrator** role includes operations that are performed at the site level, and not the item level. For users who require access to both site-wide operations and items stored on the report server, create a second role assignment on the Home folder that includes the **Content Manager** role. Together, the two role definitions provide a complete set of tasks for users who require full access to all items on a report server.  
  
### System administrator tasks  
 The following table lists tasks that are included in the **System Administrator** role:  
  
|Task|Description|  
|----------|-----------------|  
|Execute report definitions|Start execution for report definition without publishing it to a report server.|  
|Manage jobs|View and cancel jobs that are running. For more information, see [Manage a Running Process](../../reporting-services/subscriptions/manage-a-running-process.md).|  
|Manage report server properties|View and modify properties that apply to the report server and to items that the report server manages.<br /><br /> This task supports renaming the web portal, enabling My Reports, and setting report history defaults.|  
|Manage report server security|View and modify system-wide role assignments|  
|Manage roles|Create, view, and modify, and delete role definitions.<br /><br /> Members of the **System Administrator** role can use the Site Settings page to manage roles.|  
|Manage shared schedules|Create, view, modify, and delete shared schedules that are used to run or refresh reports.|  
  
 The **System Administrator** role is used in default security.  
  
##  <a name="bkmk_systemuser"></a> System user role  
The **System User** role is a predefined role that includes tasks that allow users to view basic information about the report server. It also includes support for loading a report in Report Builder. Report Builder is a client application that can process a report independently of a report server. The "Execute report definitions" task is intended for use with Report Builder. If you are not using Reporting Builder, you can remove this task from the **System User** role.  

The following table lists tasks that are included in the **System User** role definition:  
  
### System user tasks  
  
|Task|Description|  
|----------|-----------------|  
|Execute report definitions|Run a report without publishing it to a report server.|  
|View report server properties|View properties that apply to the report server, such as the application name, whether the My Reports setting is enabled, and report history defaults.<br /><br /> If you remove this task from the **System User** role, the Site Settings page is not available. Also, the application title is not displayed at the top of each page. By default, the title for the web portal is "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]."|  
|View shared schedules|View shared schedules that are used to run reports or refresh a report.<br /><br /> If you remove this task from the **System User** role, users cannot select shared schedules to use with subscriptions and other scheduled operations.|  
  
 The **System User** role can be used to supplement default security. You can include the role in new role assignments that extend report server access to report users. For more information, see [Granting Permissions on a Native Mode Report Server](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md).  
  
## See also  
[Create, Delete, or Modify a Role &#40;Management Studio&#41;](../../reporting-services/security/role-definitions-create-delete-or-modify.md)  
[Grant User Access to a Report Server](../../reporting-services/security/grant-user-access-to-a-report-server.md)  
[Modify or Delete a Role Assignment &#40;SSRS web portal&#41;](../../reporting-services/security/role-assignments-modify-or-delete.md)  
[Granting Permissions on a Native Mode Report Server](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
[Tasks and Permissions](../../reporting-services/security/tasks-and-permissions.md)
