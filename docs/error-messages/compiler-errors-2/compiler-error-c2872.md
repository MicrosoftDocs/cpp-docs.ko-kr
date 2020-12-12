---
description: '자세한 정보: 컴파일러 오류 C2872'
title: 컴파일러 오류 C2872
ms.date: 11/04/2016
f1_keywords:
- C2872
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
ms.openlocfilehash: b1b1bc09917e499b3b9e1c72070c4a6b19e9c523
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320563"
---
# <a name="compiler-error-c2872"></a>컴파일러 오류 C2872

'*symbol*': 모호한 기호입니다.

컴파일러가 참조 하는 기호를 확인할 수 없습니다. 지정 된 이름의 기호가 둘 이상 범위에 있습니다. 컴파일러에서 모호한 기호에 대해 찾은 파일 위치 및 선언에 대 한 오류 메시지 뒤에 나오는 참고를 참조 하세요. 이 문제를 해결 하기 위해 또는와 같은 네임 스페이스를 사용 하 여 모호한 기호를 정규화 할 수 있습니다 `std::byte` `::byte` . [네임 스페이스 별칭](../../cpp/namespaces-cpp.md#namespace_aliases) 을 사용 하 여 소스 코드에서 기호를 명확히 구분 때 사용할 편리한 짧은 이름을 포함 된 네임 스페이스에 제공할 수도 있습니다.

C2872는 헤더 파일에 [using 지시문](../../cpp/namespaces-cpp.md#using_directives)이 포함 되어 있고 지시문에 지정 된 네임 스페이스에도 있는 형식을 포함 하는 후속 헤더 파일이 포함 되어 있는 경우에 발생할 수 있습니다 **`using`** . **`using`** 모든 헤더 파일이로 지정 된 후에만 지시문을 지정 `#include` 합니다.

C2872는 `Windows::Foundation::Metadata::Platform` 열거형 형식과 c + +/CX-defined 네임 스페이스 간의 충돌로 인해 Visual Studio 2013에서 발생할 수 있습니다 `Platform` . 이 문제를 해결 하려면 다음 단계를 수행 합니다.

- 프로젝트 파일에서 "using namespace Windows:: Foundation:: Metadata" 절을 제거 합니다.

- 이 네임 스페이스에 포함 된 모든 형식의 정규화 된 이름을 지정 합니다.

## <a name="example"></a>예제

다음 샘플에서는 이름이 인 변수에 대해 모호한 참조가 있으므로 C2872을 생성 합니다 `i` . 이름이 같은 두 개의 변수가 범위 내에 있습니다.

```cpp
// C2872.cpp
// compile with: cl /EHsc C2872.cpp
namespace A {
   int i;
}

using namespace A;
int i;
int main() {
   ::i++;   // ok, uses i from global namespace
   A::i++;   // ok, uses i from namespace A
   i++;   // C2872 ambiguous: ::i or A::i?
   // To fix this issue, use the fully qualified name
   // for the intended variable.
}
```
