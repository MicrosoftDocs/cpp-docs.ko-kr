---
title: unary_negate 클래스
ms.date: 02/21/2019
f1_keywords:
- functional/std::unary_negate
helpviewer_keywords:
- unary_negate class
ms.assetid: e3b86eec-3205-49b9-ab83-f55225af4e0c
ms.openlocfilehash: 2d9f0bedd9e541e65f04ac20375f16f41413cf03
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684430"
---
# <a name="unary_negate-class"></a>unary_negate 클래스

지정 된 단항 함수의 반환 값을 부정 하는 멤버 함수를 제공 하는 클래스 템플릿입니다. [Not_fn](functional-functions.md#not_fn)를 사용 하 여 c + + 17에서 사용 되지 않습니다.

## <a name="syntax"></a>구문

```cpp
template <class Predicate>
class unary_negate
    : public unaryFunction<typename Predicate::argument_type, bool>
{
    explicit unary_negate(const Predicate& Func);
    bool operator()(const typename Predicate::argument_type& left) const;
};
```

### <a name="parameters"></a>매개 변수

*Func* \
부정할 단항 함수입니다.

*왼쪽* \
부정할 단항 함수의 피연산자입니다.

## <a name="return-value"></a>반환 값

단항 함수의 부정

## <a name="remarks"></a>주의

클래스 템플릿은 *\_Func*단항 함수 개체의 복사본을 저장 합니다. @No__t_1 반환 하는 것 처럼 `operator()` 멤버 함수를 정의 합니다.

`unary_negate`의 생성자는 직접 사용되는 경우가 거의 없습니다. 도우미 함수 [not1](../standard-library/functional-functions.md#not1)을 사용하면 **unary_negator** 어댑터 조건자를 보다 쉽게 선언하고 사용할 수 있습니다.

## <a name="example"></a>예제

```cpp
// functional_unary_negate.cpp
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
    for (i = 0; i <= 7; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    // Count the elements greater than 10
    result1 = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    vector<int>::iterator::difference_type result2;
    // Use the negator to count the elements less than or equal to 10
    result2 = count_if(v1.begin(), v1.end(),
        unary_negate<binder2nd <greater<int> > >(bind2nd(greater<int>(),10)));

    // The following helper function not1 also works for the above line
    // not1(bind2nd(greater<int>(), 10)));

    cout << "The number of elements in v1 not greater than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 30 35 )
The number of elements in v1 greater than 10 is: 5.
The number of elements in v1 not greater than 10 is: 3.
```
