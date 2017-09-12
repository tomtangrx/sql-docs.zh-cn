---
title: "Reporting services 服务应用程序配置电子邮件 |Microsoft 文档"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f
caps.latest.revision: 13
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 7d5bc198ae3082c1b79a3a64637662968b0748b2
ms.openlocfilehash: d7fb8e7ae95ef5606b42db3b0622a90a4bdd7990
ms.contentlocale: zh-cn
ms.lasthandoff: 08/17/2017

---
# <a name="configure-e-mail-for-a-reporting-services-service-application"></a>为 Reporting Services 服务应用程序配置电子邮件

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]数据警报，则会在电子邮件中发送警报。 若要发送电子邮件，您可能需要配置 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序，并可能需要修改该服务应用程序的电子邮件传递扩展插件。 如果您计划将电子邮件传递扩展插件用于 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 订阅功能，则也需要进行电子邮件设置。  

> [!NOTE]
> 与 SharePoint 的 reporting Services 集成 SQL Server 2016 之后将不再可用。
  
### <a name="to-configure-e-mail-for-the-shared-service"></a>为共享服务配置电子邮件  
  
1.  在 SharePoint 管理中心中，单击 **“应用程序管理”**。  
  
2.  在 **“服务应用程序”** 组中，单击 **“管理服务应用程序”**。  
  
3.  在 **“名称”** 列表中，单击 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序的名称。  
  
4.  在“管理 Reporting Services 应用程序”页上，单击“电子邮件设置”。  
  
5.  选择 **“使用 SMTP 服务器”**。  
  
6.  在 **“出站 SMTP 服务器”** 框中，键入 SMTP 服务器的名称。  
  
7.  在“发件人地址”框中，键入电子邮件地址。  
  
     此地址为所有警报电子邮件的发件人。  
  
     **“发件人地址”** 中指定的用户帐户必须是您为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序配置应用程序池时指定的托管帐户。 如果您具有权限，则可以在 SharePoint 管理中心的“服务帐户”页上查看现有托管帐户的列表。  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="ntlm-authentication"></a>NTLM 身份验证  
  
1.  如果您的电子邮件环境需要 NTLM 身份验证且不允许匿名访问，则需要修改 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序的电子邮件传递扩展插件配置。 例如，如果你在“管理订阅”  页面上的“上次结果”  中看到以下页面：订阅。  
  
    -   发送邮件失败：SMTP 服务器需要安全连接或客户端未经身份验证。 服务器响应为：5.7.1 客户端未经身份验证 将不重新发送邮件。  
  
     对 **SMTPAuthenticate** 进行更改，令其使用值“2”。 无法从用户界面更改此值。 以下 PowerShell 脚本示例更新了名为“SSRS_TESTAPPLICATION”的服务应用程序的报表服务器电子邮件传递扩展插件的完全配置。 请注意，此脚本中列出的某些节点（例如“发件人”地址）也可从用户界面进行设置。  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRS_TESTAPPLICATION *"}  
    $emailCfg = Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml   
    $emailXml = [xml]$emailCfg   
    $emailXml.SelectSingleNode("//SMTPServer").InnerText = “your email server name"  
    $emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
    $emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
    $emailXml.SelectSingleNode("//From").InnerText = “your FROM email address”  
    Set-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
    ```  
  
2.  如果需要验证服务应用程序的名称，请运行 **Get-SPRSServiceApplication cmdlet**。  
  
    ```  
    get-sprsserviceapplication  
    ```  
  
3.  以下示例将返回名为“SSRS_TESTAPPLICATION”的服务应用程序的电子邮件扩展插件的当前值。  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRSTEST_APPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
    ```  
  
4.  以下示例将使用名为“SSRS_TESTAPPLICATION”的服务应用程序的电子邮件扩展插件的当前值创建名为“emailconfig.txt”的新文件。  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRS_TESTAPPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml | out-file c:\emailconfig.txt  
    ```  
  
  
更多问题？ [尝试的 Reporting Services 论坛](http://go.microsoft.com/fwlink/?LinkId=620231)