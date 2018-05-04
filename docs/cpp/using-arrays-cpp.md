---
title: 배열 (c + +)를 사용 하 여 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arrays [C++]
ms.assetid: 7818a7fe-7e82-4881-a3d1-7d25162b7fc7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c2140dbe786a5d2a2a1b86eca17912e5e06b922
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="using-arrays-c"></a>배열 사용 (C++)
배열 첨자 연산자(`[ ]`)를 사용하여 배열의 개별 요소에 액세스할 수 있습니다. 식에서 아래 첨자 없이 1차원 배열이 사용된 경우 배열 이름은 배열의 첫 번째 요소에 대한 포인터로 평가됩니다.  
  
```  
// using_arrays.cpp  
int main() {  
   char chArray[10];  
   char *pch = chArray;   // Evaluates to a pointer to the first element.  
   char   ch = chArray[0];   // Evaluates to the value of the first element.  
   ch = chArray[3];   // Evaluates to the value of the fourth element.  
}  
```  
  
 다차원 배열을 사용할 때 식에서 다양한 조합을 사용할 수 있습니다.  
  
```  
// using_arrays_2.cpp  
// compile with: /EHsc /W1  
#include <iostream>  
using namespace std;  
int main() {  
   double multi[4][4][3];   // Declare the array.  
   double (*p2multi)[3];  
   double (*p1multi);  
  
   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.  
   p2multi = multi[3];               // Make p2multi point to  
                                     // fourth "plane" of multi.  
   p1multi = multi[3][2];            // Make p1multi point to  
                                     // fourth plane, third row  
                                     // of multi.  
}  
```  
  
 위의 코드에서 `multi`는 `double` 형식의 3차원 배열입니다. `p2multi` 포인터는 크기가 3인 `double` 형식의 배열을 가리킵니다. 이 예제에서 배열은 한 개, 두 개 및 세 개의 아래 첨자와 함께 사용됩니다. `cout` 문에서처럼 모든 첨자를 지정하는 것이 더 일반적이기는 하지만 `cout` 문에서처럼 배열 요소의 특정 하위 집합을 선택하는 것이 유용할 때도 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [배열](../cpp/arrays-cpp.md)