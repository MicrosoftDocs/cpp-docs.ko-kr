---
description: '자세한 정보: 최적화에 유용한 정보'
title: 최적화에 유용한 정보
ms.date: 05/06/2019
helpviewer_keywords:
- C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: 06588225838da3b52216fa0ae3eb51b7538ee58d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179826"
---
# <a name="optimization-best-practices"></a>최적화에 유용한 정보

이 문서에서는 Visual Studio에서 C++ 프로그램을 최적화하기 위한 몇 가지 모범 사례를 설명합니다.

## <a name="compiler-and-linker-options"></a>컴파일러 및 링커 옵션

### <a name="profile-guided-optimization"></a>프로필 기반 최적화

Visual Studio에서는  PGO(프로필 기반 최적화)를 지원합니다. 이 최적화는 애플리케이션의 계측된 버전에 대한 학습 실행의 프로필 데이터를 사용하여 이후의 애플리케이션 최적화를 진행합니다. PGO를 사용하면 시간이 많이 걸릴 수 있으므로 모든 개발자가 사용할 필요는 없지만, 제품의 최종 릴리스 빌드에 PGO를 사용하는 것이 좋습니다. 자세한 내용은 [프로필 기반 최적화](profile-guided-optimizations.md)를 참조하세요.

또한 전체 프로그램 최적화(링크 타임 코드 생성이라고도 함)와 **`/O1`** 및 **`/O2`** 최적화가 향상되었습니다. 일반적으로 이러한 옵션 중 하나를 사용하여 컴파일된 애플리케이션은 이전 컴파일러로 컴파일된 애플리케이션보다 빠릅니다.

자세한 내용은 [`/GL`(전체 프로그램 최적화)](reference/gl-whole-program-optimization.md) 및 [`/O1`, `/O2`(크기 최소화, 속도 최대화)](reference/o1-o2-minimize-size-maximize-speed.md)를 참조하세요.

### <a name="which-level-of-optimization-to-use"></a>사용할 최적화 수준

가능하면 프로필 기반 최적화를 사용하여 최종 릴리스 빌드를 컴파일해야 합니다. 계측된 빌드를 실행하기 위한 인프라가 부족하거나 시나리오에 액세스할 수 없어 PGO를 사용하여 빌드할 수 없는 경우 전체 프로그램 최적화를 사용하여 빌드하는 것이 좋습니다.

**`/Gy`** 스위치도 매우 유용합니다. 이 스위치는 각 함수마다 별도의 COMDAT를 생성하여 링커가 참조되지 않은 COMDAT 및 COMDAT 접기를 제거하는 데 더 많은 유연성을 제공합니다. **`/Gy`** 를 사용하는 경우 유일한 단점은 디버그할 때 문제가 발생할 수 있다는 것입니다. 따라서 일반적으로 사용을 권장합니다. 자세한 내용은 [`/Gy`(함수 수준 링크 사용)](reference/gy-enable-function-level-linking.md)를 참조하세요.

64비트 환경에서 연결하는 경우 **`/OPT:REF,ICF`** 링커 옵션을 사용하고 32비트 환경에서는 **`/OPT:REF`** 를 사용하는 것이 좋습니다. 자세한 내용은 [/OPT(최적화)](reference/opt-optimizations.md)를 참조하세요.

최적화된 릴리스 빌드라도 디버그 기호를 생성하는 것도 좋습니다. 이는 생성된 코드에 영향을 주지 않으며, 필요한 경우 애플리케이션을 훨씬 더 쉽게 디버그할 수 있습니다.

### <a name="floating-point-switches"></a>부동 소수점 스위치

**`/Op`** 컴파일러 옵션이 제거되었으며 부동 소수점 최적화를 처리하는 다음 네 가지 컴파일러 옵션이 추가되었습니다.

|옵션|Description|
|-|-|
|**`/fp:precise`**|이 옵션은 기본 권장 사항이며 대부분의 경우 사용해야 합니다.|
|**`/fp:fast`**|게임과 같이 성능이 가장 중요한 경우에 권장됩니다. 이 옵션을 사용하면 성능이 가장 빠릅니다.|
|**`/fp:strict`**|정밀한 부동 소수점 예외 및 IEEE 동작이 필요한 경우에 권장됩니다. 이 옵션을 사용하면 성능이 가장 느립니다.|
|**`/fp:except[-]`**|**`/fp:strict`** 또는 **`/fp:precise`** 와 함께 사용할 수 있지만 **`/fp:fast`** 와는 사용할 수 없습니다.|

