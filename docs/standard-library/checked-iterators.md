---
title: Checked Iterators
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL_THROWS
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- iterators, checked
- checked iterators
ms.assetid: cfc87df8-e3d9-403b-ab78-e9483247d940
ms.openlocfilehash: 2327638208f30908cd3429ae656ce569f5821195
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684905"
---
# <a name="checked-iterators"></a>Checked Iterators

확인된 반복기는 컨테이너 경계를 덮어쓰지 않습니다. 확인된 반복기는 릴리스 빌드 및 디버그 빌드에 모두 적용됩니다. 디버그 모드에서 컴파일할 때 디버그 반복기를 사용하는 방법에 대한 자세한 내용은 [Debug Iterator Support](../standard-library/debug-iterator-support.md)(디버그 반복기 지원)를 참조하세요.

## <a name="remarks"></a>설명

확인된 반복기에서 생성한 경고를 사용하지 않도록 설정하는 방법에 대한 자세한 내용은 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)를 참조하세요.

[ \_ 반복기 \_ 디버그 \_ 수준](../standard-library/iterator-debug-level.md) 전처리기 매크로를 사용 하 여 확인 된 반복기 기능을 사용 하거나 사용 하지 않도록 설정할 수 있습니다. _ITERATOR_DEBUG_LEVEL 1 또는 2로 정의 된 경우 반복기를 안전 하지 않은 방식으로 사용 하면 런타임 오류가 발생 하 고 프로그램이 종료 됩니다. 0으로 정의한 경우 확인된 반복기를 사용하지 않도록 설정됩니다. 기본적으로 _ITERATOR_DEBUG_LEVEL의 값은 릴리스 빌드의 경우 0, 디버그 빌드의 경우 2입니다.

> [!IMPORTANT]
> 이전 설명서와 소스 코드에서 [_SECURE_SCL](../standard-library/secure-scl.md) 매크로를 참조할 수 있습니다. _ITERATOR_DEBUG_LEVEL를 사용 하 여 _SECURE_SCL를 제어 합니다. 자세한 내용은 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)을 참조하세요.

_ITERATOR_DEBUG_LEVEL가 1 또는 2로 정의 된 경우 다음 반복기 검사가 수행 됩니다.

