---
title: "提示 (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- query optimizer [SQL Server], hints
- hints [SQL Server], about hints
- SELECT statement [SQL Server], hints
- hints [SQL Server]
- INSERT statement [SQL Server], hints
- UPDATE statement [SQL Server], hints
- DELETE statement [SQL Server], hints
ms.assetid: 99412475-b0df-4264-9938-33a0b302b41a
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d2d8b50a38299162677b1f7d5bbff501fba9881
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="hints-transact-sql"></a>提示 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  提示是指定的强制选项或策略，由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查询处理器针对 SELECT、INSERT、UPDATE 或 DELETE 语句执行。 提示将替换查询优化器可能会为查询选择的任何执行计划。  
  
> [!CAUTION]  
>  因为[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]查询优化器通常选择查询的最佳执行计划，我们建议， \<join_hint >， \<query_hint >，和\<table_hint > 只可用作最后一招由有经验开发人员和数据库管理员。
  
 本节将介绍下列提示：  
  
-   [联接提示](../../t-sql/queries/hints-transact-sql-join.md)  
  
-   [查询提示](../../t-sql/queries/hints-transact-sql-query.md)  
  
-   [表提示](../../t-sql/queries/hints-transact-sql-table.md)  
  
  
