---
title: 인수 전달 및 명명 규칙
ms.date: 12/17/2018
helpviewer_keywords:
- argument passing [C++], conventions
- arguments [C++], widening
- coding conventions, arguments
- arguments [C++], passing
- registers, return values
- thiscall keyword [C++]
- naming conventions [C++], arguments
- arguments [C++], naming
- passing arguments [C++], conventions
- conventions [C++], argument names
ms.assetid: de468979-eab8-4158-90c5-c198932f93b9
ms.openlocfilehash: 32f32ceb56267dc39b58b8eed1b30af697ca6d74
ms.sourcegitcommit: d5a7ea8e462f555fbb3852d6fe5112521fef3133
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96324178"
---
# <a name="argument-passing-and-naming-conventions"></a>인수 전달 및 명명 규칙

**Microsoft 전용**

Microsoft c + + 컴파일러를 사용 하면 함수와 호출자 간에 인수를 전달 하 고 값을 반환 하는 규칙을 지정할 수 있습니다. 지원되는 모든 플랫폼에서 모든 규칙을 사용할 수 있는 것은 아니며, 일부 규칙은 플랫폼별 구현을 사용합니다. 대부분의 경우 특정 플랫폼에서 지원되지 않는 규칙을 지정하는 키워드 또는 컴파일러 스위치는 무시되며 플랫폼 기본 규칙이 사용됩니다.

X86 플랫폼에서 모든 인수는 전달 될 때 32 비트로 확장 됩니다. 반환 값도 32비트로 확장되며 EDX:EAX 레지스터 쌍에서 반환되는 8바이트 구조체를 제외하고 EAX 레지스터에서 반환됩니다. 더 큰 구조체는 숨겨진 반환 구조체에 대한 포인터로 EAX 레지스터에서 반환됩니다. 매개 변수는 오른쪽에서 왼쪽으로 스택에 푸시됩니다. POD가 아닌 구조체는 레지스터에서 반환되지 않습니다.

컴파일러는 ESI, EDI, EBX 및 EBP 레지스터가 함수에서 사용되는 경우 이러한 레지스터를 저장하고 복원하는 프롤로그 및 에필로그 코드를 생성합니다.

> [!NOTE]
> 구조체, 공용 구조체 또는 클래스가 값으로 함수에서 반환되는 경우 형식의 모든 정의가 동일해야 하며, 그렇지 않으면 프로그램이 런타임에 실패할 수 있습니다.

사용자 고유의 함수 프롤로그 및 에필로그 코드를 정의 하는 방법에 대 한 자세한 내용은 [Naked 함수 호출](../cpp/naked-function-calls.md)을 참조 하세요.

X64 플랫폼을 대상으로 하는 코드의 기본 호출 규칙에 대 한 자세한 내용은 [X64 호출 규칙](../build/x64-calling-convention.md)을 참조 하세요. ARM 플랫폼을 대상으로 하는 코드에서 규칙 문제를 호출 하는 방법에 대 한 자세한 내용은 [일반적인 VISUAL C++ ARM 마이그레이션 문제](../build/common-visual-cpp-arm-migration-issues.md)를 참조 하세요.

다음과 같은 호출 규칙이 Visual C/C++ 컴파일러에서 지원됩니다.

|키워드|스택 정리|매개 변수 전달|
|-------------|-------------------|-----------------------|
|[__cdecl](../cpp/cdecl.md)|Caller|매개 변수를 스택에 역순으로(오른쪽에서 왼쪽으로) 푸시합니다.|
|[__clrcall](../cpp/clrcall.md)|해당 없음|CLR 식 스택에 매개 변수를 순서대로(왼쪽에서 오른쪽으로) 로드합니다.|
|[__stdcall](../cpp/stdcall.md)|호출 수신자|매개 변수를 스택에 역순으로(오른쪽에서 왼쪽으로) 푸시합니다.|
|[__fastcall](../cpp/fastcall.md)|호출 수신자|레지스터에 저장된 다음 스택에 푸시됩니다.|
|[__thiscall](../cpp/thiscall.md)|호출 수신자|스택에 푸시 됨 **`this`** ECX에 저장 된 포인터|
|[__vectorcall](../cpp/vectorcall.md)|호출 수신자|레지스터에 저장된 다음 스택에 역순으로(오른쪽에서 왼쪽으로) 푸시됩니다.|

관련 내용은 [사용 되지 않는 호출 규칙](../cpp/obsolete-calling-conventions.md)을 참조 하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[호출 규칙](../cpp/calling-conventions.md)
