---
title: C + +의 선언 위치 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e42f43e6187e19df6e9c1111c0e92aa4b9929199
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="point-of-declaration-in-c"></a>C++의 선언 지점
선언자 바로 뒤, 이니셜라이저 앞(선택 사항)에서 이름이 선언된다고 간주합니다. (선언 자에 대 한 자세한 내용은 참조 하십시오. [선언 및 정의](declarations-and-definitions-cpp.md).)  
  
 다음 예제를 고려해 보세요.  
  
```  
// point_of_declaration1.cpp  
// compile with: /W1   
double dVar = 7.0;  
int main()  
{  
   double dVar = dVar;   // C4700  
}  
```  
  
 선언 시점 되었으면 *후* 를 초기화 하는 다음의 로컬 `dVar` 7.0, 전역 변수의 값으로 초기화는 `dVar`합니다. 그러나 그런 경우는 아니므로 `dVar`이 정의되지 않은 값으로 초기화됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [범위](../cpp/scope-visual-cpp.md)