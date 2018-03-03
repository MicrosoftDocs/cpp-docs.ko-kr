---
title: "정수를 부동 소수점 값으로 캐스팅 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d926b50cdd8caef1a1119aaf319bfae88970651
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="casting-integers-to-floating-point-values"></a>정수를 부동 소수점 값으로 캐스팅
**ANSI 3.2.1.3** 정수가 원래의 값을 정확하게 나타낼 수 없는 부동 소수점 숫자로 변환될 경우 잘라내기 방향입니다.  
  
 정수가 값을 정확히 나타낼 수 없는 부동 소수점 값으로 캐스팅되면 알맞은 근사값으로 값이 반올림되거나 반내림됩니다.  
  
 예를 들어, **unsigned long**(전체 자릿수가 32비트)을 **float**(가수의 전체 자릿수가 23비트)로 캐스팅하면 가장 근사한 256의 배수로 반올림됩니다. 4,294,966,913에서 4,294,967,167까지의 **long** 값이 모두 **float** 값 4,294,967,040으로 반올림됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [부동 소수점의 수학](../c-language/floating-point-math.md)