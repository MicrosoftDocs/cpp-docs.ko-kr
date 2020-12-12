---
description: '자세한 정보: __asm 블록에서 연산자 사용'
title: __asm 블록에서 연산자 사용
ms.date: 08/30/2018
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
ms.openlocfilehash: 266d840e6cb407d45c1d3a49bed6a2390e52aa2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97121851"
---
# <a name="using-operators-in-__asm-blocks"></a>__asm 블록에서 연산자 사용

**Microsoft 전용**

**`__asm`** 블록은 연산자와 같은 c 또는 c + + 관련 연산자를 사용할 수 없습니다 **<<** . 그러나 연산자와 같이 C 및 MASM에서 공유 하는 연산자 \* 는 어셈블리 언어 연산자로 해석 됩니다. 예를 들어 블록 외부에서 **`__asm`** 대괄호 (**[]**)는 바깥쪽 배열 첨자로 해석 됩니다 .이 경우 C는 배열의 요소 크기에 맞게 자동으로 조정 됩니다. 블록 안에는 **`__asm`** MASM 인덱스 연산자로 표시 됩니다 .이 연산자는 배열 뿐만 아니라 모든 데이터 개체 또는 레이블에서 크기를 조정 하는 바이트 오프셋을 생성 합니다. 다음 코드에서는 차이점을 보여 줍니다.

```cpp
int array[10];

__asm mov array[6], bx ;  Store BX at array+6 (not scaled)

array[6] = 0;         /* Store 0 at array+24 (scaled) */
```

`array`에 대한 첫 번째 참조는 크기가 조정되지 않지만 두 번째 참조는 크기가 조정됩니다. **형식** 연산자를 사용 하 여 상수를 기반으로 크기를 조정할 수 있습니다. 예를 들어 다음 두 개의 문은 동일합니다.

```cpp
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24

array[6] = 0;                   /* Store 0 at array + 24 */
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__Asm 블록에서 C 또는 c + + 사용](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
