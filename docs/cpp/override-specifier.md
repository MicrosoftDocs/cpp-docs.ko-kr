---
description: '자세한 정보: override 지정자'
title: override 지정자
ms.date: 11/04/2016
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
ms.openlocfilehash: da29c5c37ff834513736bda02745d031fe3d92aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146005"
---
# <a name="override-specifier"></a>override 지정자

**Override** 키워드를 사용 하 여 기본 클래스의 가상 함수를 재정의 하는 멤버 함수를 지정할 수 있습니다.

## <a name="syntax"></a>구문

```
function-declaration override;
```

## <a name="remarks"></a>설명

**재정의** 는 상황에 맞는 것 이며 멤버 함수 선언 후에 사용 되는 경우에만 특별 한 의미가 있습니다. 그렇지 않으면 예약 된 키워드가 아닙니다.

## <a name="example"></a>예제

**재정의** 를 사용 하 여 코드에서 실수로 인 한 상속 동작을 방지할 수 있습니다. 다음 예제에서는 **재정의** 를 사용 하지 않고 파생 클래스의 멤버 함수 동작이 의도 되지 않았을 수 있는 경우를 보여 줍니다. 컴파일러는 이 코드의 오류를 내보내지 않습니다.

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA(); // ok, works as intended

    virtual void funcB(); // DerivedClass::funcB() is non-const, so it does not
                          // override BaseClass::funcB() const and it is a new member function

    virtual void funcC(double = 0.0); // DerivedClass::funcC(double) has a different
                                      // parameter type than BaseClass::funcC(int), so
                                      // DerivedClass::funcC(double) is a new member function
};
```

**Override** 를 사용 하는 경우 컴파일러는 새 멤버 함수를 자동으로 만드는 대신 오류를 생성 합니다.

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA() override; // ok

    virtual void funcB() override; // compiler error: DerivedClass::funcB() does not
                                   // override BaseClass::funcB() const

    virtual void funcC( double = 0.0 ) override; // compiler error:
                                                 // DerivedClass::funcC(double) does not
                                                 // override BaseClass::funcC(int)

    void funcD() override; // compiler error: DerivedClass::funcD() does not
                           // override the non-virtual BaseClass::funcD()
};
```

함수를 재정의할 수 없고 클래스를 상속할 수 없도록 지정 하려면 [final](../cpp/final-specifier.md) 키워드를 사용 합니다.

## <a name="see-also"></a>참고 항목

[final 지정자](../cpp/final-specifier.md)<br/>
[키워드](../cpp/keywords-cpp.md)
