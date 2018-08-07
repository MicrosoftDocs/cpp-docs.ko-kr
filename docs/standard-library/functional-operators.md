---
title: '&lt;functional&gt; 연산자 | Microsoft 문서'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
dev_langs:
- C++
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b9bc37213ed2e5690f85fca738d44e6eecfaa8c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962051"
---
# <a name="ltfunctionalgt-operators"></a>&lt;functional&gt; 연산자

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  operator==

호출 가능 개체가 비어 있는지 테스트합니다.

```cpp
template <class Fty>
bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
bool operator==(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>매개 변수

*Fty* 래핑할 함수 형식입니다.

*f* 함수 개체

*npc* null 포인터입니다.

### <a name="remarks"></a>설명

연산자는 둘 다 `function` 개체에 대한 참조인 인수와 null 포인터 상수인 인수를 사용합니다. `function` 개체가 비어 있는 경우에만 둘 다 true를 반환합니다.

### <a name="example"></a>예

```cpp
// std__functional__operator_eq.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
{
    return (-val);
}

int main()
{
    std::function<int(int)> fn0;
    std::cout << std::boolalpha << "empty == "
        << (fn0 == 0) << std::endl;

    std::function<int(int)> fn1(neg);
    std::cout << std::boolalpha << "empty == "
        << (fn1 == 0) << std::endl;

    return (0);
}

```

```Output
empty == true
empty == false
```

## <a name="op_neq"></a>  operator!=

호출 가능 개체가 비어 있지 않은지 테스트합니다.

```cpp
template <class Fty>
bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
bool operator!=(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>매개 변수

*Fty* 래핑할 함수 형식입니다.

*f* 함수 개체

*npc* null 포인터입니다.

### <a name="remarks"></a>설명

연산자는 둘 다 `function` 개체에 대한 참조인 인수와 null 포인터 상수인 인수를 사용합니다. `function` 개체가 비어 있지 않은 경우에만 둘 다 true를 반환합니다.

### <a name="example"></a>예

```cpp
// std__functional__operator_ne.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0;
    std::cout << std::boolalpha << "not empty == "
        << (fn0 != 0) << std::endl;

    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "not empty == "
        << (fn1 != 0) << std::endl;

    return (0);
    }

```

```Output
not empty == false
not empty == true
```

## <a name="see-also"></a>참고자료

[\<functional>](../standard-library/functional.md)<br/>
