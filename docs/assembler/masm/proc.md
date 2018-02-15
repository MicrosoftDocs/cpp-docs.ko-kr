---
title: PROC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- PROC
dev_langs:
- C++
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0900b277650fee1c4134d354d964d49d570c6266
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="proc"></a>PROC
호출 하는 프로시저 블록의 시작 및 끝 표시 *레이블*합니다. 블록의 문이 호출할 수는 **호출** 명령 또는 [INVOKE](../../assembler/masm/invoke.md) 지시문입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
   label PROC [[distance]] [[langtype]] [[visibility]] [[<prologuearg>]]   
[[USES reglist]] [[, parameter [[:tag]]]]...  
[FRAME [:ehandler-address] ]  
statements  
label ENDP  
```  
  
## <a name="remarks"></a>설명  
 [프레임 [:*ehandler 주소*]]는 에서만 ml64.exe, 사용할 및 MASM.pdata에서 함수 테이블 항목을 생성 하는 함수의 구조적에 대 한.xdata에서 정보를 해제 하면 예외 처리 동작을 해제 합니다.  
  
 경우는 **프레임** 특성을 사용 하 여 따라야 할는 [합니다. 프롤로그 끝](../../assembler/masm/dot-endprolog.md) 지시문입니다.  
  
 참조 [MASM (ml64.exe) x64](../../assembler/masm/masm-for-x64-ml64-exe.md) ml64.exe를 사용 하 여 대 한 자세한 내용은 합니다.  
  
## <a name="example"></a>예  
  
```  
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
  
 위의 코드는 다음 함수 표 내보내고 정보를 해제 됩니다.  
  
```  
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
 [지시문 참조](../../assembler/masm/directives-reference.md)