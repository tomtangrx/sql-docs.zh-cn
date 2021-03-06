---
title: 上级 (MDX) |Microsoft 文档
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 464f8504850c6aa13f1cf040f9429be56f7181be
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739316"
---
# <a name="ancestor-mdx"></a>Ancestor (MDX)


  此函数返回指定成员在指定级别或距离处的祖先。  
  
## <a name="syntax"></a>语法  
  
```  
  
Level syntax  
Ancestor(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestor(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>参数  
 *Member_Expression*  
 返回成员的有效多维表达式 (MDX)。  
  
 *Level_Expression*  
 返回级别的有效多维表达式 (MDX)。  
  
 *距离*  
 指定与指定成员距离的有效数值表达式。  
  
## <a name="remarks"></a>Remarks  
 与**上级**函数，该函数提供的 MDX 成员表达式，然后提供的级别，该成员的祖先一个 MDX 表达式，或者表示的上面该成员的级别数的数值表达式。 使用此信息，**上级**函数返回在该级别的祖先成员。  
  
> [!NOTE]  
>  若要返回一个包含祖先成员，而不是只需祖先成员集使用[上级&#40;MDX&#41; ](../mdx/ancestors-mdx.md)函数。  
  
 如果指定一个级别表达式，则**上级**函数返回在指定的级别的指定成员的祖先。 如果指定成员与指定级别不在同一个层次结构中，该函数将返回错误。  
  
 如果指定的距离，则**上级**函数返回由成员表达式指定层次结构中指定设置的步骤数的指定成员的祖先。 可以将成员指定为属性层次结构的成员或用户定义层次结构的成员，有时还可以指定为父子层次结构的成员。 数值 1 返回成员的父成员，数值 2 返回成员的祖父成员（如果存在）。 数值 0 返回成员本身。  
  
> [!NOTE]  
>  使用这种形式的**上级**情况下在其中的父级别，未知或不能为命名的函数。  
  
## <a name="examples"></a>示例  
 下面的示例使用一个级别表达式，并返回 Australia 中每个 State-Province 的 Internet Sales Amount 及其占 Australia 总 Internet Sales Amount 的百分比。  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   (  
   [Measures].[Internet Sales Amount],    
      Ancestor   
         (  
         [Customer].[Customer Geography].CurrentMember,  
            [Customer].[Customer Geography].[Country]  
         )  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{  
   Descendants   
      (  
        [Customer].[Customer Geography].[Country].&[Australia],  
           [Customer].[Customer Geography].[State-Province], SELF   
      )  
} ON 1  
FROM [Adventure Works]  
```  
  
 下面的示例使用一个数值表达式，并返回 Australia 中每个 State-Province 的 Internet Sales Amount 及其占所有国家/地区总 Internet Sales Amount 的百分比。  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   (  
      [Measures].[Internet Sales Amount],  
         Ancestor   
            ([Customer].[Customer Geography].CurrentMember, 2)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{  
   Descendants   
      (  
         [Customer].[Customer Geography].[Country].&[Australia],  
            [Customer].[Customer Geography].[State-Province], SELF   
      )  
} ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>请参阅  
 [MDX 函数引用&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
