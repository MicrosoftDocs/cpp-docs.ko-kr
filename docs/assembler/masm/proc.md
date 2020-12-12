---
description: '자세한 정보: PROC'
title: PROC
ms.date: 12/06/2019
f1_keywords:
- PROC
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
ms.openlocfilehash: fe811ed1723dc1a41014720d97b6f21ab596c2e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97126037"
---
# <a name="proc"></a>PROC

*레이블* 이라는 프로시저 블록의 시작과 끝을 표시 합니다. **호출** 명령 또는 [INVOKE](invoke.md) 지시문을 사용 하 여 블록의 문을 호출할 수 있습니다.

## <a name="syntax"></a>Syntax

> *label* **PROC** ⟦*distance**⟧ ⟦ ⟧* **⟦ ⟧**⟦ ⟧ ⟦ ⟧ ⟦ ⟦ ⟧  |    |   __\<__*prologuearg*__>__ __:__*tag*   ... ⟧\
> ⟦**FRAME** ⟦__:__*ehandler-address*⟧ ⟧ \
> *할당문*\
>  **endp** 레이블

## <a name="remarks"></a>설명

⟦*Distance*⟧*및 ⟦ ⟧* 인수는 32 비트 MASM 에서만 유효 합니다.

⟦**FRAME** ⟦__:__*ehandler-address*⟧ ⟧는 ml64.exe에만 사용할 수 있으며, 함수의 구조화 된 예외 처리 해제 동작에 대 한 .xdata의 .pdata 및 해제 정보에는 MASM에서 함수 테이블 항목을 생성 합니다.

**FRAME** 특성을 사용 하는 경우 뒤에가와 야 합니다 [. ENDPROLOG](dot-endprolog.md) 지시문입니다.

ml64.exe 사용에 대 한 자세한 내용은 x [64 용 MASM (ml64.exe)](masm-for-x64-ml64-exe.md) 을 참조 하세요.

## <a name="example"></a>예제

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

위의 코드는 다음 함수 테이블 및 해제 정보를 내보냅니다.

```Output
FileHeader->Machine 34404
Dumping Unwind Information for file ex2.exe

.pdata entry 1 0x00001000 0x00001023

  Unwind data: 0x00002000

    Unwind version: 1
    Unwind Flags: None
    Size of prologue: 0x08
    Count of codes: 3
    Frame register: rbp
    Frame offset: 0x0
    Unwind codes:

      Code offset: 0x08, SET_FPREG, register=rbp, offset=0x00
      Code offset: 0x05, ALLOC_SMALL, size=0x10
      Code offset: 0x01, PUSH_NONVOL, register=rbp
```

## <a name="see-also"></a>참고 항목

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
