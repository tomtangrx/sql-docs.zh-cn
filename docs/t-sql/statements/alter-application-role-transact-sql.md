---
title: "更改应用程序角色 (Transact SQL) |Microsoft 文档"
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
- ALTER_APPLICATION_ROLE_TSQL
- ALTER APPLICATION ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- modifying application roles
- passwords [SQL Server], application roles
- ALTER APPLICATION ROLE statement
- application roles [SQL Server], modifying
ms.assetid: c6cd5d0f-18f4-49be-b161-64d9c5569086
caps.latest.revision: 46
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d5205897f64dfb05d8903ed2f4197f35bd722224
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="alter-application-role-transact-sql"></a>ALTER APPLICATION ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  更改应用程序角色的名称、密码或默认架构。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
ALTER APPLICATION ROLE application_role_name   
    WITH <set_item> [ ,...n ]  
  
<set_item> ::=   
    NAME = new_application_role_name   
    | PASSWORD = 'password'  
    | DEFAULT_SCHEMA = schema_name  
```  
  
## <a name="arguments"></a>参数  
 *application_role_name*  
 要修改的应用程序角色的名称。  
  
 名称 =*new_application_role_name*  
 指定应用程序角色的新名称。 该名称一定不能被用于引用数据库中任何主体。  
  
 密码 =*密码*  
 指定应用程序角色的密码。 *密码*必须符合 Windows 密码策略要求的计算机的运行的实例[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 应始终使用强密码。  
  
 DEFAULT_SCHEMA =*schema_name*  
 指定服务器在解析对象名时将搜索的第一个架构。 *schema_name*可以是数据库中不存在的架构。  
  
## <a name="remarks"></a>注释  
 如果数据库中已存在新的应用程序角色名称，则该语句将失败。 当更改应用程序角色的名称、密码或默认架构更改时，与该角色关联的 ID 将不会随之改变。  
  
> [!IMPORTANT]  
>  密码过期策略不适用于应用程序角色密码。 为此，选择强密码时要格外谨慎。 调用应用程序角色的应用程序必须存储其密码。  
  
 在 sys.database_principals 目录视图中可以查看应用程序角色。  
  
> [!CAUTION]  
>  在[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]架构的行为更改的早期版本中的行为[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 假设架构与数据库用户等效的代码可能不会返回正确的结果。 包括 sysobjects 在内的旧目录视图不应在曾经使用下列任何 DDL 语句的数据库中使用：CREATE SCHEMA、ALTER SCHEMA、DROP SCHEMA、CREATE USER、ALTER USER、DROP USER、CREATE ROLE、ALTER ROLE、DROP ROLE、CREATE APPROLE、ALTER APPROLE、DROP APPROLE、ALTER AUTHORIZATION。 在曾经使用过这些语句中的任意一个语句的数据库中，必须使用新的目录视图。 新的目录视图将采用在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中引入的使主体和架构分离的方法。 有关目录视图的详细信息，请参阅[目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)。  
  
## <a name="permissions"></a>Permissions  
 需要对数据库具有 ALTER ANY APPLICATION ROLE 权限。 若要更改默认架构，用户还需要对应用程序角色有 ALTER 权限。 应用程序角色可以修改其自身的默认架构，但不能修改其名称或密码。  
  
## <a name="examples"></a>示例  
  
### <a name="a-changing-the-name-of-application-role"></a>A. 更改应用程序角色的名称  
 以下示例将应用程序角色 `weekly_receipts` 的名称更改为 `receipts_ledger`。  
  
```  
USE AdventureWorks2012;  
CREATE APPLICATION ROLE weekly_receipts   
    WITH PASSWORD = '987Gbv8$76sPYY5m23' ,   
    DEFAULT_SCHEMA = Sales;  
GO  
ALTER APPLICATION ROLE weekly_receipts   
    WITH NAME = receipts_ledger;  
GO  
```  
  
### <a name="b-changing-the-password-of-application-role"></a>B. 更改应用程序角色的密码  
 以下示例将更改应用程序角色 `receipts_ledger` 的密码。  
  
```  
ALTER APPLICATION ROLE receipts_ledger   
    WITH PASSWORD = '897yUUbv867y$200nk2i';  
GO  
```  
  
### <a name="c-changing-the-name-password-and-default-schema"></a>C. 更改名称、密码和默认架构  
 以下示例将同时更改应用程序角色 `receipts_ledger` 的名称、密码和默认架构。  
  
```  
ALTER APPLICATION ROLE receipts_ledger   
    WITH NAME = weekly_ledger,   
    PASSWORD = '897yUUbv77bsrEE00nk2i',   
    DEFAULT_SCHEMA = Production;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [应用程序角色](../../relational-databases/security/authentication-access/application-roles.md)   
 [创建应用程序角色 &#40;Transact SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [删除应用程序角色 &#40;Transact SQL &#41;](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  