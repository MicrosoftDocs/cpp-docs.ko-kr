---
description: '자세한 정보: 지시문 참조'
title: 지시문 참조
ms.date: 07/15/2020
f1_keywords:
- Directives Reference
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), directives reference
ms.assetid: da6efcd1-18f7-41de-81cd-a002a02f9a22
ms.openlocfilehash: 5f4e4a75ce37b0d393bbc6a2a8fd45d16247dcff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132590"
---
# <a name="directives-reference"></a>지시문 참조

## <a name="x64"></a>X64

:::row:::
   :::column span="":::
      [`.ALLOCSTACK`](dot-allocstack.md)\
      [`.ENDPROLOG`](dot-endprolog.md)\
      [`PROC`](proc.md)
   :::column-end:::
   :::column span="":::
      [`.PUSHFRAME`](dot-pushframe.md)\
      [`.PUSHREG`](dot-pushreg.md)\
      [`.SAVEREG`](dot-savereg.md)
   :::column-end:::
   :::column span="":::
      [`.SAVEXMM128`](dot-savexmm128.md)\
      [`.SETFRAME`](dot-setframe.md)
   :::column-end:::
:::row-end:::

## <a name="code-labels"></a>코드 레이블

:::row:::
   :::column span="":::
      [`ALIGN`](align-masm.md)\
      [`EVEN`](even.md)
   :::column-end:::
   :::column span="":::
      [`LABEL`](label-masm.md)
   :::column-end:::
   :::column span="":::
      [`ORG`](org.md)
   :::column-end:::
:::row-end:::

## <a name="conditional-assembly"></a>조건부 어셈블리

:::row:::
   :::column span="":::
      [`ELSE`](else-masm.md)\
      [`ELSEIF`](elseif-masm.md)\
      [`ELSEIF2`](elseif2.md)\
      [`IF`](if-masm.md)\
      [`IF2`](if2.md)
   :::column-end:::
   :::column span="":::
      [`IFB`](ifb.md)\
      [`IFNB`](ifnb.md)\
      [`IFDEF`](ifdef.md)\
      [`IFNDEF`](ifndef.md)\
      [`IFDIF`](ifdif.md)
   :::column-end:::
   :::column span="":::
      [`IFDIFI`](ifdif.md)\
      [`IFE`](ife.md)\
      [`IFIDN`](ifidn.md)\
      [`IFIDNI`](ifidn.md)
   :::column-end:::
:::row-end:::

## <a name="conditional-control-flow"></a>조건부 제어 흐름

:::row:::
   :::column span="":::
      [`.BREAK`](dot-break.md)\
      [`.CONTINUE`](dot-continue.md)\
      [`.ELSE`](dot-else.md)\
      [`.ELSEIF`](dot-if.md)
   :::column-end:::
   :::column span="":::
      [`.ENDIF`](dot-endif.md)\
      [`.ENDW`](dot-endw.md)\
      [`.IF`](dot-if.md)\
      [`.REPEAT`](dot-repeat.md)
   :::column-end:::
   :::column span="":::
      [`.UNTIL`](dot-until.md)\
      [`.UNTILCXZ`](dot-untilcxz.md)\
      [`.WHILE`](dot-while.md)
   :::column-end:::
:::row-end:::

## <a name="conditional-error"></a>조건부 오류

:::row:::
   :::column span="":::
      [`.ERR`](dot-err.md)\
      [`.ERR2`](dot-err2.md)\
      [`.ERRB`](dot-errb.md)\
      [`.ERRDEF`](dot-errdef.md)
   :::column-end:::
   :::column span="":::
      [`.ERRDIF`](dot-errdif.md)\
      [`.ERRDIFI`](dot-errdif.md)\
      [`.ERRE`](dot-erre.md)\
      [`.ERRIDN`](dot-erridn.md)
   :::column-end:::
   :::column span="":::
      [`.ERRIDNI`](dot-erridn.md)\
      [`.ERRNB`](dot-errnb.md)\
      [`.ERRNDEF`](dot-errndef.md)\
      [`.ERRNZ`](dot-errnz.md)
   :::column-end:::
