---
title: .PUSHREG
ms.date: 12/16/2019
f1_keywords:
- .PUSHREG
helpviewer_keywords:
- .PUSHREG directive
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
ms.openlocfilehash: de6ffd3668f47732144e8c632410f6dfde6b2f31
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318295"
---
# <a name="pushreg"></a>.PUSHREG

프롤로그의 현재 오프셋을 사용 하 여 지정 된 레지스터 번호에 대 한 `UWOP_PUSH_NONVOL` 해제 코드 항목을 생성 합니다.

## <a name="syntax"></a>구문

> . PUSHREG *등록*

## <a name="remarks"></a>주의

**. PUSHREG** 를 사용 하면 ml64.exe 사용자가 프레임 함수를 해제 하는 방법을 지정할 수 있으며, 프롤로그 내 에서만 허용 되며, [프로시저](proc.md) **프레임** 선언에서로 확장 됩니다 [. ENDPROLOG](dot-endprolog.md) 지시문입니다. 이러한 지시문은 코드를 생성 하지 않습니다. `.xdata` 및 `.pdata`생성 합니다. **. PUSHREG** 는 해제할 작업을 실제로 구현 하는 명령 앞에와 야 합니다. 규약을 보장 하기 위해 매크로에서 해제할 해제 지시문과 코드를 모두 래핑하는 것이 좋습니다.

*등록* 은 다음 중 하나일 수 있습니다.
RAX | RCX | RDX | RBX | RDI | RSI | RBP | R8 | R 9 | R10 | R 11 | R12 | R13 | R14 | R15.

자세한 내용은 [x 64 용 MASM (ml64.exe)](masm-for-x64-ml64-exe.md)을 참조 하세요.

## <a name="sample"></a>예제

### <a name="description"></a>설명

다음 샘플에서는 비휘발성 레지스터를 푸시하는 방법을 보여 줍니다.

### <a name="code"></a>코드

```asm
; ml64 ex1.asm /link /entry:Example1 /SUBSYSTEM:CONSOLE
_text SEGMENT
Example1 PROC FRAME
   push r10
.pushreg r10
   push r15
.pushreg r15
   push rbx
.pushreg rbx
   push rsi
.pushreg rsi
.endprolog
   ; rest of function ...
   ret
Example1 ENDP
_text ENDS
END
```

## <a name="see-also"></a>참조

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
