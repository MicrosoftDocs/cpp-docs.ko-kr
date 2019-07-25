---
title: C++ 라이브러리 헤더 사용
ms.date: 11/04/2016
helpviewer_keywords:
- headers, naming in C++ include directive
- standard header in C++
- headers
- INCLUDE directive
- headers, C++ Standard Library
- library headers
- C++ Standard Library, headers
ms.assetid: a36e889e-1af2-4cd9-a211-bfc7a3fd8e85
ms.openlocfilehash: 9cc0bb51b159f6668adad05ebd2d386364ae2f81
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450067"
---
# <a name="using-c-library-headers"></a>C++ 라이브러리 헤더 사용

include 지시문에서 이름을 지정하여 표준 헤더의 내용을 포함할 수 있습니다.

```cpp
#include <iostream>// include I/O facilities
```

표준 헤더는 원하는 어떤 순서로나 포함할 수 있고 두 번 이상 포함할 수도 있으며 같은 매크로나 형식을 정의하는 둘 이상의 표준 헤더를 포함할 수도 있습니다. 선언 내에는 표준 헤더를 포함하지 마세요. 또한 표준 헤더를 포함하기 전에 키워드와 이름이 같은 매크로를 정의하지 마세요.

C++ 라이브러리 헤더에는 필요한 형식을 정의하는 데 사용해야 하는 기타 C++ 라이브러리 헤더가 포함됩니다. 그러나 실제 종속성을 잘못 추측하는 일이 없도록 하려면 항상 필요한 C++ 라이브러리 헤더는 변환 단위에 명시적으로 포함하세요. 표준 C 헤더는 다른 표준 헤더를 포함하지 않습니다. 표준 헤더는 이 문서에서 해당 헤더에 대해 설명되어 있는 엔터티만 선언하거나 정의합니다.

라이브러리의 모든 함수는 표준 헤더에서 선언됩니다. 표준 C에서와는 달리 표준 헤더는 함수 선언을 마스킹하는 함수와 이름이 같은 마스킹 매크로를 제공하지 않고도 동일한 결과를 제공할 수 있습니다. 매크로 마스킹에 대한 자세한 내용은 [C++ 라이브러리 규칙](../standard-library/cpp-library-conventions.md)을 참조하세요.

C++ 라이브러리`std` 헤더에서 **operator delete** 및 **operator new** 이외의 모든 이름은 네임 스페이스 또는 네임 스페이스 내 `std` 에 중첩 된 네임 스페이스에 정의 됩니다. `std::cin`과 같이 `cin`이라는 이름을 참조합니다. 단, 매크로 이름에는 네임스페이스 한정이 적용되지 않으므로 `__STD_COMPLEX`는 항상 네임스페이스 한정자 없이 작성합니다.

일부 변환 환경에서는 C++ 라이브러리 헤더를 포함 하 여 `std` 네임 스페이스에 선언 된 외부 이름을 전역 네임 스페이스에도 호 이스트 할 수 있으며 각 이름에 대해 선언을 **사용 하 여** 개별를 사용할 수도 있습니다. 그렇지 않은 경우 헤더는 현재 네임스페이스로 라이브러리 이름을 가져오지 *않습니다*.

표준 C++ 에서는 C 표준 헤더에서 네임 스페이스 `std`의 모든 외부 이름을 선언 하 고 각 이름에 대 한 선언을 **사용 하** 여 개별를 사용 하는 전역 네임 스페이스로이를 다시 선언 해야 합니다. 하지만 일부 변환 환경에서는 C 표준 헤더가 네임스페이스 선언을 포함하지 않으며 모든 이름을 전역 네임스페이스에서 직접 선언합니다. 따라서 네임스페이스를 처리하는 가장 간편한 방식은 다음의 두 규칙을 따르는 것입니다.

- 일반적으로는 \<stdlib.h> 등에서 선언되는 외부 이름을 `std` 네임스페이스에서 명확하게 선언하려면 \<cstdlib> 헤더를 포함합니다. 이름은 전역 네임스페이스에서도 선언될 수 있습니다.

- \<stdlib.h>에서 선언되는 외부 이름을 전역 네임스페이스에서 명확하게 선언하려면 \<stdlib.h> 헤더를 직접 포함합니다. 이름은 `std` 네임스페이스에서도 선언될 수 있습니다.

따라서 `std::abort`를 호출하여 선언을 비정상적으로 종료하려는 경우에는 \<cstdlib>를 포함해야 합니다. `abort`를 호출하려면 \<stdlib.h>를 포함해야 합니다.

다음과 같은 선언을 작성할 수도 있습니다.

```cpp
using namespace std;
```

모든 라이브러리 이름을 현재 네임스페이스로 가져오는 선언. 모든 include 지시문 바로 뒤에 이 선언을 작성하면 이름이 전역 네임스페이스로 호이스트됩니다. 그리고 나면 변환 단위의 나머지 부분에서는 네임스페이스 고려 사항을 무시해도 됩니다. 서로 다른 여러 변환 환경에서 나타나는 대부분의 차이도 방지할 수 있습니다.

별도로 명시되어 있지 않은 경우에는 프로그램 내의 `std` 네임스페이스 또는 `std` 네임스페이스 내에 중첩된 네임스페이스에서 이름을 정의할 수 없습니다.

## <a name="see-also"></a>참고자료

[C++ 표준 라이브러리 개요](../standard-library/cpp-standard-library-overview.md)\
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
