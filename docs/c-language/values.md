---
title: "값 | Microsoft Docs"
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
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ea979083fb00d57e455b97c2f6b94f7ea7c6b596
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="values"></a>값
**ANSI 3.1.2.5** 다양한 형식의 부동 소수점 숫자의 값에 대한 표현 및 집합  
  
 **float** 형식에는 32비트(부호１비트, 지수 ８비트, 가수 23비트)가 포함됩니다. 범위는 +/- 3.4E38이고 전체 자릿수는 7자리 이상입니다.  
  
 **double** 형식에는 64비트(부호 1비트, 지수 11비트, 가수 52비트)가 포함됩니다. 범위는 +/- 1.7E308이고 전체 자릿수는 15자리 이상입니다.  
  
 **long double** 형식에는 80비트(부호 1비트, 지수 15비트, 가수 64비트)가 포함됩니다. 범위는 +/- 1.2E4932이고 전체 자릿수는 19자리 이상입니다. Microsoft C 컴파일러를 사용하는 경우 **long double** 형식의 표현은 **double** 형식과 동일합니다.  
  
## <a name="see-also"></a>참고 항목  
 [부동 소수점의 수학](../c-language/floating-point-math.md)