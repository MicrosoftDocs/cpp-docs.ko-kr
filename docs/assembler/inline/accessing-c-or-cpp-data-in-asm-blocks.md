---
title: C 또는 __asm 블록에서 c + + 데이터 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9631db3c09c19e38791a6c909be02acd1c91601b
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2018
---
# <a name="accessing-c-or-c-data-in-asm-blocks"></a>__asm 블록에서 C 또는 C++ 데이터 액세스
## <a name="microsoft-specific"></a>Microsoft 전용  
 인라인 어셈블리를 사용하면 C 또는 C++ 변수를 이름으로 참조할 수 있으므로 매우 편리합니다. `__asm` 블록은 블록이 나타나는 범위에 있는 변수 이름을 비롯한 모든 기호를 참조할 수 있습니다. 예를 들어 C 변수 `var`이 범위에 있는 경우 다음 명령은  
  
```  
__asm mov eax, var  
```  
  
 `var`의 값을 EAX에 저장합니다.  
  
 클래스, 구조체 또는 공용 구조체 멤버에는 고유한 이름이 있는 경우는 `__asm` 변수를 지정 하지 않고 멤버 이름만 사용 하 여 참조할 수 있습니다 또는 `typedef` 점 앞에 오는 이름이 (**.**) 연산자. 그러나 멤버 이름이 고유하지 않은 경우에는 마침표 연산자 바로 앞에 변수 또는 `typedef` 이름을 배치해야 합니다. 예를 들어 다음 샘플의 구조체 형식은 `same_name`을 멤버 이름으로 공유합니다.  
  
 다음 형식으로 변수를 선언하는 경우  
  
```  
struct first_type hal;  
struct second_type oat;  
```  
  
 `same_name`이 고유하지 않기 때문에 `same_name` 멤버에 대한 모든 참조는 변수 이름을 사용해야 합니다. 그러나 `weasel` 멤버에는 고유한 이름이 있으므로 멤버 이름만 사용하여 참조할 수 있습니다.  
  
```  
// InlineAssembler_Accessing_C_asm_Blocks.cpp  
// processor: x86  
#include <stdio.h>  
struct first_type  
{  
   char *weasel;  
   int same_name;  
};  
  
struct second_type  
{  
   int wonton;  
   long same_name;  
};  
  
int main()  
{  
   struct first_type hal;  
   struct second_type oat;  
  
   __asm  
   {  
      lea ebx, hal  
      mov ecx, [ebx]hal.same_name ; Must use 'hal'  
      mov esi, [ebx].weasel       ; Can omit 'hal'  
   }  
   return 0;  
}  
```  
  
 단순히 코딩 편의를 위해 변수 이름을 생략하는 것 입니다. 변수 이름이 있는지 여부에 관계없이 동일한 어셈블리 명령이 생성됩니다.  
  
 액세스 제한에 관계없이 C++의 데이터 멤버에 액세스할 수 있습니다. 하지만 멤버 함수를 호출할 수는 없습니다.  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [__asm 블록에서 C 또는 C++ 사용](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)