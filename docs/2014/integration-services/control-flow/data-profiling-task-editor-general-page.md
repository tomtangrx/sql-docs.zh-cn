---
title: 数据事件探查任务编辑器（常规页）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataprofilingtask.general.f1
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: eec15906-d757-4079-b2f6-aca4e52b3b4c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8e6bf10248bb3d8f280a24191634392df3b4ff5c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084819"
---
# <a name="data-profiling-task-editor-general-page"></a>数据事件探查任务编辑器（常规页）
  可以使用 **“数据事件探查任务编辑器”** 的 **“常规”** 页配置以下选项：  
  
-   指定配置文件输出的目标。  
  
-   使用默认设置可简化对单个表或视图进行事件探查的任务。  
  
 有关如何使用数据事件探查任务的详细信息，请参阅 [设置数据事件探查任务](data-profiling-task.md)。 有关如何使用数据配置文件查看器分析数据事件探查任务输出的详细信息，请参阅 [数据配置文件查看器](data-profile-viewer.md)。  
  
 **打开“数据事件探查任务编辑器”的“常规”页**  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开具有该数据事件探查任务的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。  
  
2.  在“控制流”选项卡上，双击数据事件探查任务。  
  
3.  在 **“数据事件探查任务编辑器”** 中，单击 **“常规”**。  
  
## <a name="data-profiling-options"></a>数据事件探查选项  
 **超时**  
 指定一个秒数，在这段时间之后数据事件探查任务应超时并停止运行。 默认值为 0，表示无超时。  
  
## <a name="destination-options"></a>目标选项  
  
> [!IMPORTANT]  
>  输出文件可能包含有关数据库的敏感数据和数据库所包含的数据。 有关如何使此文件更加安全的建议，请参阅 [访问包使用的文件](../access-to-files-used-by-packages.md)。  
  
 **目标类型**  
 指定将数据配置文件输出保存到文件，还是保存到变量：  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|**文件连接**|将配置文件输出保存到文件，位置为文件连接管理器中指定的位置。<br /><br /> 注意：请在“目标”选项中指定要使用的文件连接管理器。 |  
|**变量**|将配置文件输出保存到包变量。<br /><br /> 注意：请在“目标”选项中指定要使用的包变量。 |  
  
 **目标**  
 指定哪个文件连接管理器或包变量包含数据配置文件输出：  
  
-   如果将 **“目标类型”** 选项设置为 **“文件连接”**，则 **“目标”** 选项显示可用文件连接服务器。 选择这些连接管理器中的一个，或选择“\<新建文件连接>”创建新的文件连接管理器。  
  
-   如果将 **“目标类型”** 选项设置为 **“变量”**，则 **“目标”** 选项显示 **“目标”** 列表中可用的包变量。 选择这些变量中的一个，或选择“\<新建变量>”创建新变量。  
  
 **OverwriteDestination**  
 如果输出文件已经存在，则指定是否将其覆盖。 默认值为 **False**。 只有在“目标类型”选项设置为“文件连接”时才使用此属性的值。 当“目标类型”选项设置为变量时，任务将始终覆盖该变量以前的值。  
  
> [!IMPORTANT]  
>  如果尝试多次运行数据事件探查任务时，不更改输出文件名或将 **OverwriteDestination** 属性的值更改为 **True**，则该任务将以输出文件已存在的消息失败。  
  
## <a name="other-options"></a>其他选项  
 **快速配置文件**  
 显示“单个表快速配置文件窗体”。 此窗体使用默认设置简化了探查单个表或视图的任务。 有关详细信息，请参阅[单个表快速配置文件窗体（数据事件探查任务）](single-table-quick-profile-form-data-profiling-task.md)。  
  
 **打开配置文件查看器**  
 打开数据配置文件查看器。 独立数据配置文件查看器显示数据事件探查任务的数据配置文件输出。 可以在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包内运行数据事件探查任务并计算数据配置文件之后，查看这些数据配置文件输出。  
  
> [!NOTE]  
>  还可以通过在文件夹 \<drive>:\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn 中运行 DataProfileViewer.exe 来打开数据配置文件查看器。  
  
## <a name="see-also"></a>请参阅  
 [单个表快速配置文件窗体&#40;数据事件探查任务&#41;](single-table-quick-profile-form-data-profiling-task.md)   
 [数据事件探查任务编辑器（“配置文件请求”页）](data-profiling-task-editor-profile-requests-page.md)  
  
  
