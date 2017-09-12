---
title: "准备实现数据处理扩展插件 |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- interfaces [Reporting Services]
- data processing extensions [Reporting Services], implementing
ms.assetid: 698817e4-33da-4eb5-9407-4103e1c35247
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 6d516201d8018b1d58b77be8e3cf543745da037a
ms.contentlocale: zh-cn
ms.lasthandoff: 08/12/2017

---
# <a name="preparing-to-implement-a-data-processing-extension"></a>准备实现数据处理扩展插件
  在实现之前你[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]数据处理扩展插件，您应该定义这些接口，以便实现。 你可能想要提供特定于扩展的实现的接口，整个集或你可能只想要专注实现上一个子集，例如<xref:Microsoft.ReportingServices.DataProcessing.IDataReader>和<xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>接口在其中客户端将与一个结果集作为主要交互**DataReader**对象并将使用你[!INCLUDE[ssRS](../../../includes/ssrs-md.md)]作为结果集和数据源之间的桥梁的数据处理扩展插件。  
  
 然后，您可以通过以下两种方式之一实现数据处理扩展插件：  
  
-   你的数据处理扩展类可实现[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]数据提供程序接口和 （可选） 提供的扩展的数据处理扩展接口[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]。  
  
-   您的数据处理扩展插件类可以实现 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 提供的数据处理扩展插件接口，并且可以选择实现扩展数据处理扩展插件接口。  
  
 如果您的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件将不支持某一特定的属性或方法，则将该属性或方法作为无操作实现。 如果客户端需要一个特定的行为，引发**NotSupportedException**异常。  
  
> [!NOTE]  
>  某一属性或方法的无操作实现只应用于您选择实现的那些接口的属性和方法。 您选择不实现的可选接口应排除在您的数据处理扩展插件程序集之外。 有关某一接口是必需接口还是可选接口的详细信息，请参阅本节后面的表。  
  
## <a name="required-extension-functionality"></a>必需的扩展插件功能  
 每个 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件都必须提供以下功能：  
  
-   打开与数据源之间的连接。  
  
-   分析查询并返回结果集的字段名的列表。  
  
-   对数据源执行查询，并返回行集。  
  
-   将单值参数传递到查询。  
  
-   遍历行集中的行，并检索数据。  
  
 可以扩展每个数据处理扩展插件以包含以下功能：  
  
-   分析某一查询，并返回该查询中所使用的参数名称的列表。  
  
-   分析某一查询，并返回按该查询分组的字段的列表。  
  
-   分析某一查询，并返回按该查询排序的字段的列表。  
  
-   提供用户名和密码以连接到独立于连接字符串的数据源。  
  
-   遍历行集中的行，并检索与数据值有关的辅助元数据。  
  
-   在服务器聚合数据。  
  
## <a name="available-extension-interfaces"></a>可用的扩展插件接口  
 下表介绍可用接口以及实现是必需的还是可选的。  
  
|接口|Description|实现|  
|---------------|-----------------|--------------------|  
|IDbConnection|表示与某一数据源的唯一会话。 在客户端/服务器数据库系统的情况下，该会话可等效于到服务器的一个网络连接。|必需|  
|IDbConnectionExtension|表示可由 [!INCLUDE[ssRS](../../../includes/ssrs-md.md)] 数据处理扩展插件针对安全性和身份验证实现的附加连接属性。|選擇性|  
|IDbTransaction|表示本地事务。|必需|  
|IDbTransactionExtension|表示可由 [!INCLUDE[ssRS](../../../includes/ssrs-md.md)] 数据处理扩展插件实现的附加事务属性。|選擇性|  
|IDbCommand|表示在连接到数据源时使用的查询或命令。|必需|  
|IDbCommandAnalysis|表示用于分析某一查询并返回在该查询中使用的参数名称列表的附加命令信息。|選擇性|  
|IDataParameter|表示传递到命令或查询的参数或名称/值对。|必需|  
|IDataParameterCollection|表示与某一命令或查询相关的所有参数的集合。|必需|  
|IDataReader|提供从数据源读取数据的只进、只读流的方法。|必需|  
|IDataReaderExtension|提供一种方法来读取一个或多个通过在数据源执行命令所获得的只进结果集流。 此接口为字段聚合提供附加支持。|選擇性|  
|IExtension|为 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件提供基类。 还使实现者可为扩展插件包括本地化的名称并将配置设置从配置文件传递到扩展插件。|必需|  
  
 数据处理扩展插件接口将尽可能与 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 数据访问接口、方法和属性的子集完全相同。 有关实现完整 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 数据访问接口的详细信息，请参阅 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 软件开发包 (SDK) 文档中的“实现 .NET Framework 数据访问接口”。  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 扩展插件](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [实现数据处理扩展插件](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 扩展库](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  