자세한 내용은 [`/fp`(부동 소수점 동작 지정)](reference/fp-specify-floating-point-behavior.md)를 참조하세요.

## <a name="optimization-declspecs"></a>최적화 declspec

이 섹션에서는 프로그램에서 성능을 개선하기 위해 사용할 수 있는 두 가지 declspec `__declspec(restrict)` 및 `__declspec(noalias)`을 살펴보겠습니다.

`restrict` declspec은 포인터를 반환하는 함수 선언에만 적용할 수 있습니다(예: `__declspec(restrict) void *malloc(size_t size);`).

`restrict` declspec은 별칭이 지정되지 않은 포인터를 반환하는 함수에 사용됩니다. 이 키워드는 해제된 메모리를 사용하는 등의 잘못된 작업을 수행하지 않는 한 현재 프로그램에서 이미 사용 중인 포인터 값을 반환하지 않기 때문에 `malloc`의 C 런타임 라이브러리 구현에 사용됩니다.

`restrict` declspec은 컴파일러 최적화를 수행하기 위한 자세한 정보를 컴파일러에 제공합니다. 컴파일러가 결정해야 하는 가장 어려운 것 중 하나는 어떤 포인터가 다른 포인터에 별칭을 지정할지 결정하는 것인데, 이 정보를 사용하면 컴파일러에 매우 유용합니다.

이는 컴파일러가 확인할 것이 아니라 컴파일러에 대한 약속이라는 점을 알아야 합니다. 프로그램이 이 `restrict` declspec을 잘못 사용하는 경우 프로그램에서 잘못된 동작이 발생할 수 있습니다.

자세한 내용은 [`restrict`](../cpp/restrict.md)를 참조하세요.

또한 `noalias` declspec은 함수에만 적용되며, 해당 함수가 반 순수 함수임을 나타냅니다. 반 순수 함수는 로컬 변수, 인수 및 인수의 첫 번째 수준 간접 참조만 참조하거나 수정하는 함수입니다. 이 declspec은 컴파일러에 대한 약속이며 함수가 전역 변수 또는 포인터 인수의 두 번째 수준 간접 참조를 참조하는 경우 컴파일러에서 애플리케이션을 중단하는 코드를 생성할 수 있습니다.

자세한 내용은 [`noalias`](../cpp/noalias.md)를 참조하세요.

## <a name="optimization-pragmas"></a>최적화 pragma

코드를 최적화하는 데 도움이 되는 몇 가지 유용한 pragma도 있습니다. 첫 번째로 설명한 pragma는 `#pragma optimize`입니다.

```cpp
#pragma optimize("{opt-list}", on | off)
```

이 pragma를 사용하면 함수별로 지정된 최적화 수준을 설정할 수 있습니다. 이는 지정된 함수가 최적화를 사용하여 컴파일될 때 애플리케이션이 작동을 중단하는 드문 경우에 적합합니다. 이를 사용하여 단일 함수에 대한 최적화를 해제할 수 있습니다.

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

자세한 내용은 [`optimize`](../preprocessor/optimize.md)를 참조하세요.

인라이닝은 컴파일러가 수행하는 가장 중요한 최적화 중 하나이며 여기서는 이 동작을 수정하는 데 도움이 되는 몇 가지 pragma에 대해 설명합니다.

`#pragma inline_recursion`은 애플리케이션에서 재귀 호출을 인라인 처리할 수 있는지 여부를 지정하는 데 유용합니다. 기본적으로 이 pragma는 해제되어 있습니다. 소규모 함수의 단순 재귀를 위해 이를 설정할 수 있습니다. 자세한 내용은 [`inline_recursion`](../preprocessor/inline-recursion.md)를 참조하세요.

인라이닝 수준을 제한하는 또 다른 유용한 pragma는 `#pragma inline_depth`입니다. 이 pragma는 일반적으로 프로그램 또는 함수의 크기를 제한하려는 경우에 유용합니다. 자세한 내용은 [`inline_depth`](../preprocessor/inline-depth.md)를 참조하세요.

## <a name="__restrict-and-__assume"></a>`__restrict` 및 `__assume`

Visual Studio에는 성능 개선에 도움이 될 수 있는 두 가지 키워드가 있습니다. [__restrict](../cpp/extension-restrict.md) 및 [__assume](../intrinsics/assume.md).

