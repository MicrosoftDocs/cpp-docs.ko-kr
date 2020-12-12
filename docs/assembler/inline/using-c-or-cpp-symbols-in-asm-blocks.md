---
description: '자세히 알아보기: __asm 블록에서 C 또는 c + + 기호 사용'
title: __asm 블록에서 C 또는 C++ 기호 사용
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
ms.openlocfilehash: 3a2e46ab13bb316cb4761103d34da6c129c97995
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97121890"
---
# <a name="using-c-or-c-symbols-in-__asm-blocks"></a>__asm 블록에서 C 또는 C++ 기호 사용

**Microsoft 전용**

블록 **`__asm`** 은 블록이 표시 되는 범위에서 c 또는 c + + 기호를 참조할 수 있습니다. C 및 c + + 기호는 변수 이름, 함수 이름 및 레이블, 즉 기호화 된 상수 또는 멤버가 아닌 이름입니다 **`enum`** . C++ 멤버 함수는 호출할 수 없습니다.

C 및 C++ 기호를 사용할 때는 몇 가지 제한이 적용됩니다.

- 각 어셈블리 언어 문에는 C 또는 C++ 기호를 하나만 포함할 수 있습니다. 여러 기호는 동일한 어셈블리 명령에 **길이**, **형식** 및 **크기** 식 으로만 나타날 수 있습니다.

- 블록에서 참조 되는 함수 **`__asm`** 는 프로그램에서 앞서 선언 (프로토타입화 됨) 해야 합니다. 그렇지 않으면 컴파일러는 블록의 함수 이름과 레이블을 구분할 수 없습니다 **`__asm`** .

- **`__asm`** 블록은 대/소문자에 관계 없이 MASM 예약어와 동일한 철자를 사용 하는 모든 C 또는 c + + 기호를 사용할 수 없습니다. MASM 예약어에는 **이름 (예** : SI)과 같은 명령 이름이 포함 됩니다.

- 구조체 및 공용 구조체 태그는 블록에서 인식 되지 않습니다 **`__asm`** .

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__Asm 블록에서 C 또는 c + + 사용](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
