---
title: 인라인 어셈블리에서 레지스터 사용 및 유지 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a5db1c9c4facd51b2886d93017ad87a0683b899
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2018
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>인라인 어셈블리에서 레지스터 사용 및 유지
## <a name="microsoft-specific"></a>Microsoft 전용  
 일반적으로 `__asm` 블록이 시작될 때 레지스터에 지정된 값이 있을 것으로 가정하면 안 됩니다. 레지스터 값은 여러 개별 `__asm` 블록에서 유지되도록 보장되지 않습니다. 인라인 코드 블록을 종료하고 다른 블록을 시작하는 경우 첫 번째 블록의 레지스터 값을 유지하기 위해 두 번째 블록에서 해당 레지스터에 의존할 수 없습니다. `__asm` 블록은 일반 제어 흐름에서 발생하는 레지스터 값을 상속합니다.  
  
 `__fastcall` 호출 규칙을 사용하는 경우 컴파일러는 스택 대신 레지스터의 함수 인수를 전달합니다. 함수에서는 어느 매개 변수가 어느 레지스터에 있는지 알 수 없기 때문에 이로 인해 `__asm` 블록을 사용하는 함수에서 문제가 발생할 수 있습니다. 함수에서 EAX의 매개 변수를 수신하고 EAX에 다른 항목을 즉시 저장하는 경우 원래 매개 변수가 손실됩니다. 또한 `__fastcall`을 사용하여 선언된 모든 함수에서 ECX 레지스터를 유지해야 합니다.  
  
 이러한 레지스터 충돌을 방지하려면 `__fastcall` 블록을 포함하는 함수에 대해 `__asm` 규칙을 사용하지 마십시오. /Gr 컴파일러 옵션을 사용하여 `__fastcall` 규칙을 전역적으로 지정하는 경우 `__asm` 또는 `__cdecl`을 사용하여 `__stdcall` 블록을 포함하는 모든 함수를 선언해야 합니다. `__cdecl` 특성은 해당 함수에 대해 C 호출 규칙을 사용하도록 컴파일러에 지시합니다. /Gr을 사용하여 컴파일하지 않을 경우 `__fastcall` 특성으로 함수를 선언하지 마십시오.  
  
 `__asm`을 사용하여 C/C++ 함수에서 어셈블리 언어를 작성하는 경우 EAX, EBX, ECX, EDX, ESI 또는 EDI 레지스터를 유지할 필요가 없습니다. 예를 들어 POWER2에. 예제에서는 C [인라인 어셈블리로 함수 작성](../../assembler/inline/writing-functions-with-inline-assembly.md), `power2` 함수는 EAX 레지스터에 값을 유지 하지 않습니다. 하지만 레지스터 할당자는 이러한 레지스터를 사용하여 여러 `__asm` 블록에서 값을 저장할 수 없으므로 이러한 레지스터를 사용하면 코드 품질에 영향을 미칩니다. 또한 인라인 어셈블리 코드에서 EBX, ESI 또는 EDI를 사용하면 컴파일러가 해당 레지스터를 함수 프롤로그 및 에필로그에 저장하고 복원하게 됩니다.  
  
 `__asm` 블록의 범위에 사용하는 다른 레지스터(DS, SS, SP, BP, 플래그 레지스터 등)를 유지해야 합니다. 스택 전환과 같이 변경해야 하는 이유가 없는 한 ESP 및 EBP 레지스터를 유지해야 합니다. 또한 참조 [인라인 어셈블리 최적화](../../assembler/inline/optimizing-inline-assembly.md)합니다.  
  
 일부 SSE 형식은 8바이트 스택 정렬이 필요로 하며 컴파일러가 동적 스택 정렬 코드를 내보내도록 합니다. 정렬 후 지역 변수와 함수 매개 변수 모두에 액세스할 수 있기 위해 컴파일러는 두 개의 프레임 포인터를 유지합니다.  프레임 포인터 생략 FPO ()를 수행 하는 컴파일러, ESP 및 EBP를 사용 합니다.  컴파일러는 FPO를 수행 하지 않으면, EBX 및 EBP를 사용 합니다. 코드가 올바르게 실행되도록 하려면 함수가 동적 스택 정렬을 필요로 하는 경우 프레임 포인터를 수정할 수 있으므로 asm 코드에서 EBX를 수정하지 마십시오. 8바이트로 정렬된 형식을 함수 밖으로 이동하거나, EBX를 사용하지 않아야 합니다.  
  
> [!NOTE]
>  인라인 어셈블리 코드가 STD 또는 CLD 명령을 사용하여 방향 플래그를 변경하는 경우 해당 플래그를 원래 값으로 복원해야 합니다.  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [인라인 어셈블러](../../assembler/inline/inline-assembler.md)