첫째, **`__restrict`** 와 `__declspec(restrict)`은 서로 다릅니다. 어느 정도 관련은 있지만 해당 의미 체계가 다릅니다. **`__restrict`** 는 **`const`** 또는 **`volatile`** 과 같은 형식 한정자이지만 포인터 형식에만 사용됩니다.

**`__restrict`** 로 수정된 포인터를 __restrict 포인터라고 합니다. __restrict 포인터는 \__restrict 포인터를 통해서만 액세스할 수 있는 포인터입니다. 즉, 다른 포인터를 사용하여 \__restrict 포인터가 가리키는 데이터에 액세스할 수 없습니다.

**`__restrict`** 는 Microsoft C++ 최적화 프로그램을 위한 강력한 도구가 될 수 있지만 매우 신중하게 사용해야 합니다. 잘못 사용하는 경우 최적화 프로그램에서 애플리케이션을 중단하는 최적화를 수행할 수 있습니다.

**`__restrict`** 키워드는 이전 버전의 **/Oa** 스위치를 대체합니다.

개발자는 **`__assume`** 을 사용하여 일부 변수의 값을 가정하도록 컴파일러에 지시할 수 있습니다.

예를 들어 `__assume(a < 5);`은 최적화 프로그램에 해당 코드 줄에서 변수 `a`가 5미만이라고 지시합니다. 이 또한 컴파일러에 대한 약속입니다. 프로그램에서 실제로 `a`가 6인 경우에는 컴파일러가 최적화된 후 프로그램의 동작이 예상과 다를 수 있습니다. **`__assume`** 은 문 및/또는 조건식을 전환하기 전에 가장 유용합니다.

**`__assume`** 에는 몇 가지 제한 사항이 있습니다. 첫째, **`__restrict`** 처럼 단지 제안이므로 컴파일러가 무시할 수 있습니다. 또한 현재 **`__assume`** 은 상수 부등식 변수에만 작동합니다. 예를 들어 assume(a < b) 같이 기호로만 구성된 부등식은 사용할 수 없습니다.

## <a name="intrinsic-support"></a>내장 함수 지원

내장 함수는 컴파일러가 호출에 대한 내장 정보를 포함하고 라이브러리에서 함수를 호출하는 대신 해당 함수에 대한 코드를 내보내는 함수 호출입니다. 헤더 파일 \<intrin.h>에는 지원되는 각 하드웨어 플랫폼에 대해 사용 가능한 모든 내장 함수가 포함되어 있습니다.

내장 함수를 사용하면 프로그래머가 어셈블리를 사용하지 않고도 코드를 상세하게 파악할 수 있습니다. 내장 함수를 사용하는 경우 다음과 같은 몇 가지 이점이 있습니다.

- 코드의 이식성이 향상됩니다. 여러 개의 내장 함수를 여러 CPU 아키텍처에서 사용할 수 있습니다.

- 코드가 여전히 C/C++로 작성되므로 코드를 더 쉽게 읽을 수 있습니다.

- 코드가 컴파일러 최적화의 이점을 얻습니다. 컴파일러가 우수할수록 내장 함수에 대한 코드 생성이 향상됩니다.

자세한 내용은 [컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)를 참조하세요.

## <a name="exceptions"></a>예외

예외 사용과 관련된 성능 저하가 있습니다. 컴파일러가 특정 최적화를 수행할 수 없도록 하는 try 블록을 사용하는 경우 몇 가지 제한 사항이 도입되었습니다. x86 플랫폼에서는 코드를 실행하는 동안 생성되어야 하는 추가 상태 정보로 인해 try 블록에서 추가 성능 저하가 발생합니다. 64비트 플랫폼에서는 try 블록의 성능이 저하되지 않지만 예외가 throw되면 처리기를 찾고 스택을 해제하는 프로세스에 비용이 많이 들 수 있습니다.

따라서 필요하지 않은 코드에 try/catch 블록을 도입하지 않는 것이 좋습니다. 예외를 사용해야 하는 경우 가능하면 동기 예외를 사용합니다. 자세한 내용은 [Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)을 참조하세요.

마지막으로, 예외적인 경우에만 예외를 throw합니다. 일반적인 제어 흐름에 대한 예외를 사용하면 성능이 저하될 수 있습니다.

## <a name="see-also"></a>참조

- [코드 최적화](optimizing-your-code.md)
