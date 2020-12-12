---
description: '자세한 정보: 컴파일러 경고 (수준 2) C4412'
title: 컴파일러 경고(수준 2) C4412
ms.date: 11/04/2016
f1_keywords:
- C4412
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
ms.openlocfilehash: 9b7ce857d5b0545ac620e94bda9655dde0f63489
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208634"
---
# <a name="compiler-warning-level-2-c4412"></a>컴파일러 경고(수준 2) C4412

> '*function*': 함수 시그니처에 '*type*' 형식이 포함 되어 있습니다. C + + 개체는 순수형 코드와 mixed 또는 native 간에 전달 하기에 안전 하지 않습니다.

## <a name="remarks"></a>설명

**/Clr: pure** 컴파일러 옵션은 visual studio 2015에서는 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다. 순수 해야 하는 코드가 있는 경우 c #으로 이식 하는 것이 좋습니다.

컴파일러가 잠재적으로 안전 하지 않은 상황을 발견 하 여 런타임 오류가 발생할 수 있습니다. **/clr: pure** compiland에서 dllimport를 통해 가져온 함수로의 호출을 수행 하 고 있으며 함수 시그니처에 unsafe 형식이 포함 되어 있습니다. 멤버 함수가 포함 되어 있거나 안전 하지 않은 형식 또는 안전 하지 않은 형식에 대 한 간접 참조 인 데이터 멤버가 있는 경우 형식이 안전 하지 않습니다.

이는 순수 코드와 네이티브 코드 (또는 혼합 네이티브 및 관리) 간의 기본 호출 규칙의 차이로 인해 안전 하지 않습니다. `dllimport`함수를 **/clr: pure** compiland로 가져올 때 시그니처의 각 형식 선언이 함수를 내보내는 compiland의 선언과 동일한 지 확인 합니다. 특히 암시적 호출 규칙의 차이점에 주의 해야 합니다.

가상 멤버 함수는 예기치 않은 결과를 제공 하는 데 특히 취약 합니다.  그러나 비가상 함수를 테스트 하 여 올바른 결과를 얻을 수 있는지 확인 해야 합니다. 올바른 결과를 얻는 것이 확실 한 경우이 경고를 무시 해도 됩니다.

C4412은 기본적으로 해제 되어 있습니다. 자세한 내용은 [기본적으로 해제 되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 및 [dllexport, dllimport를](../../cpp/dllexport-dllimport.md) 참조 하세요.

이 경고를 해결 하려면 형식에서 모든 함수를 제거 합니다.

## <a name="examples"></a>예제

다음 샘플에서는 C4412를 생성 합니다.

```cpp
// C4412.cpp
// compile with: /c /W2 /clr:pure
#pragma warning (default : 4412)

struct Unsafe {
   virtual void __cdecl Test();
};

struct Safe {
   int i;
};

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   Unsafe *pUnsafe = func();   // C4412
   // pUnsafe->Test();

   Safe *pSafe = func2();   // OK
}
```

다음 샘플은 두 개의 형식을 선언 하는 헤더 파일입니다. `Unsafe`멤버 함수가 있으므로 형식이 안전 하지 않습니다.

```cpp
// C4412.h
struct Unsafe {
   // will be __clrcall if #included in pure compilation
   // defaults to __cdecl in native or mixed mode compilation
   virtual void Test(int * pi);

   // try the following line instead
   // virtual void __cdecl Test(int * pi);
};

struct Safe {
   int i;
};
```

이 샘플에서는 헤더 파일에 정의 된 형식을 사용 하 여 함수를 내보냅니다.

```cpp
// C4412_2.cpp
// compile with: /LD
#include "C4412.h"

void Unsafe::Test(int * pi) {
   *pi++;
}

__declspec(dllexport) Unsafe * __cdecl func() { return new Unsafe; }
__declspec(dllexport) Safe * __cdecl func2() { return new Safe; }
```

**/Clr: pure** 컴파일의 기본 호출 규칙은 네이티브 컴파일과 다릅니다.  C4412이 포함 된 경우 기본값은 `Test` `__clrcall` 입니다. 이 프로그램을 컴파일 및 실행 하는 경우 ( **/c** 를 사용 하지 않음) 프로그램에서 예외를 throw 합니다.

다음 샘플에서는 C4412를 생성 합니다.

```cpp
// C4412_3.cpp
// compile with: /W2 /clr:pure /c /link C4412_2.lib
#pragma warning (default : 4412)
#include "C4412.h"

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   int n = 7;
   Unsafe *pUnsafe = func();   // C4412
   pUnsafe->Test(&n);

   Safe *pSafe = func2();   // OK
}
```
