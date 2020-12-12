---
description: Static_cast 연산자에 대해 자세히 알아보세요.
title: static_cast 연산자
ms.date: 11/04/2016
f1_keywords:
- static_cast_cpp
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
ms.openlocfilehash: 7d76b4e21adea6561d7d6822871631c242aaf9c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317963"
---
# <a name="static_cast-operator"></a>static_cast 연산자

식에  있는 형식만 기반으로 식을 *형식 id* 형식으로 변환 합니다.

## <a name="syntax"></a>구문

```
static_cast <type-id> ( expression )
```

## <a name="remarks"></a>설명

표준 C++에서는 변환의 안전성을 보장하기 위해 런타임 형식 검사가 수행되지 않습니다. C++/CX에서는 컴파일 시간 및 런타임 검사가 수행됩니다. 자세한 내용은 [캐스팅](casting.md)에 정의된 인터페이스의 private C++ 관련 구현입니다.

**`static_cast`** 연산자는 기본 클래스에 대 한 포인터를 파생 클래스에 대 한 포인터로 변환 하는 등의 작업에 사용할 수 있습니다. 이러한 변환이 항상 안전한 것은 아닙니다.

일반적으로 **`static_cast`** 열거형과 같은 숫자 데이터 형식을 정수 또는 정수를 부동으로 변환 하 고 변환에 관련 된 데이터 형식을 지정할 때 사용 합니다. **`static_cast`****`dynamic_cast`** **`static_cast`** 는에서 런타임 형식 검사를 수행 하지 않으므로 변환은 변환 만큼 안전 하지 않습니다 **`dynamic_cast`** . **`dynamic_cast`** 모호한 포인터에 대 한는 실패 하는 반면,은 **`static_cast`** 잘못 된 것으로 반환 되 면 위험할 수 있습니다. **`dynamic_cast`** 변환은 더 안전 하지만 **`dynamic_cast`** 포인터나 참조 에서만 작동 하며 런타임 형식 검사는 오버 헤드입니다. 자세한 내용은 [Dynamic_cast 연산자](../cpp/dynamic-cast-operator.md)를 참조 하세요.

다음에 나오는 예제에서 `D* pd2 = static_cast<D*>(pb);` 줄은 `D`에서 `B`에 있지 않은 필드와 메서드를 가질 수 있기 때문에 안전하지 않습니다. 그러나 `B* pb2 = static_cast<B*>(pd);`는 항상 모든 `D`를 포함하기 때문에 `B` 줄의 변환은 안전합니다.

```cpp
// static_cast_Operator.cpp
// compile with: /LD
class B {};

class D : public B {};

void f(B* pb, D* pd) {
   D* pd2 = static_cast<D*>(pb);   // Not safe, D can have fields
                                   // and methods that are not in B.

   B* pb2 = static_cast<B*>(pd);   // Safe conversion, D always
                                   // contains all of B.
}
```

[Dynamic_cast](../cpp/dynamic-cast-operator.md)와는 달리의 변환에 대해 런타임 검사가 수행 되지 않습니다 **`static_cast`** `pb` . `pb`가 가리키는 개체는 유형 `D`의 개체가 아닐 수 있으며, 이 경우 `*pd2`를 사용하는 것은 매우 위험합니다. 예를 들어 `D` 클래스가 아닌 `B` 클래스의 멤버인 함수를 호출하면 액세스 위반이 발생할 수 있습니다.

**`dynamic_cast`** 및 **`static_cast`** 연산자는 클래스 계층 구조 전체에서 포인터를 이동 합니다. 그러나는 **`static_cast`** cast 문에 제공 된 정보에만 의존 하므로 안전 하지 않을 수 있습니다. 예를 들어:

```cpp
// static_cast_Operator_2.cpp
// compile with: /LD /GR
class B {
public:
   virtual void Test(){}
};
class D : public B {};

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);
   D* pd2 = static_cast<D*>(pb);
}
```

`pb`가 `D` 형식의 개체를 가리킬 경우 `pd1` 및 `pd2`는 동일한 값을 얻습니다. 또한 `pb == 0`일 경우 같은 값을 얻습니다.

가 `pb` 전체 클래스가 아닌 형식의 개체를 가리키는 경우 `B` `D` **`dynamic_cast`** 는 0을 반환할 만큼 충분 합니다. 그러나는 **`static_cast`** 형식의 개체를 가리키는 프로그래머의 어설션을 사용 하 여 `pb` `D` 해당 하는 개체에 대 한 포인터를 반환 `D` 합니다.

따라서는 **`static_cast`** 암시적 변환의 역함수를 수행할 수 있으며,이 경우 결과가 정의 되지 않습니다. 변환 결과가 안전한 지 확인 하는 것은 프로그래머에 게 남아 **`static_cast`** 있습니다.

이 동작은 클래스 형식 이외의 형식에도 적용됩니다. 예를 들어,를 사용 하 여 **`static_cast`** int에서로 변환할 수 있습니다 **`char`** . 그러나 결과에는 **`char`** 전체 값을 저장할 수 있는 충분 한 비트가 없을 수 있습니다 **`int`** . 다시, 변환 결과가 안전한 지 확인 하는 것은 프로그래머에 게 남아 있습니다 **`static_cast`** .

**`static_cast`** 연산자를 사용 하 여 표준 변환 및 사용자 정의 변환을 비롯 한 암시적 변환을 수행할 수도 있습니다. 예를 들어:

```cpp
// static_cast_Operator_3.cpp
// compile with: /LD /GR
typedef unsigned char BYTE;

void f() {
   char ch;
   int i = 65;
   float f = 2.5;
   double dbl;

   ch = static_cast<char>(i);   // int to char
   dbl = static_cast<double>(f);   // float to double
   i = static_cast<BYTE>(ch);
}
```

**`static_cast`** 연산자는 정수 계열 값을 열거형 형식으로 명시적으로 변환할 수 있습니다. 정수 계열 형식의 값이 열거형 값 범위에 속하지 않으면 결과 열거형 값이 정의되지 않습니다.

**`static_cast`** 연산자는 null 포인터 값을 대상 형식의 null 포인터 값으로 변환 합니다.

모든 식은 연산자에 의해 명시적으로 void 형식으로 변환 될 수 있습니다 **`static_cast`** . 대상 void 형식에는 선택적으로 **`const`** , 또는 특성이 포함 될 수 있습니다 **`volatile`** **`__unaligned`** .

**`static_cast`** 연산자는 **`const`** , **`volatile`** 또는 특성으로 캐스트할 수 없습니다 **`__unaligned`** . 이러한 특성을 제거 하는 방법에 대 한 자세한 내용은 [Const_cast 연산자](../cpp/const-cast-operator.md) 를 참조 하세요.

**C + +/CLI:** 재배치 가비지 수집기에서 확인 되지 않은 캐스트를 수행 하는 위험으로 인해가 제대로 작동 하는 것이 확실 한 경우의 사용은 **`static_cast`** 성능이 중요 한 코드에만 있어야 합니다. 릴리스 모드에서를 사용 해야 하 **`static_cast`** 는 경우 성공 여부를 확인 하려면 디버그 빌드에서 [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) 로 대체 합니다.

## <a name="see-also"></a>참고 항목

[캐스팅 연산자](../cpp/casting-operators.md)<br/>
[키워드](../cpp/keywords-cpp.md)
