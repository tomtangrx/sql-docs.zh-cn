---
title: 列分布 （数据挖掘） |Microsoft 文档
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 83da6c1ba0a278d2d6b80f309a7bc7f6a1688ba4
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
ms.locfileid: "34014104"
---
# <a name="column-distributions-data-mining"></a>列分布（数据挖掘）
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中，可以定义挖掘结构中的列分布以影响在创建挖掘模型时算法如何处理这些列中的数据。 对于某些算法，如果已知列中包含常用的值分布，则在处理模型之前定义任意连续列的分布将非常有用。 如果不定义分布，则由于算法据以解释数据的信息较少，生成的挖掘模型产生的预测可能不如定义了分布时产生的预测精确。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中可用的算法支持下列分布类型：  
  
 **Normal**  
 连续列的值构成一个正态分布直方图。  
  
 ![与正态的分布的直方图](../../analysis-services/data-mining/media/normal-distribution.gif "正态分布直方图")  
  
 **Log Normal**  
 连续列的值构成一个直方图，其曲线在较高端延长并向较低端倾斜。  
  
 ![具有日志正态分布的直方图](../../analysis-services/data-mining/media/log-normal-distribution.gif "与对数正态分布的直方图")  
  
 **Uniform**  
 连续列的值构成平坦曲线，曲线上的所有值都具有相同概率。  
  
 ![使用均匀分布的直方图](../../analysis-services/data-mining/media/uniform-distribution.gif "使用均匀分布的直方图")  
  
 有关 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 提供的算法的详细信息，请参阅[数据挖掘算法（Analysis Services - 数据挖掘）](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)。  
  
## <a name="see-also"></a>另请参阅  
 [内容类型 & #40; 数据挖掘 & #41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [挖掘结构 & #40;Analysis Services-数据挖掘 & #41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [离散化方法 & #40; 数据挖掘 & #41;](../../analysis-services/data-mining/discretization-methods-data-mining.md)   
 [分发 & #40; DMX & #41;](../../dmx/distributions-dmx.md)   
 [挖掘结构列](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
