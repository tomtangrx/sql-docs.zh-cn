---
title: "SET ANSI_DEFAULTS (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET ANSI_DEFAULTS
- ANSI_DEFAULTS
- SET_ANSI_DEFAULTS_TSQL
- ANSI_DEFAULTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ANSI_DEFAULTS option
- SET ANSI_DEFAULTS statement
ms.assetid: bd721d97-6e23-488b-8c8c-c0453d5b3b86
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 170fb1f5a95b9f6fe4fbe596906595475175b1a2
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="set-ansidefaults-transact-sql"></a>SET ANSI_DEFAULTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  控制一组可共同指定某种 ISO 标准行为的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 设置。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
-- Syntax for SQL Server  
  
SET ANSI_DEFAULTS { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_DEFAULTS ON;  
```  
  
## <a name="remarks"></a>注释  
 SET ANSI_DEFAULTS 是客户端不会修改的服务器端设置。 客户端管理自己的设置。 在默认情况下，这些设置与服务器设置相反。 用户不应修改服务器设置。 若要更改客户端行为，用户应使用 SQL_COPT_SS_PRESERVE_CURSORS。 有关详细信息，请参阅[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)。  
  
 当启用 (ON) 时，此选项将启用下列 ISO 设置：  
  
|||  
|-|-|  
|SET ANSI_NULLS|SET CURSOR_CLOSE_ON_COMMIT|  
|SET ANSI_NULL_DFLT_ON|SET IMPLICIT_TRANSACTIONS|  
|SET ANSI_PADDING|SET QUOTED_IDENTIFIER|  
|SET ANSI_WARNINGS||  
  
 这些 ISO 标准 SET 选项共同定义了用户工作会话、运行触发器或存储过程执行期间的查询处理环境。 不过，这些 SET 选项并未包括遵守 ISO 标准所需的所有选项。  
  
 在处理计算列和索引视图上的索引时，必须将这四个默认选项（ANSI_NULLS、ANSI_PADDING、ANSI_WARNINGS 和 QUOTED_IDENTIFIER）设置为 ON。 这些默认选项是七个 SET 选项中的一部分，当您在计算列和索引视图上创建和更改索引时，必须给这七个选项分配必需的值。 另外三个 SET 选项分别是：ARITHABORT (ON)、CONCAT_NULL_YIELDS_NULL (ON) 和 NUMERIC_ROUNDABORT (OFF)。 计算列上具有索引的视图和索引所需的 SET 选项设置的详细信息，请参阅"当你使用 SET 语句的注意事项"中[SET 语句 &#40;Transact SQL &#41;](../../t-sql/statements/set-statements-transact-sql.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]本机客户端 OLE DB Provider for[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]连接时自动将 ANSI_DEFAULTS 设置为 ON。 然后，驱动程序和访问接口将 CURSOR_CLOSE_ON_COMMIT 和 IMPLICIT_TRANSACTIONS 设置为 OFF。 SET CURSOR_CLOSE_ON_COMMIT 和 SET IMPLICIT_TRANSACTIONS 的 OFF 设置可以在 ODBC 数据源、ODBC 连接特性或 OLE DB 连接属性（它们在连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前在应用程序中设置）中进行配置。 对于 DB-Library 应用程序的连接，SET ANSI_DEFAULTS 默认为 OFF。  
  
 当发出 SET ANSI_DEFAULTS 时，ET QUOTED_IDENTIFIER 将在分析时设置，而下列选项则在执行时设置：  
  
|||  
|-|-|  
|SET ANSI_NULLS|SET ANSI_WARNINGS|  
|SET ANSI_NULL_DFLT_ON|SET CURSOR_CLOSE_ON_COMMIT|  
|SET ANSI_PADDING|SET IMPLICIT_TRANSACTIONS|  
  
## <a name="permissions"></a>Permissions  
 要求 **公共** 角色具有成员身份。  
  
## <a name="examples"></a>示例  
 下面的示例设置了 `SET ANSI_DEFAULTS ON` 并使用 `DBCC USEROPTIONS` 语句显示受影响的设置。  
  
```  
-- SET ANSI_DEFAULTS ON.  
SET ANSI_DEFAULTS ON;  
GO  
-- Display the current settings.  
DBCC USEROPTIONS;  
GO  
-- SET ANSI_DEFAULTS OFF.  
SET ANSI_DEFAULTS OFF;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [DBCC USEROPTIONS &#40;Transact SQL &#41;](../../t-sql/database-console-commands/dbcc-useroptions-transact-sql.md)   
 [SET 语句 (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [设置 ANSI_NULL_DFLT_ON &#40;Transact SQL &#41;](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)   
 [SET ANSI_NULLS (Transact-SQL)](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING (Transact-SQL)](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS (Transact-SQL)](../../t-sql/statements/set-ansi-warnings-transact-sql.md)   
 [设置 CURSOR_CLOSE_ON_COMMIT &#40;Transact SQL &#41;](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md)   
 [设置 IMPLICIT_TRANSACTIONS &#40;Transact SQL &#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [SET QUOTED_IDENTIFIER (Transact-SQL)](../../t-sql/statements/set-quoted-identifier-transact-sql.md)  
  
  