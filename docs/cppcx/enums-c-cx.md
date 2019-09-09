---
title: 열거형(C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: 3bdcff03872dcfe83f0be5752cec4f567fbc6b72
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740219"
---
# <a name="enums-ccx"></a>열거형(C++/CX)

C++/Cx는 표준 `public enum class` C++ `scoped  enum`analagous 하는 키워드를 지원 합니다. `public enum class` 키워드를 사용하여 선언된 열거자를 사용할 경우 열거형 식별자를 사용하여 각 열거자 값의 범위를 지정해야 합니다.

### <a name="remarks"></a>설명

`public enum class` 과 같은 액세스 지정자가 없는 `public`는 표준 C++ [범위 지정 열거형](../cpp/enumerations-cpp.md)으로 처리됩니다.

`public enum class` 또는`public enum struct` 선언에는 모든 정수 형식의 기본 형식이 있을 수 있습니다. 단, Windows 런타임 자체에는 형식이 int32 이거나 플래그 열거형의 경우 uint32가 필요 합니다. 다음 구문에서는 `public enum class` 또는 `public enum struct`부분을 설명합니다.

이 예제에서는 public enum 클래스를 정의하는 방법을 보여 줍니다.

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

다음 예제에서는 클래스를 사용하는 방법을 보여 줍니다.

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>예

다음 예제에서는 열거형을 선언하는 방법을 보여 줍니다.

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

다음 예제에서는 해당 숫자로 캐스팅하고 비교를 수행하는 방법을 보여 줍니다. 열거자 `One` 의 사용은 `Enum1` 열거형 식별자로 범위가 지정되고, 열거자 `First` 는 `Enum2`로 범위가 지정됩니다.

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>참고자료

[형식 시스템](../cppcx/type-system-c-cx.md)<br/>
[C++/CX 언어 참조](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[네임스페이스 참조](../cppcx/namespaces-reference-c-cx.md)
