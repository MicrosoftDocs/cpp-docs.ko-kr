---
description: '자세한 정보: 프롤로그/에필로그 코드 작성 시 고려 사항'
title: Prolog-Epilog 코드 작성 시 고려 사항
ms.date: 11/04/2016
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
ms.openlocfilehash: 6deb6e9120c83992a7fe2529d0c9366b8e191056
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204773"
---
# <a name="considerations-for-writing-prologepilog-code"></a>프롤로그/에필로그 코드 작성 시 고려 사항

**Microsoft 전용**

사용자 고유의 프롤로그 및 에필로그 코드 시퀀스를 작성 하기 전에 스택 프레임을 배치 하는 방법을 이해 하는 것이 중요 합니다. 또한 기호를 사용 하는 방법을 알고 있으면 유용 `__LOCAL_SIZE` 합니다.

## <a name="stack-frame-layout"></a><a name="_pluslang_c.2b2b_.stack_frame_layout"></a> 스택 프레임 레이아웃

이 예제에서는 32비트 함수에 표시될 수 있는 표준 prolog 코드를 보여 줍니다.

```
push        ebp                ; Save ebp
mov         ebp, esp           ; Set stack frame pointer
sub         esp, localbytes    ; Allocate space for locals
push        <registers>        ; Save registers
```

`localbytes` 변수는 지역 변수를 위한 스택에 필요한 바이트 수를 나타내고, `<registers>` 변수는 스택에 저장될 레지스터의 목록을 나타내는 자리 표시자입니다. 레지스터를 푸시한 후 스택에 다른 적절한 데이터를 배치할 수 있습니다. 다음은 해당 epilog 코드입니다.

```
pop         <registers>   ; Restore registers
mov         esp, ebp      ; Restore stack pointer
pop         ebp           ; Restore ebp
ret                       ; Return from function
```

스택은 항상 높은 메모리 주소에서 낮은 메모리 주소로 감소합니다. 기본 포인터(`ebp`)는 `ebp`의 푸시된 값을 가리킵니다. 지역 변수 영역은 `ebp-4`에서 시작합니다. 지역 변수에 액세스하려면 `ebp`에서 적절한 값을 빼는 방법으로 `ebp`에서 오프셋을 계산합니다.

## <a name="__local_size"></a><a name="_pluslang___local_size"></a> __LOCAL_SIZE

컴파일러는 `__LOCAL_SIZE` 함수 프롤로그 코드의 인라인 어셈블러 블록에서 사용할 기호를 제공 합니다. 이 기호는 사용자 지정 프롤로그 코드에서 스택 프레임에 지역 변수를 위한 공간을 할당하는 데 사용됩니다.

컴파일러는의 값을 결정 합니다 `__LOCAL_SIZE` . 이 값은 모든 사용자 정의 지역 변수와 컴파일러에서 생성된 임시 변수의 총 바이트 수입니다. `__LOCAL_SIZE` 는 직접 피연산자로만 사용할 수 있습니다. 식에 사용할 수 없습니다. 이 기호의 값을 변경하거나 다시 정의하면 안 됩니다. 예를 들어:

```
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov        eax, [ebp - __LOCAL_SIZE]   ;Error
```

사용자 지정 프롤로그 및 에필로그 시퀀스를 포함 하는 naked 함수의 다음 예에서는 `__LOCAL_SIZE` 프롤로그 시퀀스에서 기호를 사용 합니다.

```cpp
// the__local_size_symbol.cpp
// processor: x86
__declspec ( naked ) int main() {
   int i;
   int j;

   __asm {      /* prolog */
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */
   __asm {   /* epilog */
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[Naked 함수 호출](../cpp/naked-function-calls.md)
