---
description: '자세히 알아보기: &lt; memory &gt; operators'
title: '&lt;memory&gt; 연산자'
ms.date: 11/04/2016
f1_keywords:
- memory/std::operator!=
- memory/std::operator>
- memory/std::operator>=
- memory/std::operator<
- memory/std::operator<=
- memory/std::operator<<
- memory/std::operator==
ms.assetid: 257e3ba9-c4c2-4ae8-9b11-b156ba9c28de
ms.openlocfilehash: cbf52aa2af13a0eae241444d88e0eeabe7efe47b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183947"
---
# <a name="ltmemorygt-operators"></a>&lt;memory&gt; 연산자

## <a name="operator"></a><a name="op_neq"></a> 연산자! =

개체 간의 같지 않음을 테스트합니다.

```cpp
template <class Type, class Other>
bool operator!=(
    const allocator<Type>& left,
    const allocator<Other>& right) throw();

template <class T, class Del1, class U, class Del2>
bool operator!=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator!=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
같지 않음을 테스트할 개체 중 하나입니다.

*오른쪽*\
같지 않음을 테스트할 개체 중 하나입니다.

*Ty1*\
왼쪽 공유 포인터로 제어되는 형식입니다.

*Ty2*\
오른쪽 공유 포인터로 제어되는 형식입니다.

### <a name="return-value"></a>반환 값

**`true`** 개체가 같지 않으면이 고, 그렇지 않으면입니다. **`false`** 개체가 같으면이 고,

### <a name="remarks"></a>설명

첫 번째 템플릿 연산자는 false를 반환합니다. (모든 기본 할당자가 같습니다.)

두 번째 및 세 번째 템플릿 연산자는 `!(left == right)`을 반환합니다.

### <a name="example"></a>예제

```cpp
// memory_op_me.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<double> Alloc;
   vector <char>:: allocator_type v1Alloc;

   if ( Alloc != v1Alloc )
      cout << "The allocator objects Alloc & v1Alloc not are equal."
           << endl;
   else
      cout << "The allocator objects Alloc & v1Alloc are equal."
           << endl;
}
```

```Output
The allocator objects Alloc & v1Alloc are equal.
```

### <a name="example"></a>예제

```cpp
// std__memory__operator_ne.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(0));
    std::shared_ptr<int> sp1(new int(0));

    std::cout << "sp0 != sp0 == " << std::boolalpha
        << (sp0 != sp0) << std::endl;
    std::cout << "sp0 != sp1 == " << std::boolalpha
        << (sp0 != sp1) << std::endl;

    return (0);
    }
```

```Output
sp0 != sp0 == false
sp0 != sp1 == true
```

## <a name="operator"></a><a name="op_eq_eq"></a> 연산자 = =

개체 간의 같음을 테스트합니다.

```cpp
template <class Type, class Other>
bool operator==(
    const allocator<Type>& left,
    const allocator<Other>& right) throw();

template <class Ty1, class Del1, class Ty2, class Del2>
bool operator==(
    const unique_ptr<Ty1, Del1>& left,
    const unique_ptr<Ty2, Del2>& right);

template <class Ty1, class Ty2>
bool operator==(
    const shared_ptr<Ty1>& left;,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
같은지 여부를 테스트할 개체 중 하나입니다.

*오른쪽*\
같은지 여부를 테스트할 개체 중 하나입니다.

*Ty1*\
왼쪽 공유 포인터로 제어되는 형식입니다.

*Ty2*\
오른쪽 공유 포인터로 제어되는 형식입니다.

### <a name="return-value"></a>반환 값

**`true`** 개체가 같으면이 고, 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

첫 번째 템플릿 연산자는 true를 반환합니다. (모든 기본 할당자가 같습니다.)

두 번째 및 세 번째 템플릿 연산자는 `left.get() ==  right.get()`을 반환합니다.

### <a name="example"></a>예제

```cpp
// memory_op_eq.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<char> Alloc;
   vector <int>:: allocator_type v1Alloc;

   allocator<char> cAlloc(Alloc);
   allocator<int> cv1Alloc(v1Alloc);

   if ( cv1Alloc == v1Alloc )
      cout << "The allocator objects cv1Alloc & v1Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cv1Alloc & v1Alloc are not equal."
           << endl;

   if ( cAlloc == Alloc )
      cout << "The allocator objects cAlloc & Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cAlloc & Alloc are not equal."
           << endl;
}
```

```Output
The allocator objects cv1Alloc & v1Alloc are equal.
The allocator objects cAlloc & Alloc are equal.
```

### <a name="example"></a>예제

```cpp
// std__memory__operator_eq.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(0));
    std::shared_ptr<int> sp1(new int(0));

    std::cout << "sp0 == sp0 == " << std::boolalpha
        << (sp0 == sp0) << std::endl;
    std::cout << "sp0 == sp1 == " << std::boolalpha
        << (sp0 == sp1) << std::endl;

    return (0);
    }
```

```Output
sp0 == sp0 == true
sp0 == sp1 == false
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a> 연산자&gt;=

한 개체가 두 번째 개체보다 크거나 같은지 테스트합니다.

```cpp
template <class T, class Del1, class U, class Del2>
bool operator>=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U, Del2>& right);

