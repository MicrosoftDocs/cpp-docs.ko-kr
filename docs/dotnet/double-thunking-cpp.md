---
title: 이중 썽킹(C++)
ms.date: 11/04/2016
helpviewer_keywords:
- double thunks
- interop [C++], double thunking
- mixed assemblies [C++], double thunking
- /clr compiler option [C++], double thunking
- interoperability [C++], double thunking
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
ms.openlocfilehash: 3f0fc5567baaa0c4f3fea410770963adf51e8366
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414011"
---
# <a name="double-thunking-c"></a>이중 썽킹(C++)

이중 썽킹은 관리 되는 컨텍스트의 함수 호출에서 관리 되는 함수 Visual C++를 호출 하 고 프로그램 실행이 관리 되는 함수를 호출 하기 위해 함수의 네이티브 진입점을 호출 하는 경우 발생할 수 있는 성능 저하를 나타냅니다. 이 항목에서는 이중 썽킹이 발생 하는 위치 및 성능 향상을 방지 하는 방법을 설명 합니다.

## <a name="remarks"></a>설명

기본적으로 **/clr**을 사용 하 여 컴파일할 때 관리 되는 함수를 정의 하면 컴파일러에서 관리 되는 진입점과 네이티브 진입점을 생성 합니다. 이렇게 하면 네이티브 및 관리 되는 호출 사이트에서 관리 되는 함수를 호출할 수 있습니다. 그러나 네이티브 진입점이 있는 경우에는 함수에 대 한 모든 호출에 대 한 진입점이 될 수 있습니다. 호출 함수를 관리 하는 경우 네이티브 진입점이 관리 되는 진입점을 호출 합니다. 실제로 두 호출은 함수를 호출 하는 데 필요 합니다 (따라서 이중 썽킹). 예를 들어 가상 함수는 항상 기본 진입점을 통해 호출 됩니다.

한 가지 해결 방법은 관리 되는 함수에 대 한 네이티브 진입점을 생성 하지 않도록 컴파일러에 지시 하는 것입니다. 함수는 [__clrcall](../cpp/clrcall.md) 호출 규칙을 사용 하 여 관리 되는 컨텍스트에서만 호출 됩니다.

마찬가지로 관리 되는 함수를 내보내는 경우 ([dllexport, dllimport](../cpp/dllexport-dllimport.md)) 네이티브 진입점이 생성 되 고 해당 함수를 가져오고 호출 하는 모든 함수가 네이티브 진입점을 통해를 호출 합니다. 이러한 상황에서 이중 썽킹을 방지 하려면 네이티브 내보내기/가져오기 의미 체계를 사용 하지 마십시오. 를 통해 메타 데이터를 참조 하면 됩니다 `#using` ( [#using 지시문](../preprocessor/hash-using-directive-cpp.md)참조).

컴파일러는 불필요 한 이중 썽킹을 줄이기 위해 업데이트 되었습니다. 예를 들어, 시그니처에 관리 되는 형식이 있는 모든 함수 (반환 형식 포함)는 암시적으로로 표시 됩니다 `__clrcall` .

## <a name="example-double-thunking"></a>예: 이중 썽킹

### <a name="description"></a>Description

다음 샘플에서는 이중 썽킹을 보여 줍니다. 네이티브 ( **/clr**을 사용 하지 않음)를 컴파일할 때의 가상 함수 호출은 `main` 의 복사 생성자에 대 한 호출을 생성 하 `T` 고 소멸자에 대 한 호출을 하나씩 생성 합니다. 가상 함수가 **/clr** 및로 선언 된 경우에도 비슷한 동작이 수행 됩니다 `__clrcall` . 그러나 **/clr**을 사용 하 여 컴파일한 경우 함수 호출은 복사 생성자에 대 한 호출을 생성 하지만 네이티브에서 관리 되는 썽크 때문에 복사 생성자에 대 한 다른 호출은 있습니다.

### <a name="code"></a>코드

```cpp
// double_thunking.cpp
// compile with: /clr
#include <stdio.h>
struct T {
   T() {
      puts(__FUNCSIG__);
   }

   T(const T&) {
      puts(__FUNCSIG__);
   }

   ~T() {
      puts(__FUNCSIG__);
   }

   T& operator=(const T&) {
      puts(__FUNCSIG__);
      return *this;
   }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;

   printf("calling struct S\n");
   pS->f(t);
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>샘플 출력

```
__thiscall T::T(void)
calling struct S
__thiscall T::T(const struct T &)
__thiscall T::T(const struct T &)
__thiscall T::~T(void)
__thiscall T::~T(void)
after calling struct S
__thiscall T::~T(void)
```

## <a name="example-effect-of-double-thunking"></a>예: 이중 썽킹의 효과

### <a name="description"></a>Description

이전 샘플에서는 이중 썽킹이 있음을 보여 주었습니다. 이 샘플은 해당 효과를 보여 줍니다. **`for`** 루프는 가상 함수를 호출 하 고 프로그램은 실행 시간을 보고 합니다. 프로그램이 **/clr**로 컴파일될 때 가장 느린 시간이 보고 됩니다. **/Clr** 을 사용 하지 않고 컴파일할 때 또는 가상 함수가로 선언 된 경우 가장 빠른 시간이 보고 됩니다 `__clrcall` .

### <a name="code"></a>코드

```cpp
// double_thunking_2.cpp
// compile with: /clr
#include <time.h>
#include <stdio.h>

#pragma unmanaged
struct T {
   T() {}
   T(const T&) {}
   ~T() {}
   T& operator=(const T&) { return *this; }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;
   clock_t start, finish;
   double  duration;
   start = clock();

   for ( int i = 0 ; i < 1000000 ; i++ )
      pS->f(t);

   finish = clock();
   duration = (double)(finish - start) / (CLOCKS_PER_SEC);
   printf( "%2.1f seconds\n", duration );
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>샘플 출력

```
4.2 seconds
after calling struct S
```

## <a name="see-also"></a>참고 항목

[혼합형 (네이티브 및 관리) 어셈블리](../dotnet/mixed-native-and-managed-assemblies.md)
