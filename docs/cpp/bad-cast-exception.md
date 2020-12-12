---
description: '자세한 정보: bad_cast 예외'
title: bad_cast 예외
ms.date: 10/04/2019
f1_keywords:
- bad_cast
- bad_cast_cpp
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
ms.openlocfilehash: 40408128bd1c90feff34e8ea1ce8bf7a3c0d56cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255693"
---
# <a name="bad_cast-exception"></a>bad_cast 예외

**Bad_cast** 예외는 **`dynamic_cast`** 참조 형식으로의 실패 한 캐스트의 결과로 연산자에 의해 throw 됩니다.

## <a name="syntax"></a>구문

```
catch (bad_cast)
   statement
```

## <a name="remarks"></a>설명

**Bad_cast** 에 대 한 인터페이스는 다음과 같습니다.

```cpp
class bad_cast : public exception
```

다음 코드에는 **`dynamic_cast`** **bad_cast** 예외를 throw 하는 실패 한의 예가 포함 되어 있습니다.

```cpp
// expre_bad_cast_Exception.cpp
// compile with: /EHsc /GR
#include <typeinfo>
#include <iostream>

class Shape {
public:
   virtual void virtualfunc() const {}
};

class Circle: public Shape {
public:
   virtual void virtualfunc() const {}
};

using namespace std;
int main() {
   Shape shape_instance;
   Shape& ref_shape = shape_instance;
   try {
      Circle& ref_circle = dynamic_cast<Circle&>(ref_shape);
   }
   catch (bad_cast b) {
      cout << "Caught: " << b.what();
   }
}
```

캐스팅 되는 개체 (도형)가 지정 된 캐스트 형식 (원)에서 파생 되지 않기 때문에 예외가 throw 됩니다. 예외를 방지하려면 `main`에 다음과 같은 선언을 추가합니다.

```cpp
Circle circle_instance;
Circle& ref_circle = circle_instance;
```

그런 다음 블록에서 캐스트의 의미를 **`try`** 다음과 같이 바꿉니다.

```cpp
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);
```

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[bad_cast](#bad_cast)|`bad_cast` 형식의 개체에 대한 생성자입니다.|

### <a name="functions"></a>Functions

|함수|설명|
|-|-|
|[이며](#what)|TBD|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자 =](#op_eq)|한 `bad_cast` 개체를 다른 개체에 할당 하는 대입 연산자입니다.|

## <a name="bad_cast"></a><a name="bad_cast"></a> bad_cast

`bad_cast` 형식의 개체에 대한 생성자입니다.

```cpp
bad_cast(const char * _Message = "bad cast");
bad_cast(const bad_cast &);
```

## <a name="operator"></a><a name="op_eq"></a> 연산자 =

한 `bad_cast` 개체를 다른 개체에 할당 하는 대입 연산자입니다.

```cpp
bad_cast& operator=(const bad_cast&) noexcept;
```

## <a name="what"></a><a name="what"></a> 이며

```cpp
const char* what() const noexcept override;
```

## <a name="see-also"></a>참고 항목

[dynamic_cast 연산자](../cpp/dynamic-cast-operator.md)\
[어](../cpp/keywords-cpp.md)\
[예외 및 오류 처리에 대 한 최신 c + + 모범 사례](../cpp/errors-and-exception-handling-modern-cpp.md)
