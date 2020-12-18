---
description: '자세한 정보: 프롤로그/에필로그 코드를 작성할 때 고려 사항'
title: 프롤로그-에필로그 코드를 작성할 때 고려 사항
ms.date: 11/04/2016
helpviewer_keywords:
- layouts, stack frame
- stack frame layout
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: 3b8addec-e809-48e4-b1d0-5bad133bd4b8
ms.openlocfilehash: 65416e915afa95a27658e2c7517da8f2868dfef9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293289"
---
# <a name="considerations-when-writing-prologepilog-code"></a>프롤로그/에필로그 코드를 작성할 때 고려 사항

**Microsoft 전용**

자신의 prolog 및 epilog 코드 시퀀스를 작성하기 전에 스택 프레임을 배치하는 방법을 이해하는 것이 중요합니다. **__LOCAL_SIZE** 의 미리 정의된 상수를 사용하는 방법을 알아두는 것도 좋습니다.

## <a name="cstack-frame-layout"></a><a name="_clang_c_stack_frame_layout"></a> C 스택 프레임 레이아웃

이 예제에서는 32비트 함수에 표시될 수 있는 표준 prolog 코드를 보여 줍니다.

```
push     ebp                 ; Save ebp
mov      ebp, esp            ; Set stack frame pointer
sub      esp, localbytes     ; Allocate space for locals
push     <registers>         ; Save registers
```

`localbytes` 변수는 지역 변수를 위한 스택에 필요한 바이트 수를 나타내고, `registers` 변수는 스택에 저장될 레지스터의 목록을 나타내는 자리 표시자입니다. 레지스터를 푸시한 후 스택에 다른 적절한 데이터를 배치할 수 있습니다. 다음은 해당 epilog 코드입니다.

```
pop      <registers>         ; Restore registers
mov      esp, ebp            ; Restore stack pointer
pop      ebp                 ; Restore ebp
ret                          ; Return from function
```

스택은 항상 높은 메모리 주소에서 낮은 메모리 주소로 감소합니다. 기본 포인터(`ebp`)는 `ebp`의 푸시된 값을 가리킵니다. 지역 변수 영역은 `ebp-2`에서 시작됩니다. 지역 변수에 액세스하려면 `ebp`에서 적절한 값을 빼는 방법으로 `ebp`에서 오프셋을 계산합니다.

## <a name="the-__local_size-constant"></a><a name="_clang_the___local_size_constant"></a> __LOCAL_SIZE 상수

컴파일러는 함수 prolog 코드의 인라인 어셈블러 블록에서 사용할 **__LOCAL_SIZE** 상수를 제공합니다. 이 상수는 사용자 지정 prolog 코드의 스택 프레임에 대한 지역 변수의 공간을 할당하는 데 사용됩니다.

컴파일러는 **__LOCAL_SIZE** 의 값을 결정합니다. 값은 모든 사용자 정의 지역 변수 및 컴파일러 생성 임시 변수의 총 바이트 수입니다. **__LOCAL_SIZE** 는 즉시 피연산자로만 사용할 수 있으며 식에서는 사용할 수 없습니다. 이 상수의 값을 변경하거나 다시 정의해서는 안 됩니다. 예를 들어:

```
mov      eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov      eax, [ebp - __LOCAL_SIZE]   ;Error
```

다음 예제에서는 사용자 지정 prolog 및 epilog 시퀀스를 포함하는 다음 naked 함수가 prolog 시퀀스에서 **__LOCAL_SIZE** 를 사용한다는 방식을 보여 줍니다.

```
__declspec ( naked ) func()
{
   int i;
   int j;

   __asm      /* prolog */
      {
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */

   __asm      /* epilog */
      {
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[Naked 함수](../c-language/naked-functions.md)
