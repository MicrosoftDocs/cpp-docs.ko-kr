---
description: '자세한 정보: 컴파일러 내장 함수'
title: 컴파일러 내장 함수
ms.date: 09/02/2019
helpviewer_keywords:
- intrinsics, compiler
- compiler intrinsics
- cl.exe compiler, performance
- cl.exe compiler, intrinsics
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
ms.openlocfilehash: c81608af1021919691b6241e14b1fefbe03643f4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337163"
---
# <a name="compiler-intrinsics"></a>컴파일러 내장 함수

대부분의 함수는 라이브러리에 포함되어 컴파일러에서 기본 제공되는 내장 함수도 있습니다. 이러한 함수를 내장 함수라고 합니다.

## <a name="remarks"></a>설명

내장 함수의 코드는 보통 인라인으로 삽입되므로 함수 호출 오버헤드가 발생하지 않으며 해당 함수에 대해 매우 효율적인 컴퓨터 명령을 내보낼 수 있습니다. 내장 함수는 동일한 인라인 어셈블리보다 속도가 빠른 경우가 많습니다. 최적화 프로그램에는 정상적으로 동작하는 내장 함수의 수를 확인하는 기본 기능이 있어서 인라인 어셈블리를 사용할 때는 제공되지 않는 일부 최적화 기능을 사용할 수 있기 때문입니다. 또한 최적화 프로그램은 내장 함수를 다르게 확장하거나, 버퍼를 다르게 정렬하거나, 호출의 인수와 컨텍스트에 따라 기타 조정을 수행할 수도 있습니다.

내장 함수를 사용하는 경우 코드의 이식성에 영향을 주게 됩니다. Visual C++에서 사용할 수 있는 내장 함수는 코드를 다른 컴파일러로 컴파일하는 경우에는 제공되지 않을 수도 있으며 일부 대상 아키텍처에 대해 제공되는 내장 함수를 모든 아키텍처에 사용할 수 있는 것은 아니기 때문입니다. 그러나 내장 함수는 일반적으로 인라인 어셈블리보다 이식성이 뛰어납니다. 인라인 어셈블리가 지원되지 않는 64비트 아키텍처에서는 내장 함수를 사용해야 합니다.

및와 같은 일부 내장 함수는 **`__assume`** `__ReadWriteBarrier` 최적화 프로그램의 동작에 영향을 주는 정보를 컴파일러에 제공 합니다.

내장 함수로만 사용할 수 있는 함수도 있고 함수 및 내장 함수 구현에서 모두 사용할 수 있는 함수도 있습니다. 특정 함수만 사용하도록 설정할지 아니면 모든 내장 함수를 사용하도록 설정할지에 따라 두 가지 방법 중 하나로 내장 함수 구현을 사용하도록 컴파일러에 명령할 수 있습니다. 첫 번째 방법은 `#pragma intrinsic(` *내장 함수 이름 목록을* 사용 하는 것입니다 `)` . 여기서는 pragma를 사용하여 내장 함수 하나 또는 쉼표로 구분된 여러 내장 함수를 지정할 수 있습니다. 두 번째는 지정 된 플랫폼에서 모든 내장 함수를 사용할 수 있도록 하는 [/oi (내장 함수 생성)](../build/reference/oi-generate-intrinsic-functions.md) 컴파일러 옵션을 사용 하는 것입니다. **/Oi** 에서 내장 `#pragma function(` 함수 대신 함수 호출을 사용 하려면 *내장 함수 이름 목록을* 사용 `)` 합니다. 특정 내장 함수에 대 한 설명서에서 루틴을 내장 함수로만 사용할 수 있는 경우에는 기본 구현은 **/oi** 또는이 지정 되었는지 여부에 관계 없이 사용 됩니다 `#pragma intrinsic` . 모든 경우에는 **/oi** 또는가 `#pragma intrinsic` 내장 함수를 사용 하도록 최적화를 허용 하지만 강제로 적용 하지는 않습니다. 즉, 최적화 프로그램은 함수를 호출할 수도 있습니다.

일부 아키텍처에서는 내장 함수 구현에 일부 표준 C/C++ 라이브러리 함수를 사용할 수 있습니다. CRT 함수를 호출 하는 경우 명령줄에서 **/oi** 를 지정 하면 내장 구현이 사용 됩니다.

\<intrin.h>일반적인 내장 함수의 프로토타입을 선언 하는 헤더 파일를 사용할 수 있습니다. 제조업체 고유의 내장 함수는 \<immintrin.h> 및 헤더 파일에서 사용할 수 있습니다 \<ammintrin.h> . 또한 특정 Windows 헤더는 컴파일러 내장 함수에 매핑되는 함수를 선언합니다.

다음 섹션에는 다양한 아키텍처에서 사용할 수 있는 모든 내장 함수를 나열합니다. 사용 중인 대상 프로세서에서 내장 함수가 작동하는 방식에 대한 자세한 내용은 제조업체의 참조 설명서를 참조하세요.

- [ARM 내장 함수](../intrinsics/arm-intrinsics.md)

- [ARM64 내장 함수](../intrinsics/arm64-intrinsics.md)

- [x86 내장 목록](../intrinsics/x86-intrinsics-list.md)

- [x64(amd64) 내장 목록](../intrinsics/x64-amd64-intrinsics-list.md)

- [모든 아키텍처에서 사용할 수 있는 내장 함수](../intrinsics/intrinsics-available-on-all-architectures.md)

- [내장 함수의 사전순 목록](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)

## <a name="see-also"></a>참고 항목

[ARM 어셈블러 참조](../assembler/arm/arm-assembler-reference.md)<br/>
[Microsoft 매크로 어셈블러 참조](../assembler/masm/microsoft-macro-assembler-reference.md)<br/>
[키워드](../cpp/keywords-cpp.md)<br/>
[C 런타임 라이브러리 참조](../c-runtime-library/c-run-time-library-reference.md)
