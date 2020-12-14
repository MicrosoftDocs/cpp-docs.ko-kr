---
description: '자세한 정보: 디버그 반복기 지원'
title: Debug Iterator Support
ms.date: 09/13/2018
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- C++ Standard Library, debug iterator support
- iterators, debug iterator support
- iterators, incompatible
- incompatible iterators
- debug iterator support
ms.assetid: f3f5bd15-4be8-4d64-a4d0-8bc0761c68b6
ms.openlocfilehash: bd2de8423cb7235fdb54a3d0cfe852081ea32b18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232956"
---
# <a name="debug-iterator-support"></a>Debug Iterator Support

Visual C++ 런타임 라이브러리는 부정확한 반복기 사용을 검색하고 런타임에 대화 상자를 어설션하고 표시합니다. Debug Iterator Support를 사용하도록 설정하려면 프로그램 컴파일 시 C++ 표준 라이브러리 및 C 런타임 라이브러리의 디버그 버전을 사용해야 합니다. 자세한 내용은 [CRT 라이브러리 기능](../c-runtime-library/crt-library-features.md)을 참조하세요. 확인된 반복기를 사용하는 방법에 대한 자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

C++ 표준은 멤버 함수로 인해 컨테이너에 대한 반복기가 어떻게 무효화되는지 설명합니다. 다음과 같은 두 가지 예가 있습니다.

- 컨테이너에서 요소를 지우면 요소에 대한 반복기가 무효화됩니다.

- push 또는 insert를 사용하여 [vector](../standard-library/vector.md)의 크기를 줄이면 `vector`에 대한 반복기가 무효화됩니다.

## <a name="invalid-iterators"></a>잘못 된 반복기

이 샘플 프로그램을 디버그 모드에서 컴파일하면 이 프로그램이 런타임에 어설션되고 종료됩니다.

```cpp
// iterator_debugging_0.cpp
// compile by using /EHsc /MDd
#include <vector>
#include <iostream>

int main() {
   std::vector<int> v {10, 15, 20};
   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

## <a name="using-_iterator_debug_level"></a>_ITERATOR_DEBUG_LEVEL 사용

전처리기 매크로 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)을 사용하여 디버그 빌드에서 반복기 디버깅 기능을 끌 수 있습니다. 이 프로그램은 어설션되지 않지만 정의되지 않은 동작을 계속 트리거합니다.

```cpp
// iterator_debugging_1.cpp
// compile by using: /EHsc /MDd
#define _ITERATOR_DEBUG_LEVEL 0
#include <vector>
#include <iostream>

int main() {
    std::vector<int> v {10, 15, 20};

   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

```Output
20
-572662307
```

## <a name="unitialized-iterators"></a>초기화 되지 않은 반복기

다음과 같이 반복기가 초기화되기 전에 반복기를 사용하려고 하면 어설션이 발생합니다.

```cpp
// iterator_debugging_2.cpp
// compile by using: /EHsc /MDd
#include <string>
using namespace std;

int main() {
   string::iterator i1, i2;
   if (i1 == i2)
      ;
}
```

## <a name="incompatible-iterators"></a>호환 되지 않는 반복기

[for_each](../standard-library/algorithm-functions.md#for_each) 알고리즘에 대한 두 개의 반복기가 호환되지 않으므로 다음 코드 예제는 어설션을 발생시킵니다. 알고리즘은 알고리즘에 제공되는 반복기가 같은 컨테이너를 참조하는지 확인합니다.

```cpp
// iterator_debugging_3.cpp
// compile by using /EHsc /MDd
#include <algorithm>
#include <vector>
using namespace std;

int main()
{
    vector<int> v1 {10, 20};
    vector<int> v2 {10, 20};

    // The next line asserts because v1 and v2 are
    // incompatible.
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );
}
```

이 예제에서는 함수 대신 람다 식 `[] (int& elem) { elem *= 2; }`를 사용합니다. 이 선택은 비슷한 함수가 같은 실패를 일으키는 어설션 실패와 아무런 관련이 없지만 람다는 간단한 함수 개체 작업을 수행하는 매우 유용한 방법입니다. 람다 식에 대 한 자세한 내용은 [람다 식](../cpp/lambda-expressions-in-cpp.md)을 참조 하세요.

## <a name="iterators-going-out-of-scope"></a>범위 밖으로 이동 하는 반복기

또한 디버그 반복기 검사를 수행 하면 루프 **`for`** 범위가 종료 될 때 루프에서 선언 된 반복기 변수가 범위를 벗어났습니다 **`for`** .

```cpp
// iterator_debugging_4.cpp
// compile by using: /EHsc /MDd
#include <vector>
#include <iostream>
int main() {
   std::vector<int> v {10, 15, 20};

   for (std::vector<int>::iterator i = v.begin(); i != v.end(); ++i)
      ;   // do nothing
   --i;   // C2065
}
```

## <a name="destructors-for-debug-iterators"></a>디버그 반복기 용 소멸자

디버그 반복기에 non-trivial 소멸자가 있습니다. 소멸자가 실행 되지 않지만 개체의 메모리가 해제 된 경우 액세스 위반 및 데이터 손상이 발생할 수 있습니다. 다음 예제를 고려해 보세요.

```cpp
// iterator_debugging_5.cpp
// compile by using: /EHsc /MDd
#include <vector>
struct base {
   // TO FIX: uncomment the next line
   // virtual ~base() {}
};

struct derived : base {
   std::vector<int>::iterator m_iter;
   derived( std::vector<int>::iterator iter ) : m_iter( iter ) {}
   ~derived() {}
};

int main() {
   std::vector<int> vect( 10 );
   base * pb = new derived( vect.begin() );
   delete pb;  // doesn't call ~derived()
   // access violation
}
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리 개요](../standard-library/cpp-standard-library-overview.md)
