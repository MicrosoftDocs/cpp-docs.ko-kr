---
description: '자세히 알아보기: __asm 블록에서 C 또는 c + + 데이터 액세스'
title: __asm 블록에서 C 또는 C++ 데이터 액세스
ms.date: 08/30/2018
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
ms.openlocfilehash: b24d25b5687dd309c400b17c1e0eb6b35ef986f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118084"
---
# <a name="accessing-c-or-c-data-in-__asm-blocks"></a>__asm 블록에서 C 또는 C++ 데이터 액세스

**Microsoft 전용**

인라인 어셈블리를 사용하면 C 또는 C++ 변수를 이름으로 참조할 수 있으므로 매우 편리합니다. 블록 **`__asm`** 은 블록을 표시 하는 범위 내에 있는 모든 기호 (변수 이름 포함)를 참조할 수 있습니다. 예를 들어 C 변수 `var`이 범위에 있는 경우 다음 명령은

```cpp
__asm mov eax, var
```

`var`의 값을 EAX에 저장합니다.

클래스, 구조체 또는 공용 구조체 멤버에 고유한 이름이 있는 경우 **`__asm`** 블록은 **`typedef`** 마침표 (**.**) 연산자 앞에 변수나 이름을 지정 하지 않고 멤버 이름만 사용 하 여이를 참조할 수 있습니다. 그러나 멤버 이름이 고유 하지 않은 경우에는 **`typedef`** 마침표 연산자 바로 앞에 변수 또는 이름을 입력 해야 합니다. 예를 들어 다음 샘플의 구조체 형식은 `same_name`을 멤버 이름으로 공유합니다.

다음 형식으로 변수를 선언하는 경우

```cpp
struct first_type hal;
struct second_type oat;
```

`same_name`이 고유하지 않기 때문에 `same_name` 멤버에 대한 모든 참조는 변수 이름을 사용해야 합니다. 그러나 `weasel` 멤버에는 고유한 이름이 있으므로 멤버 이름만 사용하여 참조할 수 있습니다.

```cpp
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

## <a name="see-also"></a>참조

[__Asm 블록에서 C 또는 c + + 사용](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
