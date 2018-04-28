---
title: 인라인 어셈블리로 함수 작성 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], inline assembly
- inline assembly [C++], writing functions
- assembler [C++], writing functions
- __asm keyword [C++], in functions
ms.assetid: b5df8a04-fdc7-4622-8c9e-e4b618927497
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6c6c5b064dfc7d156d4de424e1ab69d74140f90
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2018
---
# <a name="writing-functions-with-inline-assembly"></a>인라인 어셈블리로 함수 작성
## <a name="microsoft-specific"></a>Microsoft 전용  
 인라인 어셈블리 코드를 사용하여 함수를 작성하는 경우 간편하게 인수를 함수에 전달하고 값을 반환할 수 있습니다. 다음 예제에서는 별도의 어셈블러에 대해 먼저 작성된 후 인라인 어셈블러에 대해 다시 작성된 함수를 비교합니다. 호출된 `power2` 함수가 매개 변수 2개를 수신하고 첫 번째 매개 변수에 2를 곱하여 두 번째 매개 변수의 거듭제곱을 구합니다. 별로의 어셈블러에 대해 작성된 함수는 다음과 같습니다.  
  
```  
; POWER.ASM  
; Compute the power of an integer  
;  
       PUBLIC _power2  
_TEXT SEGMENT WORD PUBLIC 'CODE'  
_power2 PROC  
  
        push ebp        ; Save EBP  
        mov ebp, esp    ; Move ESP into EBP so we can refer  
                        ;   to arguments on the stack  
        mov eax, [ebp+4] ; Get first argument  
        mov ecx, [ebp+6] ; Get second argument  
        shl eax, cl     ; EAX = EAX * ( 2 ^ CL )  
        pop ebp         ; Restore EBP  
        ret             ; Return with sum in EAX  
  
_power2 ENDP  
_TEXT   ENDS  
        END  
```  
  
 별도의 어셈블러에 대해 작성했으므로 이 함수에는 별도의 소스 파일과 어셈블리 및 링크 단계가 필요합니다. C 및 C++ 함수 인수는 대개 스택에서 전달되므로 이 버전의 `power2` 함수는 스택의 위치를 기준으로 인수에 액세스합니다. (유의 **모델** 지시문을 MASM과 몇몇 다른 어셈블러에서 사용할 수 있는 또한 이름으로 스택 인수와 로컬 스택 변수에 액세스할 수 있습니다.)  
  
## <a name="example"></a>예제  
 이 프로그램은 인라인 어셈블리 코드를 사용하여 `power2` 함수를 작성합니다.  
  
```  
// Power2_inline_asm.c  
// compile with: /EHsc  
// processor: x86  
  
#include <stdio.h>  
  
int power2( int num, int power );  
  
int main( void )  
{  
    printf_s( "3 times 2 to the power of 5 is %d\n", \  
              power2( 3, 5) );  
}  
int power2( int num, int power )  
{  
   __asm  
   {  
      mov eax, num    ; Get first argument  
      mov ecx, power  ; Get second argument  
      shl eax, cl     ; EAX = EAX * ( 2 to the power of CL )  
   }  
   // Return with result in EAX  
}  
```  
  
 인라인 버전의 `power2` 함수는 이름으로 인수를 참조하며 프로그램의 나머지 부분과 동일한 소스 파일에 나타납니다. 또한 이 버전에는 더 적은 어셈블리 명령이 필요합니다.  
  
 인라인 버전의 `power2`가 C `return` 문을 실행하지 않으므로 경고 수준 2 이상에서 컴파일할 경우 해롭지 않은 경고가 발생합니다. 함수가 값을 반환하지만 `return` 문이 없을 경우 컴파일러가 그 사실을 알릴 수 없습니다. 사용할 수 있습니다 [#pragma 경고](../../preprocessor/warning.md) 이 경고의 생성을 해제 하려면.  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [__asm 블록에서 C 또는 C++ 사용](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)