- 모든 표준 반복기(예: [vector::iterator](../standard-library/vector-class.md#iterator))를 확인합니다.

- 출력 반복기가 확인된 반복기인 경우 표준 라이브러리 함수(예: [std::copy](../standard-library/algorithm-functions.md#copy))에 대한 호출에서 확인된 동작을 가져옵니다.

- 출력 반복기가 확인되지 않은 반복기인 경우 표준 라이브러리 함수에 대한 호출에서 컴파일러 경고가 발생합니다.

- 다음 함수에서는 컨테이너 경계를 넘어 액세스할 경우 런타임 오류가 발생합니다.

:::row:::
   :::column span="":::
      &emsp;&emsp;[`basic_string::operator[]`](../standard-library/basic-string-class.md#op_at)\
      &emsp;&emsp;[`bitset::operator[]`](../standard-library/bitset-class.md#op_at)\
      &emsp;&emsp;[`deque::back`](../standard-library/deque-class.md#back)\
      &emsp;&emsp;[`deque::front`](../standard-library/deque-class.md#front)
   :::column-end:::
   :::column span="":::
      [`deque::operator[]`](../standard-library/deque-class.md#op_at)\
      [`list::back`](../standard-library/list-class.md#back)\
      [`list::front`](../standard-library/list-class.md#front)\
      [`queue::back`](../standard-library/queue-class.md#back)
   :::column-end:::
   :::column span="":::
      [`queue::front`](../standard-library/queue-class.md#front)\
      [`vector::back`](../standard-library/vector-class.md#back)\
      [`vector::front`](../standard-library/vector-class.md#front)\
      [`vector::operator[]`](../standard-library/vector-class.md#op_at)
   :::column-end:::
:::row-end:::

_ITERATOR_DEBUG_LEVEL는 0으로 정의 됩니다.

- 모든 표준 반복기가 확인되지 않습니다. 반복기가 컨테이너 경계 밖으로 이동할 수 있으며 이는 정의되지 않은 동작으로 이어집니다.

- 출력 반복기가 확인된 반복기인 경우 표준 라이브러리 함수(예: `std::copy`)에 대한 호출에서 확인된 동작을 가져옵니다.

- 출력 반복기가 확인되지 않은 반복기인 경우 표준 라이브러리 함수에 대한 호출에서 확인되지 않은 동작을 가져옵니다.

컨테이너 경계를 넘어 이동하려고 시도하는 경우 확인된 반복기는 `invalid_parameter_handler`를 호출하는 반복기를 참조합니다. `invalid_parameter_handler`에 대한 자세한 내용은 [매개 변수 유효성 검사](../c-runtime-library/parameter-validation.md)를 참조하세요.

확인된 반복기를 지원하는 반복기 어댑터는 [checked_array_iterator 클래스](../standard-library/checked-array-iterator-class.md)와 [unchecked_array_iterator 클래스](../standard-library/unchecked-array-iterator-class.md)입니다.

## <a name="examples"></a>예제

1 또는 2로 설정 된 _ITERATOR_DEBUG_LEVEL를 사용 하 여 컴파일하면 특정 클래스의 인덱싱 연산자를 사용 하 여 컨테이너 경계 밖에 있는 요소에 액세스 하려고 하면 런타임 오류가 발생 합니다.

```cpp
// checked_iterators_1.cpp
// cl.exe /Zi /MDd /EHsc /W4

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>
#include <iostream>

using namespace std;

int main()
{
   vector<int> v;
   v.push_back(67);

   int i = v[0];
   cout << i << endl;

   i = v[1]; //triggers invalid parameter handler
}
```

이 프로그램은 "67"을 인쇄한 후 실패에 대한 자세한 정보가 들어 있는 어설션 실패 대화 상자를 팝업으로 표시합니다.

마찬가지로, 1 또는 2로 설정 된 _ITERATOR_DEBUG_LEVEL를 사용 하 여 컴파일할 경우 `front` `back` 컨테이너가 비어 있을 때 컨테이너 클래스에서 또는를 사용 하 여 요소에 액세스 하려고 하면 런타임 오류가 발생 합니다.

```cpp
// checked_iterators_2.cpp
// cl.exe /Zi /MDd /EHsc /W4
#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>
#include <iostream>

using namespace std;

int main()
{
   vector<int> v;

   int& i = v.front(); // triggers invalid parameter handler
}
```

이 프로그램은 실패에 대한 자세한 정보가 들어 있는 어설션 실패 대화 상자를 팝업으로 표시합니다.

다음 코드에는 다양한 반복기 사용 사례 시나리오에 대한 설명과 각각에 대한 주석이 나와 있습니다. 기본적으로 _ITERATOR_DEBUG_LEVEL는 디버그 빌드에서 2로 설정 되 고 정품 빌드에서는 0으로 설정 됩니다.

```cpp
// checked_iterators_3.cpp
// cl.exe /MTd /EHsc /W4

#include <algorithm>
#include <array>
#include <iostream>
#include <iterator>
#include <numeric>
#include <string>
#include <vector>

using namespace std;

template <typename C>
void print(const string& s, const C& c)
{
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    vector<int> v(16);
    iota(v.begin(), v.end(), 0);
    print("v: ", v);

    // OK: vector::iterator is checked in debug mode
    // (i.e. an overrun causes a debug assertion)
    vector<int> v2(16);
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });
    print("v2: ", v2);

    // OK: back_insert_iterator is marked as checked in debug mode
    // (i.e. an overrun is impossible)
    vector<int> v3;
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });
    print("v3: ", v3);

    // OK: array::iterator is checked in debug mode
    // (i.e. an overrun causes a debug assertion)
    array<int, 16> a4;
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });
    print("a4: ", a4);

    // OK: Raw arrays are checked in debug mode
    // (an overrun causes a debug assertion)
    // NOTE: This applies only when raw arrays are given to C++ Standard Library algorithms!
    int a5[16];
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });
    print("a5: ", a5);

    // WARNING C4996: Pointers cannot be checked in debug mode
    // (an overrun causes undefined behavior)
    int a6[16];
    int * p6 = a6;
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });
    print("a6: ", a6);

    // OK: stdext::checked_array_iterator is checked in debug mode
    // (an overrun causes a debug assertion)
    int a7[16];
    int * p7 = a7;
    transform(v.begin(), v.end(), stdext::make_checked_array_iterator(p7, 16), [](int n) { return n * 7; });
    print("a7: ", a7);

    // WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode
    // (it performs no checking, so an overrun causes undefined behavior)
    int a8[16];
    int * p8 = a8;
    transform(v.begin(), v.end(), stdext::make_unchecked_array_iterator(p8), [](int n) { return n * 8; });
    print("a8: ", a8);
}
```

`cl.exe /EHsc /W4 /MTd checked_iterators_3.cpp`를 사용하여 이 코드를 컴파일할 때 컴파일러가 경고를 내보내지만, 다음과 같이 실행 파일로 오류 없이 컴파일됩니다.

```Output
algorithm(1026) : warning C4996: 'std::_Transform1': Function call with parameters
that may be unsafe - this call relies on the caller to check that the passed values
are correct. To disable this warning, use -D_SCL_SECURE_NO_WARNINGS. See documentation
on how to use Visual C++ 'Checked Iterators'
```

명령줄에서 실행하는 경우 실행 파일이 다음 출력을 생성합니다.

```Output
v: 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
v2: 0 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30
v3: 0 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45
a4: 0 4 8 12 16 20 24 28 32 36 40 44 48 52 56 60
a5: 0 5 10 15 20 25 30 35 40 45 50 55 60 65 70 75
a6: 0 6 12 18 24 30 36 42 48 54 60 66 72 78 84 90
a7: 0 7 14 21 28 35 42 49 56 63 70 77 84 91 98 105
a8: 0 8 16 24 32 40 48 56 64 72 80 88 96 104 112 120
```

## <a name="see-also"></a>추가 정보

[C + + 표준 라이브러리 개요](../standard-library/cpp-standard-library-overview.md)\
[디버그 반복기 지원](../standard-library/debug-iterator-support.md)
