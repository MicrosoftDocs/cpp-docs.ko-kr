---
description: '자세히 알아보기: C 매크로로 __asm 블록 정의'
title: __asm 블록을 C 매크로로 정의
ms.date: 08/30/2018
helpviewer_keywords:
- macros, __asm blocks
- Visual C, macros
- __asm keyword [C++], as C macros
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
ms.openlocfilehash: a0fe13acdd5a75fd86fd8107396632a5c6e7c283
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117839"
---
# <a name="defining-__asm-blocks-as-c-macros"></a>__asm 블록을 C 매크로로 정의

**Microsoft 전용**

C 매크로를 사용하면 소스 코드에 어셈블리 코드를 편리하게 삽입할 수 있지만 매크로가 단일 논리 줄로 확장되기 때문에 사용 시 특별히 주의해야 합니다. 문제가 없는 매크로를 만들려면 다음 규칙을 따르십시오.

- 블록을 **`__asm`** 중괄호로 묶습니다.

- 키워드를 **`__asm`** 각 어셈블리 명령 앞에 배치 합니다.

- 어셈블리 스타일 주석(`/* comment */`) 또는 한 줄로 된 C 주석(`; comment`) 대신 이전 스타일 C 주석(`// comment`)을 사용합니다.

다음 예제에서는 간단한 매크로를 정의합니다.

```cpp
#define PORTIO __asm      \
/* Port output */         \
{                         \
   __asm mov al, 2        \
   __asm mov dx, 0xD007   \
   __asm out dx, al       \
}
```

처음에는 마지막 세 키워드가 불필요 한 것으로 **`__asm`** 보입니다. 그러나 매크로가 단일 줄로 확장되므로 세 키워드가 필요합니다.

```cpp
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }
```

세 번째 및 네 번째 **`__asm`** 키워드는 문 구분 기호로 필요 합니다. 블록에서 인식할 수 있는 유일한 문 구분 기호는 **`__asm`** 줄 바꿈 문자 및 **`__asm`** 키워드입니다. 매크로로 정의 된 블록은 하나의 논리 줄 이므로 각 명령을로 구분 해야 합니다 **`__asm`** .

중괄호도 필요합니다. 중괄호를 생략하면 동일한 줄의 매크로 호출 오른쪽에 있는 C 또는 C++ 문 때문에 컴파일러에 혼동이 있을 수 있습니다. 닫는 중괄호가 없으면 컴파일러는 어셈블리 코드가 중지 되는 위치를 알 수 없으며 블록 뒤에 있는 C 또는 c + + 문을 **`__asm`** 어셈블리 명령으로 인식 합니다.

세미콜론 (**;**)으로 시작 하는 어셈블리 스타일 주석은 줄의 끝까지 계속 됩니다. 컴파일러는 논리 줄의 끝까지 주석 이후의 모든 항목을 무시하므로 매크로에서 문제가 발생합니다. 한 줄로 된 C 또는 C++ 주석도 마찬가지입니다(`// comment`). 오류를 방지 하려면 `/* comment */` **`__asm`** 매크로로 정의 된 블록에 이전 스타일 C 주석 ()을 사용 합니다.

**`__asm`** C 매크로로 작성 된 블록은 인수를 사용할 수 있습니다. 그러나 일반 C 매크로와 달리 **`__asm`** 매크로는 값을 반환할 수 없습니다. 따라서 C 또는 C++ 식에 이러한 매크로를 사용할 수 없습니다.

이 형식의 매크로를 무차별적으로 호출하지 않도록 하십시오. 예를 들어 규칙으로 선언 된 함수에서 어셈블리 언어 매크로를 호출 하면 **`__fastcall`** 예기치 않은 결과가 발생할 수 있습니다. [인라인 어셈블리에서 레지스터 사용 및 유지](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)를 참조 하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[인라인 어셈블러](../../assembler/inline/inline-assembler.md)<br/>
