---
description: '자세한 정보: 인라인 어셈블러 개요'
title: 인라인 어셈블러 개요
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
ms.openlocfilehash: 7e6028e0187c1aeab338636d734425d1881fc740
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117785"
---
# <a name="inline-assembler-overview"></a>인라인 어셈블러 개요

**Microsoft 전용**

인라인 어셈블러를 사용하면 추가 어셈블리 및 링크 단계를 수행하지 않고 C 및 C++ 소스 프로그램에 어셈블리 언어 명령을 포함할 수 있습니다. 컴파일러에 인라인 어셈블러가 기본 제공되므로 MASM(Microsoft Macro Assembler)과 같은 별도의 어셈블러가 필요 없습니다.

인라인 어셈블러에는 별도의 어셈블리 및 링크 단계가 필요 없으므로 별도의 어셈블리보다 편리합니다. 인라인 어셈블리 코드는 범위에 있는 임의의 C/C++ 변수 또는 함수 이름을 사용할 수 있으므로 프로그램의 C 및 C++ 코드와 쉽게 통합될 수 있습니다. 어셈블리 코드는 C 및 C++ 문과 혼합될 수 있으므로 C 또는 C++만 사용하는 경우 다루기 어렵거나 불가능한 작업을 수행할 수 있습니다.

[__Asm](../../assembler/inline/asm.md) 키워드는 인라인 어셈블러를 호출 하 고 c 또는 c + + 문이 유효한 모든 곳에 나타날 수 있습니다. 이 키워드는 자체적으로 표시할 수 없습니다. 이 키워드 다음에는 어셈블리 명령, 중괄호로 묶은 명령 그룹 또는 최소한 빈 괄호의 쌍이 와야 합니다. 여기서 " **`__asm`** 블록" 항은 중괄호에 상관없이 명령 또는 명령 그룹을 참조합니다.

다음 코드는 **`__asm`** 중괄호로 묶인 간단한 블록입니다. 이 코드는 사용자 지정 함수 프롤로그 시퀀스입니다.

```cpp
// asm_overview.cpp
// processor: x86
void __declspec(naked) main()
{
    // Naked functions must provide their own prolog...
    __asm {
        push ebp
        mov ebp, esp
        sub esp, __LOCAL_SIZE
    }

    // ... and epilog
    __asm {
        pop ebp
        ret
    }
}
```

또는 **`__asm`** 을 각 어셈블리 명령 앞에 배치할 수 있습니다.

```cpp
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

**`__asm`** 키워드는 문 구분 기호이므로 같은 줄에 어셈블리 명령을 포함할 수 있습니다.

```cpp
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[인라인 어셈블러](../../assembler/inline/inline-assembler.md)<br/>
