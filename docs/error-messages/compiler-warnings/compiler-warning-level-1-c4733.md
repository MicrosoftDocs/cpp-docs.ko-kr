---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4733'
title: 컴파일러 경고(수준 1) C4733
ms.date: 11/04/2016
f1_keywords:
- C4733
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
ms.openlocfilehash: e12e23830057404732aec641470cff5520818ef3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228627"
---
# <a name="compiler-warning-level-1-c4733"></a>컴파일러 경고(수준 1) C4733

인라인 asm이 ' FS: 0 '에 할당 되었습니다. 처리기가 안전 처리기로 등록 되지 않았습니다.

FS에서 값을 수정 하는 함수: 0 처리기가 유효한 예외 처리기로 등록 되지 않을 수 있기 때문에 새 예외 처리기를 추가 하는 것은 안전한 예외에서 작동 하지 않을 수 있습니다 ( [/safeseh](../../build/reference/safeseh-image-has-safe-exception-handlers.md)참조).

이 경고를 해결 하려면 FS를 제거 합니다. 정의 또는이 경고를 해제 하 고를 사용 [합니다. ](../../assembler/masm/dot-safeseh.md) 안전 하지 않은 예외 처리기를 지정 하기 위한 SAFESEH입니다.

다음 샘플에서는 C4733를 생성 합니다.

```cpp
// C4733.cpp
// compile with: /W1 /c
// processor: x86
#include "stdlib.h"
#include "stdio.h"
void my_handler()
{
   printf("Hello from my_handler\n");
   exit(1);
}

int main()
{
   _asm {
      push    my_handler
      mov     eax, DWORD PTR fs:0
      push    eax
      mov     DWORD PTR fs:0, esp   // C4733
   }

   *(int*)0 = 0;
}
```
