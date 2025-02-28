---
description: "Azure Blob Download Task"
title: "Azure Blob Download Task | Microsoft Docs"
ms.custom: ""
ms.date: "05/22/2019"
ms.service: sql
ms.reviewer: ""
ms.subservice: integration-services
ms.topic: conceptual
f1_keywords: 
  - "sql13.dts.designer.afpblobdltask.f1"
  - "sql14.dts.designer.afpblobdltask.f1"
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
author: chugugrace
ms.author: chugu
---
# Azure Blob Download Task

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


The Azure Blob Download Task enables an SSIS package to download files from Azure Blob Storage.

To add an **Azure Blob Download Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure Blob Download Task Editor** dialog box.  
  
 The **Azure Blob Download Task** is a component of the [SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  
  
 The following table provides description for the fields in this dialog box.  

|**Field**|**Description**|  
|---|---|
|AzureStorageConnection|Specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account, which points to where the blob files are hosted.|  
|BlobContainer|Specifies the name of the blob container that contains the blob files to be downloaded.|  
|BlobDirectory|Specifies the blob directory that contains the blob files to be downloaded. The blob directory is a virtual hierarchical structure.|  
|SearchRecursively|Specifies whether to search recursively within sub-directories.|  
|LocalDirectory|Specifies the local directory where the downloaded blob files are stored.|  
|FileName|Specifies a name filter to select files with the specified name pattern. For example, `MySheet*.xls\*` includes files such as `MySheet001.xls` and `MySheetABC.xlsx`.|  
|TimeRangeFrom/TimeRangeTo|Specifies a time range filter. Files modified after **TimeRangeFrom** and before **TimeRangeTo** are included.|  
