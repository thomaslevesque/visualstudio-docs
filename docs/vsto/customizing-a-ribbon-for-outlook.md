---
title: "Customizing a Ribbon for Outlook | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Inspectors [Office development in Visual Studio]"
  - "Outlook [Office development in Visual Studio], Ribbon"
  - "customizing the Ribbon, about customizing the Ribbon"
  - "custom Ribbon, about customizing the Ribbon"
  - "Ribbon [Office development in Visual Studio], Outlook"
ms.assetid: 11d10e72-806d-4d5e-b080-139bd8633eaa
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Customizing a Ribbon for Outlook
  When you customize the ribbon in Microsoft Office Outlook, you must consider where your custom ribbon will appear in the application. Outlook displays the ribbon in the main application user interface (UI) and in windows that open when users perform certain tasks, such as creating e-mail messages. These application windows are named inspectors.  
  
 ![link to video](../vsto/media/playvideo.gif "link to video") For a related video demonstration, see [How Do I: Use the Ribbon Designer to Customize the Ribbon in Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Adding a Custom Ribbon to the Main Application UI  
 The main application UI in Outlook is called the Explorer. If you are using the **Ribbon (Visual Designer)** item, you can add a ribbon to the Explorer by clicking the **RibbonType** property of the ribbon in the **Properties** window, and then selecting **Microsoft.Outlook.Explorer**.  
  
## Assigning a Ribbon to an Inspector  
 You identify the inspector you want to customize by specifying the ribbon type that corresponds to the message class for the Inspector.  
  
 If you are using the **Ribbon (Visual Designer)** item, click the **RibbonType** property of the ribbon in the **Properties** window, and then select one or more ribbon IDs from the list of values.  
  
 You can add more than one ribbon to a project. If more than one ribbon shares a ribbon ID, override the CreateRibbonExtensibilityObject method in the `ThisAddin` class of your project to specify which ribbon to display at run time. For more information, see [Ribbon Overview](../vsto/ribbon-overview.md). For more information about each ribbon type, see the technical article [Customizing the Ribbon in Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
## Specifying the Ribbon Type by Using Ribbon XML  
 If you are using the **Ribbon (XML)** item, check the value of the *ribbonID* parameter in the <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> method and return the appropriate ribbon.  
  
 The <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> method is automatically generated by Visual Studio in the ribbon code file. The *ribbonID* parameter is a string that identifies the Explorer or a specific type of inspector. For a complete list of the possible values of the *ribbonID* parameter, see the technical article [Customizing the Ribbon in Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
 The following code example demonstrates how to display a custom ribbon only in the `Microsoft.Outlook.Mail.Compose` inspector. This is the inspector that opens when a user creates a new e-mail message. The ribbon to display is specified in the `GetResourceText()` method, which is generated in the **Ribbon** class. For more information about the **Ribbon** class, see [Ribbon XML](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]  
  
## See Also  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Ribbon Overview](../vsto/ribbon-overview.md)   
 [Ribbon Designer](../vsto/ribbon-designer.md)   
 [Ribbon XML](../vsto/ribbon-xml.md)  
  
  