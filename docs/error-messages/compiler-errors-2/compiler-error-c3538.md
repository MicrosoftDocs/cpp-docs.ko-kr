---
title: 컴파일러 오류 C3538 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3538
dev_langs:
- C++
helpviewer_keywords:
- C3538
ms.assetid: ef3698a5-7356-4c62-b9af-5d3a4baed958
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35f852e41ff86b9eed39da0aeb367d7049b8db4b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33262581"
---
# <a name="compiler-error-c3538"></a>컴파일러 오류 C3538
선언자 목록에서 'auto'는 항상 동일한 형식으로 추론되어야 합니다.  
  
 선언 목록에 선언된 모든 변수가 동일한 형식으로 확인되지 않습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
1.  목록에 있는 모든 `auto` 선언이 동일한 형식으로 추론되는지 확인합니다.  
  
## <a name="example"></a>예제  
 다음 문은 3538 오류를 생성합니다. 각 문에서 여러 변수를 선언하지만 각각의 `auto` 키워드 사용이 동일한 형식으로 추론되지 않습니다.  
  
```  
// C3538.cpp  
// Compile with /Zc:auto  
// C3538 expected  
int main()  
{  
// Variable x1 is a pointer to char, but y1 is a double.  
   auto * x1 = "a", y1 = 3.14;    
// Variable c is a char and c1 is char*, but c2, and c3 are pointers to pointers.  
   auto c = 'a', *c1 = &c, * c2 = &c1, * c3 = &c2;   
// Variable x2 is an int, but y2 is a double and z is a char.  
   auto x2(1), y2(0.0), z = 'a';   
// Variable a is a pointer to int, but b is a pointer to double.  
   auto *a = new auto(1), *b = new auto(2.0);   
   return 0;  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [auto 키워드](../../cpp/auto-keyword.md)