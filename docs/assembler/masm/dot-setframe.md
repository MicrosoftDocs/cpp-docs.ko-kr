---
description: 에 대해 자세히 알아보세요. .SETFRAME
title: .SETFRAME
ms.date: 12/17/2019
f1_keywords:
- .SETFRAME
helpviewer_keywords:
- .SETFRAME directive
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
ms.openlocfilehash: b3554da14344293f00c499bc3084e6ddfd93c2ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97131081"
---
# <a name="setframe"></a>.SETFRAME

지정 된 레지스터 (*reg*)와 오프셋 (*오프셋*)을 사용 하 여 해제 정보에서 프레임 레지스터 필드와 오프셋을 채웁니다. 오프셋은 16의 배수여야 하며 240보다 작거나 같아야 합니다. 이 지시문은 또한 `UWOP_SET_FPREG` 현재 프롤로그 오프셋을 사용 하 여 지정 된 레지스터에 대 한 해제 코드 항목을 생성 합니다.

## <a name="syntax"></a>Syntax

> **. SETFRAME** *reg*, *offset*

## <a name="remarks"></a>설명

**. SETFRAME** 을 사용 하면 ml64.exe 사용자는 프레임 함수를 해제 하는 방법을 지정할 수 있으며, 프롤로그 내 에서만 허용 되며, [프로시저](proc.md) 프레임 선언에서로 확장 됩니다 [. ENDPROLOG](dot-endprolog.md) 지시문입니다. 이러한 지시문은 코드를 생성 하지 않습니다. 및만 생성 `.xdata` `.pdata` 합니다. **. SETFRAME** 앞에는 해제할 작업을 실제로 구현 하는 지침이 있어야 합니다. 규약을 보장 하기 위해 매크로에서 해제할 해제 지시문과 코드를 모두 래핑하는 것이 좋습니다.

자세한 내용은 x [64 용 MASM (ml64.exe)](masm-for-x64-ml64-exe.md)을 참조 하세요.

## <a name="sample"></a>샘플

### <a name="description"></a>Description

다음 샘플에서는 프레임 포인터를 사용 하는 방법을 보여 줍니다.

### <a name="code"></a>코드

```asm
; ml64 frmex2.asm /link /entry:frmex2 /SUBSYSTEM:CONSOLE
_text SEGMENT
frmex2 PROC FRAME
   push rbp
.pushreg rbp
   sub rsp, 010h
.allocstack 010h
   mov rbp, rsp
.setframe rbp, 0
.endprolog
   ; modify the stack pointer outside of the prologue (similar to alloca)
   sub rsp, 060h

   ; we can unwind from the following AV because of the frame pointer
   mov rax, 0
   mov rax, [rax] ; AV!

   add rsp, 060h
   add rsp, 010h
   pop rbp
   ret
frmex2 ENDP
_text ENDS
END
```

## <a name="see-also"></a>참조

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
