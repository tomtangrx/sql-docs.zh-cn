---
title: "安装 SQL Server Native Client |Microsoft 文档"
ms.custom: 
ms.date: 07/15/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|applications
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, uninstalling
- SQLNCLI, installing
- SQLNCLI, uninstalling
- Setup [SQL Server Native Client]
- uninstalling SQL Server Native Client
- data access [SQL Server Native Client], uninstalling SQL Server Native Client
- installing SQL Server Native Client
- SQL Server Native Client, installing
- data access [SQL Server Native Client], installing SQL Server Native Client
- removing SQL Server Native Client
ms.assetid: c6abeab2-0052-49c9-be79-cfbc50bff5c1
caps.latest.revision: "44"
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 96dba471bb1b3de2b04561392b29eaa173bed6a0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="installing-sql-server-native-client"></a>安装 SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
 > 与以前版本的 SQL Server 相关的内容，请参阅[安装 SQL Server Native Client](https://msdn.microsoft.com/en-US/library/ms131321(SQL.120).aspx)。

[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 你安装时安装[!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)]。 
 
 没有任何 SQL Server 2016 Native Client。 有关详细信息，请参阅[SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client.md)。 
 
你还可以从 SQL Server 2012 功能包网页获取 sqlncli.msi。 若要下载最新版本的 SQL Server Native Client，请转到[Microsoft® SQL Server® 2012年功能包](http://www.microsoft.com/en-us/download/confirmation.aspx?id=29065)。 如果以前版本的[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]早于的计算机上，也安装 SQL Server 2012 Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 将与该早期版本并行安装。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 文件（sqlncli11.dll、sqlnclir11.rll 和 s11ch_sqlncli.chm）将安装到以下位置：  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序的所有相应注册表设置都将在安装过程中完成。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 头文件和库文件（sqlncli.h 和 sqlncli11.lib）安装在以下位置：  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 除了安装[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]作为的一部分的本机客户端[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]安装，也没有名为 sqlncli.msi，可以找到的可再发行安装程序[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]安装磁盘，在以下位置：`%CD%\Setup\`.  
  
 您可以通过 sqlncli.msi 分发 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。 在您部署某一应用程序时，可能需要安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。 安装多个包（对于用户而言就像是一次安装）的一种方法就是使用链接器和引导程序技术。 有关详细信息，请参阅[为 Visual Studio 2005 创作自定义引导程序包](http://go.microsoft.com/fwlink/?LinkId=115667)和[添加自定义系统必备组件](http://go.microsoft.com/fwlink/?LinkId=115668)。  
  
 sqlncli.msi 的 x64 和 Itanium 版本也会安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 的 32 位版。 如果您的应用程序所针对的目标平台并非其开发时所使用的平台，则可以从 Microsoft 下载中心下载针对 x64、Itanium 和 x86 的 sqlncli.msi 版本。  
  
 在调用 sqlncli.msi 时，默认情况下只会安装客户端组件。 这些客户端组件即为那些支持运行使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 开发的应用程序的文件。 若还要安装 SDK 组件，请在命令行中指定 `ADDLOCAL=All`。 例如：  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a>无提示安装  
 如果您将 /passive、/qn、/qb 或 /qr 选项与 msiexec 一起使用，则必须还指定 IACCEPTSQLNCLILICENSETERMS=YES，以便显式指示您接受最终用户许可协议条款。 必须以全大写字母指定此选项。  
  
## <a name="uninstalling-sql-server-native-client"></a>卸载 SQL Server Native Client  
 因为应用程序，如[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]服务器和[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]工具依赖于[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]本机客户端，它将一定不能卸载[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]本机客户端之前卸载所有的从属应用程序。 提供程序具有的用户取决于你的应用程序的警告[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]本机客户端，使用 APPGUID 安装中的选项你 MSI，如下所示：  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 传递给 APPGUID 的值是您的特定产品代码。 当使用 Microsoft Installer 捆绑应用程序安装程序时，必须创建产品代码。  
  
## <a name="see-also"></a>另请参阅  
 [使用 SQL Server Native Client 生成应用程序](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)   
 [安装操作指南主题](http://msdn.microsoft.com/library/59de41e7-557f-462a-8914-53ec35496baa)  
  
  