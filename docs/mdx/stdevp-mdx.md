---
title: StdevP (MDX) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STDEVP
dev_langs:
- kbMDX
helpviewer_keywords:
- StdevP function [MDX]
ms.assetid: cd8ae7c9-3cef-49f0-bb41-8f577c7b6f31
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d72eb148aafccc60aa5097c8c7fed7f8b842a583
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="stdevp-mdx"></a>StdevP (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Standardabweichung eines numerischen Ausdrucks, ausgewertet über einer Menge mithilfe der unausgewogenen Auffüllungsformel (geteilt durch  *n* ).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
StdevP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Hinweise  
 Die **StdevP** -Funktion verwendet die unausgewogene Auffüllung Formel, während die [Stdev](../mdx/stdev-mdx.md) Funktion der Formel für die ausgewogene Auffüllung verwendet.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Standardabweichung für Internet Order Quantity, ausgewertet über die ersten drei Monate des Kalenderjahres 2003, mithilfe der Formel für die unausgewogene Auffüllung zurückgegeben.  
  
```  
WITH MEMBER Measures.x AS   
   StdevP   
   ( { [Date].[Calendar].[Month].[January 2003],  
       [Date].[Calendar].[Month].[February 2003],  
       [Date].[Calendar].[Month].[March 2003]},  
    [Measures].[Internet Order Quantity])  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
