---
title: "Flush 方法 (ADO) |Microsoft 文档"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::Flush
- _Stream::raw_Flush
helpviewer_keywords:
- Flush method [ADO]
ms.assetid: 938522b4-f836-4c80-8d27-a598a000f0ee
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dc0e90c43b2f691f1dff705e813ffe77fe5fc35a
ms.contentlocale: zh-cn
ms.lasthandoff: 09/09/2017

---
# <a name="flush-method-ado"></a>Flush 方法 (ADO)
强制的内容[流](../../../ado/reference/ado-api/stream-object-ado.md)与其的基础对象的 ADO 缓冲区中剩余**流**关联。  
  
## <a name="syntax"></a>语法  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>注释  
 此方法可以用于将流缓冲区的内容发送到基础对象： 例如，节点或文件的源的 URL 表示**流**对象。 当你想要确保所有更改，应调用此方法对的内容进行了**流**都已写入。 但是，用 ADO 它通常没有必要调用**刷新**，如 ADO 连续刷新其缓冲区尽可能多地在后台。 内容的更改**流**自动进行，直到不缓存**刷新**调用。  
  
 关闭**流**与[关闭](../../../ado/reference/ado-api/close-method-ado.md)方法刷新的内容**流**自动; 存在则无需显式调用**刷新**立即之前**关闭**。  
  
## <a name="applies-to"></a>适用范围  
 [流对象 (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)