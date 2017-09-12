---
title: "创建派生层次结构 (Master Data Services) |Microsoft 文档"
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
- derived hierarchies, creating
- creating derived hierarchies [Master Data Services]
ms.assetid: fec653c4-11cc-46a2-8dd8-b605341ebb40
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 65676239fa42e9e9f067dbd1973c005bd4198180
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-derived-hierarchy-master-data-services"></a>创建派生层次结构 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中，在您需要确保成员存在于正确级别的基于级别的层次结构时，创建派生层次结构。 派生层次结构基于在模型中存在的基于域的属性关系。  
  
> [!NOTE]  
>  如果对于某一成员不存在基于域的属性值，则在派生层次结构中将不包括该成员。 若要获取针对所有成员的基于域的属性值，请参阅[要求属性值 (Master Data Services)](../master-data-services/require-attribute-values-master-data-services.md)。  
  
## <a name="prerequisites"></a>先决条件  
 若要执行此过程：  
  
-   您必须有权访问 **“系统管理”** 功能区域。  
  
-   您必须是模型管理员。 有关详细信息，请参阅[管理员 (Master Data Services)](../master-data-services/administrators-master-data-services.md)。  
  
### <a name="to-create-a-derived-hierarchy"></a>创建派生层次结构  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。  
  
2.  从菜单栏中，指向“管理”，然后单击“派生层次结构”。  
  
3.  在 **“派生层次结构维护”** 页上，从 **“模型”** 列表中，选择某一模型。  
  
4.  单击 **“添加”**。  
  
5.  在 **“添加派生层次结构”** 页上的 **“派生层次结构名称”** 框中，键入层次结构的名称。  
  
    > [!TIP]  
    >  使用在层次结构中描述级别的名称，例如， **Product to Subcategory to Category**。  
  
6.  单击 **“保存派生层次结构”**。  
  
7.  在“编辑派生层次结构”页上的“可用实体和层次结构”窗格中，单击某一实体或层次结构并将其拖到“当前级别”窗格的“在此处放置父级”中。  
  
8.  继续拖动实体或层次结构，直到完成您的层次结构。  
  
9. 单击 **“上一步”**。  
  
## <a name="see-also"></a>另请参阅  
 [派生层次结构 &#40;Master Data Services &#41;](../master-data-services/derived-hierarchies-master-data-services.md)   
 [具有显式顶端 &#40; 派生层次结构Master Data Services &#41;](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [基于域的属性 &#40;Master Data Services &#41;](../master-data-services/domain-based-attributes-master-data-services.md)  
  
  