---
description: '자세히 알아보기: binder2nd 클래스'
title: binder2nd 클래스
ms.date: 02/21/2019
f1_keywords:
- functional/std::binder2nd
helpviewer_keywords:
- binder2nd class
ms.assetid: b2a9c1d1-dfc4-4ca9-a10e-ae84e195a62d
ms.openlocfilehash: a3c76fcea22045ee7e723ad3ad51390c39f602ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325494"
---
# <a name="binder2nd-class"></a>binder2nd 클래스

이항 함수의 두 번째 인수를 지정 된 값에 바인딩하여 이항 함수 개체를 단항 함수 개체로 변환 하는 생성자를 제공 하는 클래스 템플릿입니다. C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다.

## <a name="syntax"></a>구문

```cpp
template <class Operation>
class binder2nd
    : public unaryFunction <typename Operation::first_argument_type,
    typename Operation::result_type>
{
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder2nd(
        const Operation& func,
        const typename Operation::second_argument_type& right);

    result_type operator()(const argument_type& left) const;
    result_type operator()(argument_type& left) const;
};
```

### <a name="parameters"></a>매개 변수

*func*\
단항 함수 개체로 변환할 이항 함수 개체입니다.

*오른쪽*\
이항 함수 개체의 두 번째 인수가 바인딩되는 값입니다.

*비어*\
수정된 이진 개체를 두 번째 인수의 고정 값과 비교하는 인수의 값입니다.

## <a name="return-value"></a>반환 값

이항 함수 개체의 두 번째 인수를 값 *오른쪽* 에 바인딩하여 생성 되는 단항 함수 개체입니다.

## <a name="remarks"></a>설명

클래스 템플릿은에서 이진 함수 개체 *func* 의 복사본을 저장 `op` 하 고의 복사본을에 저장  합니다 `value` . 반환 하는 멤버 함수 `operator()` 를 정의 `op(left, value)` 합니다.

*Func* 가 형식의 개체이 `Operation` 고 c가 상수인 경우 [bind2nd](../standard-library/functional-functions.md#bind2nd) `(func, c)` 는 `binder2nd` 클래스 생성자 `binder2nd<Operation>(func, c)` 와 같으며 더 편리 합니다.

## <a name="example"></a>예제

```cpp
// functional_binder2nd.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(),
        binder2nd<greater<int> >(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    // Compare using binder1st fixing 1st argument:
    // count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(),
        binder1st<greater<int> >(greater<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
```
