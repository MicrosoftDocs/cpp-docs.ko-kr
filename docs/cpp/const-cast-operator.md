---
description: Const_cast 연산자에 대해 자세히 알아보세요.
title: const_cast 연산자
ms.date: 11/04/2016
f1_keywords:
- const_cast_cpp
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
ms.openlocfilehash: c0c08402450773368914facb719c4ddf97b7503d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344668"
---
# <a name="const_cast-operator"></a>const_cast 연산자

**`const`** **`volatile`** 클래스에서, 및 특성을 제거 합니다 **`__unaligned`** .

## <a name="syntax"></a>구문

```
const_cast <type-id> (expression)
```

## <a name="remarks"></a>설명

모든 개체 형식 또는 데이터 멤버에 대 한 포인터에 대 한 포인터는 **`const`** , 및 한정자를 제외 하 고 동일한 형식으로 명시적으로 변환 될 수 있습니다 **`volatile`** **`__unaligned`** . 포인터 및 참조의 경우 결과는 원래 개체를 참조합니다. 데이터 멤버에 대한 포인터의 경우 결과는 데이터 멤버에 대한 원래(캐스팅 해제) 포인터와 동일한 멤버를 참조합니다. 참조 개체의 형식에 따라 결과 포인터, 참조 또는 데이터 멤버에 대한 포인터를 통한 쓰기 작업으로 인해 정의되지 않은 동작이 발생할 수 있습니다.

연산자를 사용 **`const_cast`** 하 여 상수 변수의 상수 상태를 직접 재정의할 수는 없습니다.

**`const_cast`** 연산자는 null 포인터 값을 대상 형식의 null 포인터 값으로 변환 합니다.

## <a name="example"></a>예제

```cpp
// expre_const_cast_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CCTest {
public:
   void setNumber( int );
   void printNumber() const;
private:
   int number;
};

void CCTest::setNumber( int num ) { number = num; }

void CCTest::printNumber() const {
   cout << "\nBefore: " << number;
   const_cast< CCTest * >( this )->number--;
   cout << "\nAfter: " << number;
}

int main() {
   CCTest X;
   X.setNumber( 8 );
   X.printNumber();
}
```

을 포함 하는 줄에서 **`const_cast`** 포인터의 데이터 형식은 **`this`** `const CCTest *` 입니다. **`const_cast`** 연산자는 포인터의 데이터 형식을로 변경 하 여 **`this`** 멤버를 수정할 수 있도록 합니다 `CCTest *` `number` . 캐스팅은 그것이 표시되는 문의 나머지 부분에서만 지속됩니다.

## <a name="see-also"></a>참고 항목

[캐스팅 연산자](../cpp/casting-operators.md)<br/>
[키워드](../cpp/keywords-cpp.md)
