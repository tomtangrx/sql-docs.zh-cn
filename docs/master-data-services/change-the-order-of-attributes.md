---
title: "更改属性的顺序 |Microsoft 文档"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 835a032c-e37c-4f35-8ab0-5e4ae25c2e9b
caps.latest.revision: 5
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 403b8824c09993b79f82422ba9136db73b2f7eb7
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="change-the-order-of-attributes"></a>更改属性的顺序
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，可以更改属性的顺序。  
  
## <a name="prerequisites"></a>先决条件  
 若要执行此过程：  
  
-   您必须有权访问 **“系统管理”** 功能区域。  
  
-   您必须是模型管理员。 有关详细信息，请参阅[管理员 (Master Data Services)](../master-data-services/administrators-master-data-services.md)。  
  
### <a name="to-change-the-order-of-an-attribute"></a>更改属性的顺序  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。  
  
2.  在“管理模型”  页上，从网格中选择一个模型，然后单击“实体” 。  
  
3.  在“管理实体”  页上，选择要为其创建属性的实体所在的行。  
  
4.  单击 **“属性”**。  
  
5.  在“管理属性”  页上，执行下列操作之一。  
  
    -   如果是叶成员的属性，请从“成员类型”  列表框中选择“叶”  。  
  
    -   如果属性是针对合并成员，则从“成员类型”  列表框中选择“合并”  。  
  
    -   如果属性是针对集合，则从“成员类型”  列表框中选择“集合”  。  
  
6.  选择要更改其顺序的属性所在的行。  
  
    > [!NOTE]  
    >  不能更改 Name 或 Code 属性的顺序。  
  
7.  单击“上移”或“下移”。  
  
## <a name="see-also"></a>另请参阅  
 [属性 &#40;Master Data Services &#41;](../master-data-services/attributes-master-data-services.md)  
  
  