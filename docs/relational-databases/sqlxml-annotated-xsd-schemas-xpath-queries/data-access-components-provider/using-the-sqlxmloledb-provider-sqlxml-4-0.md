---
title: "使用 SQLXMLOLEDB Provider (SQLXML 4.0) |Microsoft 文档"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXMLOLEDB Provider, samples
- ClientSideXML property
ms.assetid: fbcefac5-29c9-478b-b0e0-d510b593f446
caps.latest.revision: "26"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3b4bceef061ed01e922c0c904e2559b812859783
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="using-the-sqlxmloledb-provider-sqlxml-40"></a>使用 SQLXMLOLEDB 访问接口 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]本部分中的主题提供 ADO 说明了 SQLXMLOLEDB 提供程序特定属性的用法的示例应用程序。  
  
## <a name="application-requirements-for-sqlxmloledb-40-provider"></a>SQLXMLOLEDB 4.0 访问接口的应用程序要求  
 若要创建使用 SQLXMLOLEDB 4.0 的工作示例，必须执行以下操作：  
  
1.  创建 Microsoft Visual Basic .exe 应用程序，并添加以下引用之一：  
  
    -   Microsoft ActiveX 数据对象 2.6 库  
  
    -   Microsoft ActiveX 数据对象 2.7 库  
  
    -   Microsoft ActiveX Data Objects 2.8 Library  
  
2.  部署和安装 SQLXML 4.0 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。  
  
     有关详细信息，请参阅上[SQLXML 4.0 编程概念](../../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)和[安装 SQL Server Native Client](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)。  
  
## <a name="in-this-section"></a>本节内容  
 [执行 SQL 查询 &#40;SQLXMLOLEDB Provider &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-sql-queries-sqlxmloledb-provider.md)  
 演示如何使用 ClientSideXML 和 xml 根属性，以执行 SQL 查询。  
  
 [执行包含 SQL 查询 &#40; 的模板SQLXMLOLEDB Provider &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md)  
 演示如何使用 ClientSideXML 属性。  
  
 [正在执行 XPath 查询 &#40;SQLXMLOLEDB Provider &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-sqlxmloledb-provider.md)  
 演示如何使用 ClientSideXML、 基路径和映射架构属性。  
  
 [使用命名空间 &#40; 正在执行 XPath 查询SQLXMLOLEDB Provider &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md)  
 说明如何针对已限定命名空间的架构进行查询。  
  
 [执行包含 XPath 查询 &#40; 的模板SQLXMLOLEDB Provider &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-xpath-queries-sqlxmloledb-provider.md)  
 演示如何使用 SQL 查询使用 ClientSideXML、 基路径和映射架构属性执行模板。  
  
 [应用 XSL 转换 &#40;SQLXMLOLEDB Provider &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/applying-an-xsl-transformation-sqlxmloledb-provider.md)  
 演示如何在应用 XSL 转换的 ClientSideXML 和 xsl 属性使用。  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server Native Client 的系统要求](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md)  
  
  