---
title: 컴파일러 내장 함수
ms.date: 11/04/2016
helpviewer_keywords:
- intrinsics, compiler
- compiler intrinsics
- cl.exe compiler, performance
- cl.exe compiler, intrinsics
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
ms.openlocfilehash: 9a014e870d731d7e7d443c3bfefd66884aa50d5d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029280"
---
# <a name="compiler-intrinsics"></a>컴파일러 내장 함수

대부분의 함수는 라이브러리에 포함되어 컴파일러에서 기본 제공되는 내장 함수도 있습니다. 이러한 함수를 내장 함수라고 합니다.

## <a name="remarks"></a>설명

내장 함수의 코드는 보통 인라인으로 삽입되므로 함수 호출 오버헤드가 발생하지 않으며 해당 함수에 대해 매우 효율적인 컴퓨터 명령을 내보낼 수 있습니다. 내장 함수는 동일한 인라인 어셈블리보다 속도가 빠른 경우가 많습니다. 최적화 프로그램에는 정상적으로 동작하는 내장 함수의 수를 확인하는 기본 기능이 있어서 인라인 어셈블리를 사용할 때는 제공되지 않는 일부 최적화 기능을 사용할 수 있기 때문입니다. 또한 최적화 프로그램은 내장 함수를 다르게 확장하거나, 버퍼를 다르게 정렬하거나, 호출의 인수와 컨텍스트에 따라 기타 조정을 수행할 수도 있습니다.

내장 함수를 사용하는 경우 코드의 이식성에 영향을 주게 됩니다. Visual C++에서 사용할 수 있는 내장 함수는 코드를 다른 컴파일러로 컴파일하는 경우에는 제공되지 않을 수도 있으며 일부 대상 아키텍처에 대해 제공되는 내장 함수를 모든 아키텍처에 사용할 수 있는 것은 아니기 때문입니다. 그러나 내장 함수는 일반적으로 인라인 어셈블리보다 이식성이 뛰어납니다. 인라인 어셈블리가 지원되지 않는 64비트 아키텍처에서는 내장 함수를 사용해야 합니다.

`__assume`, `__ReadWriteBarrier` 등의 일부 내장 함수는 컴파일러에 정보를 제공하므로 최적화 프로그램의 동작에 영향을 줍니다.

내장 함수로만 사용할 수 있는 함수도 있고 함수 및 내장 함수 구현에서 모두 사용할 수 있는 함수도 있습니다. 특정 함수만 사용하도록 설정할지 아니면 모든 내장 함수를 사용하도록 설정할지에 따라 두 가지 방법 중 하나로 내장 함수 구현을 사용하도록 컴파일러에 명령할 수 있습니다. 첫 번째 방법은 사용 하는 것 `#pragma intrinsic(` *내장-함수 이름-목록을*`)`합니다. 여기서는 pragma를 사용하여 내장 함수 하나 또는 쉼표로 구분된 여러 내장 함수를 지정할 수 있습니다. 두 번째 사용 하는 것은 [/Oi (내장 함수 생성)](../build/reference/oi-generate-intrinsic-functions.md) 모든 내장 함수는 지정 된 플랫폼에서 사용할 수 있도록 컴파일러 옵션입니다. 아래 **/Oi**를 사용 하 여 `#pragma function(` *내장 함수-이름-목록* `)` to be used instead 내장 함수 호출을 하도록 합니다. 특정 내장 함수의 설명서는 정보는 루틴은 내장 함수로 사용할 수만 있으면 여부에 관계 없이 내장 함수 구현이 사용 됩니다 **/Oi** 또는 `#pragma intrinsic` 지정 됩니다. 경우도 **/Oi** 또는 `#pragma intrinsic` 허용 하기는 하지만 최적화 프로그램이 내장 함수를 사용 하도록 강제 하지 않습니다. 즉, 최적화 프로그램은 함수를 호출할 수도 있습니다.

일부 아키텍처에서는 내장 함수 구현에 일부 표준 C/C++ 라이브러리 함수를 사용할 수 있습니다. CRT 함수를 호출할 경우 내장 함수 구현이 사용 됩니다 **/Oi** 명령줄에 지정 됩니다.

헤더 파일에 \<intrin.h >에 일반 내장 함수의 프로토타입을 선언 하는 사용할 수 있습니다. 제조업체별 내장 함수에서 사용할 수는 \<immintrin.h > 및 \<ammintrin.h가 > 헤더 파일입니다. 또한 특정 Windows 헤더는 컴파일러 내장 함수에 매핑되는 함수를 선언합니다.

다음 섹션에는 다양한 아키텍처에서 사용할 수 있는 모든 내장 함수를 나열합니다. 사용 중인 대상 프로세서에서 내장 함수가 작동하는 방식에 대한 자세한 내용은 제조업체의 참조 설명서를 참조하세요.

- [ARM 내장 함수](../intrinsics/arm-intrinsics.md)

- [x86 내장 목록](../intrinsics/x86-intrinsics-list.md)

- [x64(amd64) 내장 목록](../intrinsics/x64-amd64-intrinsics-list.md)

- [모든 아키텍처에서 사용할 수 있는 내장 함수](../intrinsics/intrinsics-available-on-all-architectures.md)

- [내장 함수의 사전순 목록](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)

## <a name="see-also"></a>참고자료

[ARM 어셈블러 참조](../assembler/arm/arm-assembler-reference.md)<br/>
[Microsoft 매크로 어셈블러 참조](../assembler/masm/microsoft-macro-assembler-reference.md)<br/>
[키워드](../cpp/keywords-cpp.md)<br/>
[C 런타임 라이브러리 참조](../c-runtime-library/c-run-time-library-reference.md)