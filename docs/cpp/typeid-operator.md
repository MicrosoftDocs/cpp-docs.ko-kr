---
description: '자세한 정보: typeid 연산자'
title: typeid 연산자
ms.date: 10/04/2019
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
ms.openlocfilehash: 8e036cbdcc540eca224b97b09d174362c454da6e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145862"
---
# <a name="typeid-operator"></a>typeid 연산자

## <a name="syntax"></a>구문

```
typeid(type-id)
typeid(expression)
```

## <a name="remarks"></a>설명

**`typeid`** 연산자를 사용 하면 런타임에 개체의 형식을 확인할 수 있습니다.

의 결과는 **`typeid`** `const type_info&` 입니다. 값은 사용 되는 `type_info` 폼에 따라 *형식 id* 또는 *식* 의 형식을 나타내는 개체에 대 한 참조입니다 **`typeid`** . 자세한 내용은 [Type_info 클래스](../cpp/type-info-class.md)를 참조 하세요.

**`typeid`** 연산자는 관리 되는 형식 (추상 선언 자 또는 인스턴스)에서 작동 하지 않습니다. 지정 된 형식의를 가져오는 방법에 대 한 자세한 내용은 <xref:System.Type> [typeid](../extensions/typeid-cpp-component-extensions.md)를 참조 하세요.

**`typeid`** 연산자는 다형 클래스 형식의 l-value에 적용 될 때 런타임 검사를 수행 합니다. 여기서 개체의 실제 형식은 제공 된 정적 정보로 확인할 수 없습니다. 다음과 같은 경우가 여기에 해당합니다.

- 클래스에 대한 참조

- 포인터, 역참조 `*`

- 첨자 포인터 ( `[ ]` )입니다. 다형 형식에 대 한 포인터와 함께 첨자를 사용 하는 것은 안전 하지 않습니다.

*식이* 기본 클래스 형식을 가리키지만 개체가 실제로 해당 기본 클래스에서 파생 된 형식인 경우 `type_info` 파생 클래스에 대 한 참조가 결과입니다. *식은* 다형 형식 (가상 함수가 포함 된 클래스)을 가리켜야 합니다. 그렇지 않으면 `type_info` *식* 에서 참조 되는 정적 클래스에 대 한 결과입니다. 또한 포인터가 사용 되는 개체를 가리키는 포인터를 역참조 해야 합니다. 포인터를 역참조 하지 않을 경우 결과는 `type_info` 포인터가 가리키는 것이 아니라 포인터에 대 한입니다. 예를 들어:

```cpp
// expre_typeid_Operator.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <typeinfo>

class Base {
public:
   virtual void vvfunc() {}
};

class Derived : public Base {};

using namespace std;
int main() {
   Derived* pd = new Derived;
   Base* pb = pd;
   cout << typeid( pb ).name() << endl;   //prints "class Base *"
   cout << typeid( *pb ).name() << endl;   //prints "class Derived"
   cout << typeid( pd ).name() << endl;   //prints "class Derived *"
   cout << typeid( *pd ).name() << endl;   //prints "class Derived"
   delete pd;
}
```

*식이* 포인터를 역참조 하 고 포인터의 값이 0 이면 **`typeid`** [bad_typeid 예외가](../cpp/bad-typeid-exception.md)throw 됩니다. 포인터가 유효한 개체를 가리키지 않는 경우 `__non_rtti_object` 예외가 throw 됩니다. 개체가 유효 하지 않기 때문에 오류를 트리거한 RTTI를 분석 하려는 시도를 나타냅니다. 예를 들어 잘못 된 포인터 이거나 코드를 [/gr](../build/reference/gr-enable-run-time-type-information.md)로 컴파일하지 않은 경우입니다.

*식이* 포인터가 아닌 개체의 기본 클래스에 대 한 참조가 아닌 경우 결과는 `type_info` *식* 의 정적 형식을 나타내는 참조입니다. 식의 *정적 형식은* 컴파일 타임에 알려진 식의 형식을 참조 합니다. 식의 정적 형식을 평가할 때 식의 의미 체계가 무시됩니다. 또한 식의 정적 형식을 결정할 때 가능할 경우 참조가 무시됩니다.

```cpp
// expre_typeid_Operator_2.cpp
#include <typeinfo>

int main()
{
   typeid(int) == typeid(int&); // evaluates to true
}
```

**`typeid`** 템플릿 매개 변수의 형식을 결정 하는 데에도 사용할 수 있습니다.

```cpp
// expre_typeid_Operator_3.cpp
// compile with: /c
#include <typeinfo>
template < typename T >
T max( T arg1, T arg2 ) {
   cout << typeid( T ).name() << "s compared." << endl;
   return ( arg1 > arg2 ? arg1 : arg2 );
}
```

## <a name="see-also"></a>참고 항목

[런타임 형식 정보](../cpp/run-time-type-information.md)\
[키워드](../cpp/keywords-cpp.md)