template <class Ty1, class Ty2>
bool operator>=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
비교할 개체 중 하나입니다.

*오른쪽*\
비교할 개체 중 하나입니다.

*Ty1*\
왼쪽 공유 포인터로 제어되는 형식입니다.

*Ty2*\
오른쪽 공유 포인터로 제어되는 형식입니다.

### <a name="remarks"></a>설명

템플릿 연산자는 `left.get() >= right.get()`을 반환합니다.

## <a name="operatorlt"></a><a name="op_lt"></a> 연산자&lt;

한 개체가 두 번째 개체보다 작은지 테스트합니다.

```cpp
template <class T, class Del1, class U, class Del2>
bool operator<(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator<(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
비교할 개체 중 하나입니다.

*오른쪽*\
비교할 개체 중 하나입니다.

*Ty1*\
왼쪽 포인터에 의해 제어되는 형식입니다.

*Ty2*\
오른쪽 포인터에 의해 제어되는 형식입니다.

## <a name="operatorlt"></a><a name="op_lt_eq"></a> 연산자&lt;=

한 개체가 두 번째 개체보다 작거나 같은지 테스트합니다.

```cpp
template <class T, class Del1, class U, class Del2>
bool operator<=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator<=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
비교할 개체 중 하나입니다.

*오른쪽*\
비교할 개체 중 하나입니다.

*Ty1*\
왼쪽 공유 포인터로 제어되는 형식입니다.

*Ty2*\
오른쪽 공유 포인터로 제어되는 형식입니다.

### <a name="remarks"></a>설명

템플릿 연산자는 `left.get() <= right.get()`을 반환합니다.

## <a name="operatorgt"></a><a name="op_gt"></a> 연산자&gt;

한 개체가 두 번째 개체보다 큰지 테스트합니다.

```cpp
template <class Ty1, class Del1, class Ty2, class Del2>
bool operator>(
    const unique_ptr<Ty1, Del1>& left,
    const unique_ptr<Ty2&, Del2gt;& right);

template <class Ty1, class Ty2>
bool operator>(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
비교할 개체 중 하나입니다.

*오른쪽*\
비교할 개체 중 하나입니다.

*Ty1*\
왼쪽 공유 포인터로 제어되는 형식입니다.

*Ty2*\
오른쪽 공유 포인터로 제어되는 형식입니다.

## <a name="operatorltlt"></a><a name="op_lt_lt"></a> 연산자&lt;&lt;

공유 포인터를 스트림에 씁니다.

```cpp
template <class Elem, class Tr, class Ty>
std::basic_ostream<Elem, Tr>& operator<<(std::basic_ostream<Elem, Tr>& out,
    shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>매개 변수

*E*\
스트림 요소의 형식입니다.

*비교한*\
스트림 요소 특성의 형식입니다.

*Ty*\
공유 포인터에 의해 제어되는 형식입니다.

*제한이*\
출력 스트림입니다.

*sp-2*\
공유 포인터입니다.

### <a name="remarks"></a>설명

템플릿 함수가 `out << sp.get()`을 반환합니다.

### <a name="example"></a>예제

```cpp
// std__memory__operator_sl.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "sp0 == " << sp0 << " (varies)" << std::endl;

    return (0);
    }
```

```Output
sp0 == 3f3040 (varies)
```