:::row-end:::

## <a name="data-allocation"></a>데이터 할당

:::row:::
   :::column span="":::
      [`ALIGN`](align-masm.md)\
      [`BYTE`](byte-masm.md)\
      [`SBYTE`](sbyte-masm.md)\
      [`DWORD`](dword.md)\
      [`SDWORD`](sdword.md)\
      [`EVEN`](even.md)
   :::column-end:::
   :::column span="":::
      [`FWORD`](fword.md)\
      [`LABEL`](label-masm.md)\
      [`ORG`](org.md)\
      [`QWORD`](qword.md)\
      [`REAL4`](real4.md)
   :::column-end:::
   :::column span="":::
      [`REAL8`](real8.md)\
      [`REAL10`](real10.md)\
      [`TBYTE`](tbyte.md)\
      [`WORD`](word.md)\
      [`SWORD`](sword.md)
   :::column-end:::
:::row-end:::

## <a name="equates"></a>매월

:::row:::
   :::column span="":::
      [`=`](equal.md)
   :::column-end:::
   :::column span="":::
      [`EQU`](equ.md)
   :::column-end:::
   :::column span="":::
      [`TEXTEQU`](textequ.md)
   :::column-end:::
:::row-end:::

## <a name="listing-control"></a>목록 컨트롤

:::row:::
   :::column span="":::
      [`.CREF`](dot-cref.md)\
      [`.LIST`](dot-list.md)\
      [`.LISTALL`](dot-listall.md)\
      [`.LISTIF`](dot-listif.md)\
      [`.LISTMACRO`](dot-listmacro.md)
   :::column-end:::
   :::column span="":::
      [`.LISTMACROALL`](dot-listmacroall.md)\
      [`.NOCREF`](dot-nocref.md)\
      [`.NOLIST`](dot-nolist.md)\
      [`.NOLISTIF`](dot-nolistif.md)\
      [`.NOLISTMACRO`](dot-nolistmacro.md)
   :::column-end:::
   :::column span="":::
      [`PAGE`](page.md)\
      [`SUBTITLE`](subtitle.md)\
      [`.TFCOND`](dot-tfcond.md)\
      [`TITLE`](title.md)
   :::column-end:::
:::row-end:::

## <a name="macros"></a>Macros

:::row:::
   :::column span="":::
      [`ENDM`](endm.md)\
      [`EXITM`](exitm.md)
   :::column-end:::
   :::column span="":::
      [`GOTO`](goto-masm.md)\
      [`LOCAL`](local-masm.md)
   :::column-end:::
   :::column span="":::
      [`MACRO`](macro.md)\
      [`PURGE`](purge.md)
   :::column-end:::
:::row-end:::

## <a name="miscellaneous"></a>기타

:::row:::
   :::column span="":::
      [`ALIAS`](alias-masm.md)\
      [`ASSUME`](assume.md)\
      [`COMMENT`](comment-masm.md)\
      [`ECHO`](echo.md)\
      [`END`](end-masm.md)\
      [`.FPO`](dot-fpo.md)
   :::column-end:::
   :::column span="":::
      [`INCLUDE`](include-masm.md)\
      [`INCLUDELIB`](includelib-masm.md)\
      [`MMWORD`](mmword.md)\
      [`OPTION`](option-masm.md)\
      [`POPCONTEXT`](popcontext.md)
   :::column-end:::
   :::column span="":::
      [`PUSHCONTEXT`](pushcontext.md)\
      [`.RADIX`](dot-radix.md)\
      [`.SAFESEH`](dot-safeseh.md)\
      [`XMMWORD`](xmmword.md)\
      [`YMMWORD`](ymmword.md)
   :::column-end:::
:::row-end:::

## <a name="procedures"></a>프로시저

:::row:::
   :::column span="":::
      [`ENDP`](endp.md)\
      [`INVOKE`](invoke.md)
   :::column-end:::
   :::column span="":::
      [`PROC`](proc.md)
   :::column-end:::
   :::column span="":::
      [`PROTO`](proto.md)
   :::column-end:::
