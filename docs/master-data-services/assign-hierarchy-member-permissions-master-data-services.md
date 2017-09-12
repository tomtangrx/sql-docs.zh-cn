---
title: "分配层次结构成员权限 (Master Data Services) |Microsoft 文档"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions [Master Data Services], assigning member permissions
- members [Master Data Services], assigning permissions
ms.assetid: e1b8b46a-7cd1-4a7d-9345-dd7df081e145
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f7a7e6cafe48506446396b83200d4d2343aa7949
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="assign-hierarchy-member-permissions-master-data-services"></a>分配层次结构成员权限 (Master Data Services)
  向层次结构成员分配权限，以便使用户或组具有在 **的** “资源管理器” [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]功能区域中查看数据的权限。  
  
 层次结构成员权限是可选的。 它们增加了模型对象权限所需的粒度。  
  
## <a name="prerequisites"></a>先决条件  
 若要执行此过程：  
  
-   您必须有权访问 **“用户和组权限”** 功能区域。  
  
-   您必须是模型管理员。 有关详细信息，请参阅[管理员 (Master Data Services)](../master-data-services/administrators-master-data-services.md)。  
  
### <a name="to-assign-hierarchy-member-permissions"></a>分配层次结构成员权限  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“用户和组权限”**。  
  
2.  在 **“用户”** 或 **“组”** 页上，选择要编辑的用户或组所对应的行。  
  
3.  单击 **“编辑所选用户”**。  
  
4.  单击 **“层次结构成员”** 选项卡。  
  
5.  从 **“模型”** 列表中，选择某一模型。  
  
6.   从“版本”列表中，选择某一版本。  
  
7.  从 **“层次结构”** 列表中，选择某一层次结构。  
  
8.  单击 **“编辑”**。  
  
9. 展开树，单击要向其分配权限的层次结构节点。  
  
10. 从菜单中，选择“创建”、“读取”、“更新”和“删除”权限的组合，或选择“拒绝”权限。  
  
11. 单击 **“保存”**。  
  
    > [!NOTE]  
    >  层次结构成员权限不立即生效。 有关详细信息，请参阅[立即应用成员权限 (Master Data Services)](../master-data-services/immediately-apply-member-permissions-master-data-services.md)。  
  
## <a name="see-also"></a>另请参阅  
 [删除层次结构成员权限 (Master Data Services)](../master-data-services/delete-hierarchy-member-permissions-master-data-services.md)   
 [分配模型对象权限 &#40;Master Data Services &#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [层次结构成员权限 &#40;Master Data Services &#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  