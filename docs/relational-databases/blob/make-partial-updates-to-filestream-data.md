---
title: "对 FILESTREAM 数据进行部分更新 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-blob
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
- FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
ms.assetid: d6f7661e-6c14-4d31-9541-4520ca0f82b2
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 58c80c57cf896bdda9b653aa15f348a0f9a3edd6
ms.contentlocale: zh-cn
ms.lasthandoff: 06/22/2017

---
# <a name="make-partial-updates-to-filestream-data"></a>对 FILESTREAM 数据进行部分更新
  应用程序使用 FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT 对 FILESTREAM BLOB 数据进行部分更新。 [DeviceIoControl](http://go.microsoft.com/fwlink/?LinkId=105527) 函数将此值和从 [OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) 返回的句柄传递到 FILESTREAM 驱动程序。 然后，该驱动程序将当前的 FILESTREAM 数据从服务器端强制复制到该句柄所引用的文件。 如果应用程序在已写入句柄后发出 FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT 值，则保留最后一个写入操作，但之前对该句柄执行的写入操作将丢失。  
  
> [!NOTE]  
>  FILESTREAM 依赖于 [SMB 协议](http://go.microsoft.com/fwlink/?LinkId=112454) 进行远程访问。  
  
## <a name="example"></a>示例  
 下面的示例显示如何使用 `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` 值对插入的 FILESTREAM BLOB 执行部分更新。  
  
> [!NOTE]  
>  本示例需要在 [创建启用 FILESTREAM 的数据库](../../relational-databases/blob/create-a-filestream-enabled-database.md) 和 [创建表以存储 FILESTREAM 数据](../../relational-databases/blob/create-a-table-for-storing-filestream-data.md)中创建的启用了 FILESTREAM 的数据库和表。  
  
 [!code-cpp[FILESTREAM#FS_CPP_FSCTL](../../relational-databases/blob/codesnippet/cpp/make-partial-updates-to-_1.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [使用 OpenSqlFilestream 访问 FILESTREAM 数据](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)   
 [为 FILESTREAM 数据创建客户端应用程序](../../relational-databases/blob/create-client-applications-for-filestream-data.md)  
  
  