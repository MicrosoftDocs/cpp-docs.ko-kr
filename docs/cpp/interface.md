---
description: '다음에 대 한 자세한 정보: __interface'
title: __interface
ms.date: 05/07/2019
f1_keywords:
- __interface_cpp
helpviewer_keywords:
- __interface keyword [C++]
ms.assetid: ca5d400b-d6d8-4ba2-89af-73f67e5ec056
ms.openlocfilehash: 03ce2b6feb276ed90c3b8855b375a9240e061bba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291989"
---
# <a name="__interface"></a>__interface

**Microsoft 전용**

Microsoft c + + 인터페이스는 다음과 같이 정의할 수 있습니다.

- 0개 이상의 기본 인터페이스에서 상속할 수 있습니다.

- 기본 클래스에서 상속할 수 없습니다.

- 공용 순수 가상 메서드만 포함할 수 있습니다.

- 생성자, 소멸자 또는 연산자를 포함할 수 없습니다.

- 정적 메서드를 포함할 수 없습니다.

- 데이터 멤버를 포함할 수 없습니다. 속성은 허용됩니다.

## <a name="syntax"></a>구문

```
modifier __interface interface-name {interface-definition};
```

## <a name="remarks"></a>설명

이러한 규칙을 사용 하 여 c + + [클래스](../cpp/class-cpp.md) 또는 [구조체](../cpp/struct-cpp.md) 를 구현할 수 있지만이를 **`__interface`** 적용 합니다.

예를 들어 다음은 샘플 인터페이스 정의입니다.

```cpp
__interface IMyInterface {
   HRESULT CommitX();
   HRESULT get_X(BSTR* pbstrName);
};
```

관리 되는 인터페이스에 대 한 자세한 내용은 [interface 클래스](../extensions/interface-class-cpp-component-extensions.md)를 참조 하세요.

`CommitX` 및 `get_X` 함수가 순수 가상 함수임을 명시적으로 나타낼 필요가 없습니다. 첫 번째 함수에 대한 동일한 선언은 다음과 같습니다.

```cpp
virtual HRESULT CommitX() = 0;
```

**`__interface`**[novtable](../cpp/novtable.md) **`__declspec`** 한정자를 의미 합니다.

## <a name="example"></a>예제

다음 샘플에서는 인터페이스에서 선언된 속성을 사용하는 방법을 보여 줍니다.

```cpp
// deriv_interface.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <string.h>
#include <comdef.h>
#include <stdio.h>

[module(name="test")];

[ object, uuid("00000000-0000-0000-0000-000000000001"), library_block ]
__interface IFace {
   [ id(0) ] int int_data;
   [ id(5) ] BSTR bstr_data;
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002") ]
class MyClass : public IFace {
private:
    int m_i;
    BSTR m_bstr;

public:
    MyClass()
    {
        m_i = 0;
        m_bstr = 0;
    }

    ~MyClass()
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
    }

    int get_int_data()
    {
        return m_i;
    }

    void put_int_data(int _i)
    {
        m_i = _i;
    }

    BSTR get_bstr_data()
    {
        BSTR bstr = ::SysAllocString(m_bstr);
        return bstr;
    }

    void put_bstr_data(BSTR bstr)
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
        m_bstr = ::SysAllocString(bstr);
    }
};

int main()
{
    _bstr_t bstr("Testing");
    CoInitialize(NULL);
    CComObject<MyClass>* p;
    CComObject<MyClass>::CreateInstance(&p);
    p->int_data = 100;
    printf_s("p->int_data = %d\n", p->int_data);
    p->bstr_data = bstr;
    printf_s("bstr_data = %S\n", p->bstr_data);
}
```

```Output
p->int_data = 100
bstr_data = Testing
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[키워드](../cpp/keywords-cpp.md)<br/>
[인터페이스 특성](../windows/attributes/interface-attributes.md)
