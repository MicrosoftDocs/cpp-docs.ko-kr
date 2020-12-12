---
description: '자세히 알아보기: 인라인 어셈블리에서 레이블로 이동'
title: 인라인 어셈블리에서 레이블로 점프
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembly, jumping to labels
- labels, in inline assembly
- __asm keyword [C++], labels
- case sensitivity, labels in inline assembly
- labels, in __asm blocks
- jumping to labels in inline assembly
ms.assetid: 36c18b97-8981-4631-9dfd-af6c14a04297
ms.openlocfilehash: b4a32dd9baace77245f612d68b58f954a81075ab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117720"
---
# <a name="jumping-to-labels-in-inline-assembly"></a>인라인 어셈블리에서 레이블로 점프

**Microsoft 전용**

일반적인 C 또는 c + + 레이블과 마찬가지로 블록의 레이블은 **`__asm`** 블록이 아니라 정의 된 함수 전체에서 범위를 가집니다. 어셈블리 명령 및 **`goto`** 문은 모두 블록 내부 또는 외부의 레이블로 이동할 수 있습니다 **`__asm`** .

블록에 정의 된 레이블은 **`__asm`** 대/소문자를 구분 하지 않습니다. **`goto`** 문과 어셈블리 명령은 모두 대/소문자에 관계 없이 이러한 레이블을 참조할 수 있습니다. C 및 c + + 레이블은 문에서 사용 하는 경우에만 대/소문자를 구분 **`goto`** 합니다. 어셈블리 명령은 대/소문자에 관계없이 C 또는 C++ 레이블로 이동할 수 있습니다.

다음 코드에는 모든 순열이 나와 있습니다.

```cpp
void func( void )
{
   goto C_Dest;  /* Legal: correct case   */
   goto c_dest;  /* Error: incorrect case */

   goto A_Dest;  /* Legal: correct case   */
   goto a_dest;  /* Legal: incorrect case */

   __asm
   {
      jmp C_Dest ; Legal: correct case
      jmp c_dest ; Legal: incorrect case

      jmp A_Dest ; Legal: correct case
      jmp a_dest ; Legal: incorrect case

      a_dest:    ; __asm label
   }

   C_Dest:       /* C label */
   return;
}
int main()
{
}
```

C 라이브러리 함수 이름을 블록에서 레이블로 사용 하지 마세요 **`__asm`** . 예를 들어 `exit`를 다음과 같이 레이블로 사용하려 할 경우,

```cpp
; BAD TECHNIQUE: using library function name as label
   jne exit
   .
   .
   .
exit:
   ; More __asm code follows
```

**Exit** 는 C 라이브러리 함수의 이름이 기 때문에이 코드로 인해 원하는 위치가 아닌 **종료** 함수로 이동할 수 있습니다.

MASM 프로그램에서 달러 기호(`$`)는 현재 위치 카운터의 역할을 합니다. 이는 현재 어셈블리 되고 있는 명령에 대한 레이블로서 **`__asm`** 블록의 주요 용도는 긴 조건부 점프를 만드는 것입니다.

```cpp
   jne $+5 ; next instruction is 5 bytes long
   jmp farlabel ; $+5
   .
   .
   .
farlabel:
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[인라인 어셈블러](../../assembler/inline/inline-assembler.md)<br/>
