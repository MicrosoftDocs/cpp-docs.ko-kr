---
description: '자세한 정보: 인라인 어셈블리에서 레지스터 사용 및 유지'
title: 인라인 어셈블리에서 레지스터 사용 및 유지
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
ms.openlocfilehash: 36758a313044190c9ee2f2a9b094325821d87635
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122007"
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>인라인 어셈블리에서 레지스터 사용 및 유지

**Microsoft 전용**

일반적으로 블록이 시작 될 때 레지스터에 지정 된 값이 있는 것으로 가정 하면 안 됩니다 **`__asm`** . 레지스터 값은 개별 블록에서 유지 되지 않을 수 있습니다 **`__asm`** . 인라인 코드 블록을 종료하고 다른 블록을 시작하는 경우 첫 번째 블록의 레지스터 값을 유지하기 위해 두 번째 블록에서 해당 레지스터에 의존할 수 없습니다. **`__asm`** 블록은 정상적인 제어 흐름에서 발생 하는 모든 레지스터 값을 상속 합니다.

호출 규칙을 사용 하는 경우 **`__fastcall`** 컴파일러는 스택에서 대신 함수 인수를 레지스터에 전달 합니다. 이로 **`__asm`** 인해 함수는 어떤 매개 변수가 어떤 레지스터에 있는지 알 수 없기 때문에 블록이 있는 함수에서 문제가 발생할 수 있습니다. 함수에서 EAX의 매개 변수를 수신하고 EAX에 다른 항목을 즉시 저장하는 경우 원래 매개 변수가 손실됩니다. 또한로 선언 된 함수에는 ECX 레지스터를 유지 해야 합니다 **`__fastcall`** .

이러한 레지스터 충돌을 방지 하기 위해 블록을 **`__fastcall`** 포함 하는 함수에는 규칙을 사용 하지 마세요 **`__asm`** . /Gr 컴파일러 옵션을 사용 하 여 전역으로 규칙을 지정 하는 경우 **`__fastcall`** 또는를 사용 하 여 블록을 포함 하는 모든 함수를 선언 **`__asm`** **`__cdecl`** **`__stdcall`** 합니다. 특성은 **`__cdecl`** 해당 함수에 대해 C 호출 규칙을 사용 하도록 컴파일러에 지시 합니다. /Gr로 컴파일하지 않는 경우에는 특성을 사용 하 여 함수를 선언 하지 마세요 **`__fastcall`** .

를 사용 하 여 **`__asm`** C/c + + 함수에서 어셈블리 언어를 작성할 때는 EAX, EBX, ECX, EDX, ESI 또는 EDI 레지스터를 보존할 필요가 없습니다. 예를 들어 POWER2에 있습니다. C [인라인 어셈블리를 사용 하는 함수를 작성](../../assembler/inline/writing-functions-with-inline-assembly.md)하는 예제에서 `power2` 함수는 EAX 레지스터의 값을 유지 하지 않습니다. 그러나 이러한 레지스터를 사용 하는 경우 레지스터 할당자는 블록 전체에 값을 저장 하는 데 사용할 수 없으므로 코드 품질에 영향을 줍니다 **`__asm`** . 또한 인라인 어셈블리 코드에서 EBX, ESI 또는 EDI를 사용하면 컴파일러가 해당 레지스터를 함수 프롤로그 및 에필로그에 저장하고 복원하게 됩니다.

블록 범위에 대해 사용 하는 다른 레지스터 (예: DS, SS, SP, BP 및 flags 레지스터)를 유지 해야 합니다 **`__asm`** . 스택 전환과 같이 변경해야 하는 이유가 없는 한 ESP 및 EBP 레지스터를 유지해야 합니다. [인라인 어셈블리 최적화](../../assembler/inline/optimizing-inline-assembly.md)도 참조 하세요.

일부 SSE 형식은 8바이트 스택 정렬이 필요로 하며 컴파일러가 동적 스택 정렬 코드를 내보내도록 합니다. 정렬 후 지역 변수와 함수 매개 변수 모두에 액세스할 수 있기 위해 컴파일러는 두 개의 프레임 포인터를 유지합니다.  컴파일러가 FPO (프레임 포인터 생략)를 수행 하는 경우 EBP 및 ESP를 사용 합니다.  컴파일러가 FPO를 수행 하지 않으면 EBX 및 EBP를 사용 합니다. 코드가 올바르게 실행되도록 하려면 함수가 동적 스택 정렬을 필요로 하는 경우 프레임 포인터를 수정할 수 있으므로 asm 코드에서 EBX를 수정하지 마십시오. 8바이트로 정렬된 형식을 함수 밖으로 이동하거나, EBX를 사용하지 않아야 합니다.

> [!NOTE]
> 인라인 어셈블리 코드가 STD 또는 CLD 명령을 사용하여 방향 플래그를 변경하는 경우 해당 플래그를 원래 값으로 복원해야 합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[인라인 어셈블러](../../assembler/inline/inline-assembler.md)<br/>