:::row-end:::

## <a name="processor"></a>프로세서

:::row:::
   :::column span="":::
      [`.386`](dot-386.md)\
      [`.386P`](dot-386p.md)\
      [`.387`](dot-387.md)\
      [`.486`](dot-486.md)
   :::column-end:::
   :::column span="":::
      [`.486P`](dot-486p.md)\
      [`.586`](dot-586.md)\
      [`.586P`](dot-586p.md)\
      [`.686`](dot-686.md)
   :::column-end:::
   :::column span="":::
      [`.686P`](dot-686p.md)\
      [`.K3D`](dot-k3d.md)\
      [`.MMX`](dot-mmx.md)\
      [`.XMM`](dot-xmm.md)
   :::column-end:::
:::row-end:::

## <a name="repeat-blocks"></a>반복 블록

:::row:::
   :::column span="":::
      [`ENDM`](endm.md)\
      [`FOR`](for-masm.md)
   :::column-end:::
   :::column span="":::
      [`FORC`](forc.md)\
      [`GOTO`](goto-masm.md)
   :::column-end:::
   :::column span="":::
      [`REPEAT`](repeat.md)\
      [`WHILE`](while-masm.md)
   :::column-end:::
:::row-end:::

## <a name="scope"></a>범위

:::row:::
   :::column span="":::
      [`COMM`](comm.md)\
      [`EXTERN`](extern-masm.md)
   :::column-end:::
   :::column span="":::
      [`EXTERNDEF`](externdef.md)\
      [`INCLUDELIB`](includelib-masm.md)
   :::column-end:::
   :::column span="":::
      [`PUBLIC`](public-masm.md)
   :::column-end:::
:::row-end:::

## <a name="segment"></a>Segment

:::row:::
   :::column span="":::
      [`.ALPHA`](dot-alpha.md)\
      [`ASSUME`](assume.md)\
      [`.DOSSEG`](dot-dosseg.md)
   :::column-end:::
   :::column span="":::
      [`END`](end-masm.md)\
      [`ENDS`](ends-masm.md)\
      [`GROUP`](group.md)
   :::column-end:::
   :::column span="":::
      [`SEGMENT`](segment.md)\
      [`.SEQ`](dot-seq.md)
   :::column-end:::
:::row-end:::

## <a name="simplified-segment"></a>단순화 된 세그먼트

:::row:::
   :::column span="":::
      [`.CODE`](dot-code.md)\
      [`.CONST`](dot-const.md)\
      [`.DATA`](dot-data.md)\
      [`.DATA?`](dot-data-q.md)
   :::column-end:::
   :::column span="":::
      [`.DOSSEG`](dot-dosseg.md)\
      [`.EXIT`](dot-exit.md)\
      [`.FARDATA`](dot-fardata.md)\
      [`.FARDATA?`](dot-fardata-q.md)
   :::column-end:::
   :::column span="":::
      [`.MODEL`](dot-model.md)\
      [`.STACK`](dot-stack.md)\
      [`.STARTUP`](dot-startup.md)
   :::column-end:::
:::row-end:::

## <a name="string"></a>String

:::row:::
   :::column span="":::
      [`CATSTR`](catstr.md)\
      [`INSTR`](instr.md)
   :::column-end:::
   :::column span="":::
      [`SIZESTR`](sizestr.md)
   :::column-end:::
   :::column span="":::
      [`SUBSTR`](substr.md)
   :::column-end:::
:::row-end:::

## <a name="structure-and-record"></a>구조 및 레코드

:::row:::
   :::column span="":::
      [`ENDS`](ends-masm.md)\
      [`RECORD`](record-masm.md)
   :::column-end:::
   :::column span="":::
      [`STRUCT`](struct-masm.md)\
      [`TYPEDEF`](typedef-masm.md)
   :::column-end:::
   :::column span="":::
      [`UNION`](union.md)
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>참고 항목

[Microsoft 매크로 어셈블러 참조](microsoft-macro-assembler-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
