---
description: 에 대해 자세히 알아보세요. ALLOCSTACK
title: .ALLOCSTACK
ms.date: 12/17/2019
f1_keywords:
- .ALLOCSTACK
helpviewer_keywords:
- .ALLOCSTACK directive
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
ms.openlocfilehash: 6075b0900df104ae5faeaaff1dc0de2d3727b437
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132368"
---
# <a name="allocstack"></a>.ALLOCSTACK

프롤로그에서 현재 오프셋의 지정 된 크기를 사용 하 여 **UWOP_ALLOC_SMALL** 또는 **UWOP_ALLOC_LARGE** 을 생성 합니다.

## <a name="syntax"></a>Syntax

> **. ALLOCSTACK** *크기*

## <a name="remarks"></a>설명

MASM은 지정 된 크기에 대해 가장 효율적인 인코딩을 선택 합니다.

**. ALLOCSTACK** 을 사용 하면 ml64.exe 사용자는 프레임 함수를 해제 하는 방법을 지정 하 고, 프롤로그 내 에서만 허용 되는 방법을 지정할 수 있습니다 .이는 [프로시저](proc.md) 프레임 선언에서로 확장 됩니다 [. ENDPROLOG](dot-endprolog.md) 지시문입니다. 이러한 지시문은 코드를 생성 하지 않습니다. 및만 생성 `.xdata` `.pdata` 합니다. **. ALLOCSTACK** 앞에는 해제할 작업을 실제로 구현 하는 명령이 있어야 합니다. 규약을 보장 하기 위해 매크로에서 해제할 해제 지시문과 코드를 모두 래핑하는 것이 좋습니다.

‘크기’ 피연산자는 8의 배수여야 합니다.

자세한 내용은 x [64 용 MASM (ml64.exe)](masm-for-x64-ml64-exe.md)을 참조 하세요.

## <a name="sample"></a>샘플

다음 샘플에서는 해제/예외 처리기를 지정 하는 방법을 보여 줍니다.

```asm
; ml64 ex3.asm /link /entry:Example1  /SUBSYSTEM:Console
text SEGMENT
PUBLIC Example3
PUBLIC Example3_UW
Example3_UW PROC NEAR
   ; exception/unwind handler body

   ret 0

Example3_UW ENDP

Example3 PROC FRAME : Example3_UW

   sub rsp, 16
.allocstack 16

.endprolog

   ; function body
    add rsp, 16
   ret 0

Example3 ENDP
text ENDS
END
```

## <a name="see-also"></a>참고 항목

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
