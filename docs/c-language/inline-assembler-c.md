---
description: '자세한 정보: 인라인 어셈블러 (C)'
title: 인라인 어셈블러 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- __asm keyword [C]
- inline assembler [C]
ms.assetid: 821acc77-60b1-434c-ba54-2ba930a25ab4
ms.openlocfilehash: 8c5dc8ecc713968786b05eca6ab38e4752ea48c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181854"
---
# <a name="inline-assembler-c"></a>인라인 어셈블러 (C)

**Microsoft 전용**

인라인 어셈블러를 사용하면 추가 어셈블리 및 링크 단계를 수행하지 않고 C 소스 프로그램에 직접 어셈블리 언어 명령을 포함할 수 있습니다. 컴파일러에 인라인 어셈블러가 기본 제공되므로 MASM(Microsoft Macro Assembler)과 같은 별도의 어셈블러가 필요 없습니다.

인라인 어셈블러에는 별도의 어셈블리 및 링크 단계가 필요 없으므로 별도의 어셈블리보다 편리합니다. 범위에 속한 C 변수 또는 함수 이름을 인라인 어셈블리 코드에 사용할 수 있으므로 인라인 어셈블리 코드를 프로그램의 C 코드와 쉽게 통합할 수 있습니다. 또한 어셈블리 코드를 C 문과 함께 사용할 수 있으므로 C에서 단독으로 수행하기 어렵거나 불가능한 작업이 가능해집니다.

**`__asm`** 키워드는 인라인 어셈블러를 호출하며 C 문을 사용할 수 있는 모든 곳에 나타날 수 있습니다. 이 키워드는 자체적으로 표시할 수 없습니다. 이 키워드 다음에는 어셈블리 명령, 중괄호로 묶은 명령 그룹 또는 최소한 빈 괄호의 쌍이 와야 합니다. 여기서 " **`__asm`** 블록" 항은 중괄호에 상관없이 명령 또는 명령 그룹을 참조합니다.

아래의 코드는 중괄호로 묶인 간단한 **`__asm`** 블록입니다. 이 코드는 사용자 지정 함수 프롤로그 시퀀스입니다.

```
__asm
{
   push ebp
   mov  ebp, esp
   sub  esp, __LOCAL_SIZE
}
```

또는 **`__asm`** 을 각 어셈블리 명령 앞에 배치할 수 있습니다.

```
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

**`__asm`** 키워드는 문 구분 기호이므로 같은 줄에 어셈블리 명령을 포함할 수 있습니다.

```
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[함수 특성](../c-language/function-attributes.md)
