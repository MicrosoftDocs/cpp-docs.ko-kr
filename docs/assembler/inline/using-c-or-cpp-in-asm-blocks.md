---
description: '자세히 알아보기: __asm 블록에서 C 또는 c + + 사용'
title: __asm 블록에서 C 또는 C++ 사용
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembly, mixing instructions with C/C++ statements
- symbols, in __asm blocks
- macros, __asm blocks
- preprocessor directives, used in __asm blocks
- type names, used in __asm blocks
- preprocessor directives
- preprocessor, directives
- constants, in __asm blocks
- comments, in __asm blocks
- typedef names, used in __asm blocks
- __asm keyword [C++], C/C++ elements in
ms.assetid: ae8b2b52-6b75-42e3-ac0c-ad02d922ed97
ms.openlocfilehash: 2fc1987339fcbabee07e2b626c3ae764c3d5e2e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97121929"
---
# <a name="using-c-or-c-in-__asm-blocks"></a>__asm 블록에서 C 또는 C++ 사용

**Microsoft 전용**

인라인 어셈블리 명령은 C 또는 C++ 문과 함께 사용할 수 있으므로 C 또는 C++ 변수를 이름으로 참조하고 이러한 언어의 다른 많은 요소를 사용할 수 있습니다.

**`__asm`** 블록은 다음과 같은 언어 요소를 사용할 수 있습니다.

- 레이블과 변수 및 함수 이름을 포함하는 기호

- 기호화 된 상수 및 멤버를 포함 하는 상수 **`enum`**

- 매크로 및 전처리기 지시문

- __/ \* 설명 \* ( /__ 및 __//__ )

- 형식 이름(MASM 형식이 올바를 때마다)

- **`typedef`** 일반적으로 **PTR** , **TYPE** 등의 연산자와 함께 사용 되거나 구조체 또는 공용 구조체 멤버를 지정 하기 위해 사용 되는 이름

블록 내에서 **`__asm`** C 표기법 또는 어셈블러 기 수 표기법을 사용 하 여 정수 상수를 지정할 수 있습니다 (예: 0x100 및 100h는 동일). 이를 통해 C에서 (`#define`을 사용하여) 상수를 정의한 다음 C 또는 C++ 모두와 프로그램의 어셈블리 부분에서 사용할 수 있습니다. a 0과 함께 이전 상수에 의해 8진수에서 상수를 지정할 수도 있습니다. 예를 들어, 0777은 8진수 상수를 지정합니다.

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [__Asm 블록에서 연산자 사용](../../assembler/inline/using-operators-in-asm-blocks.md)

- [__asm 블록에서 C 또는 C++ 기호 사용](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)

- [__Asm 블록에서 C 또는 c + + 데이터 액세스](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)

- [인라인 어셈블리를 사용 하 여 함수 작성](../../assembler/inline/writing-functions-with-inline-assembly.md)

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[인라인 어셈블러](../../assembler/inline/inline-assembler.md)<br/>
