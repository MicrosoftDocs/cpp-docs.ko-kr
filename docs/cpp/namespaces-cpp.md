---
description: '네임 스페이스에 대 한 자세한 정보: 네임 스페이스 (c + +)'
title: 네임스페이스 (C++)
ms.date: 08/30/2017
f1_keywords:
- namespace_CPP
- using_CPP
helpviewer_keywords:
- namespaces [C++]
ms.assetid: d1a5a9ab-1cad-47e6-a82d-385bb77f4188
ms.openlocfilehash: 5a655b5e772d16df34e64c5e4808ce68de64f49f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313764"
---
# <a name="namespaces-c"></a>네임스페이스 (C++)

네임스페이스는 내부 식별자(형식, 함수, 변수 등의 이름)에 범위를 제공하는 선언적 영역입니다. 네임스페이스는 코드를 논리 그룹으로 구성하고 특히 코드베이스에 여러 라이브러리가 포함된 경우 발생할 수 있는 이름 충돌을 방지하는 데 사용됩니다. 네임스페이스 범위에 있는 모든 식별자는 한정 없이 서로에게 표시됩니다. 네임 스페이스 외부의 식별자는 각 식별자에 대 한 정규화 된 이름 (예:)을 사용 하 여 멤버에 액세스 하거나, 단일 식별자에 대 한 using `std::vector<std::string> vec;` [선언](../cpp/using-declaration.md) ( `using std::string` ) 또는 네임 스페이스의 모든 식별자에 대 한 [using 지시문](../cpp/namespaces-cpp.md#using_directives) ()을 사용 하 여 멤버에 액세스할 수 있습니다 `using namespace std;` . 헤더 파일의 코드는 항상 정규화된 네임스페이스 이름을 사용해야 합니다.

다음 예제에서는 네임스페이스 선언 및 네임스페이스 외부 코드가 해당 멤버에 액세스할 수 있는 세 가지 방법을 보여 줍니다.

```cpp
namespace ContosoData
{
    class ObjectManager
    {
    public:
        void DoSomething() {}
    };
    void Func(ObjectManager) {}
}
```

정규화된 이름 사용:

```cpp
ContosoData::ObjectManager mgr;
mgr.DoSomething();
ContosoData::Func(mgr);
```

using 선언을 사용하여 하나의 식별자를 범위로 가져오기:

```cpp
using ContosoData::ObjectManager;
ObjectManager mgr;
mgr.DoSomething();
```

using 지시문을 사용하여 네임스페이스의 모든 식별자를 범위로 가져오기:

```cpp
using namespace ContosoData;

ObjectManager mgr;
mgr.DoSomething();
Func(mgr);
```

## <a name="using-directives"></a><a id="using_directives"></a> using 지시문

**`using`** 지시문을 **`namespace`** 사용 하면 명시적 한정자로 *네임 스페이스 이름* 없이의 모든 이름을 사용할 수 있습니다. 네임 스페이스에서 여러 다른 식별자를 사용 하는 경우 구현 파일 (예: * .cpp)에서 using 지시문을 사용 합니다. 하나 또는 두 개의 식별자만 사용 하는 경우에는 using 선언을 사용 하 여 네임 스페이스의 모든 식별자가 아닌 해당 식별자를 범위로 가져옵니다. 지역 변수의 이름이 네임스페이스 변수와 동일한 경우 네임스페이스 변수가 숨겨집니다. 전역 변수와 동일한 이름을 가진 네임스페이스 변수를 사용하면 오류가 발생합니다.

> [!NOTE]
> using 지시문은 .cpp 파일 맨 위나(파일 범위) 클래스 또는 함수 정의 내에 배치할 수 있습니다.
>
> 일반적으로 헤더 파일(*.h)에는 using 지시문을 넣지 마세요. 해당 헤더를 포함하는 모든 파일이 네임스페이스의 모든 식별자를 범위로 가져오기 때문에 이름 숨김 및 이름 충돌 문제가 발생할 수 있으며, 디버그하기 매우 어렵습니다. 헤더 파일에는 항상 정규화된 이름을 사용하세요. 이름이 너무 길면 네임스페이스 별칭을 사용하여 축약할 수 있습니다. 다음을 참조하세요.

## <a name="declaring-namespaces-and-namespace-members"></a>네임스페이스 및 네임스페이스 멤버 선언

일반적으로 헤더 파일에서 네임스페이스를 선언합니다. 함수 구현이 별도 파일에 있는 경우 이 예제와 같이 함수 이름을 한정합니다.

```cpp
//contosoData.h
#pragma once
namespace ContosoDataServer
{
    void Foo();
    int Bar();
}
```

Contosodata의 함수 구현에서는 **`using`** 지시문을 파일의 맨 위에 둔 경우에도 정규화 된 이름을 사용 해야 합니다.

```cpp
#include "contosodata.h"
using namespace ContosoDataServer;

void ContosoDataServer::Foo() // use fully-qualified name here
{
   // no qualification needed for Bar()
   Bar();
}

int ContosoDataServer::Bar(){return 0;}
```

단일 파일의 여러 블록과 여러 파일에서 네임스페이스를 선언할 수 있습니다. 컴파일러가 전처리 중에 파트를 결합하며, 결과로 생성된 네임스페이스에는 모든 파트에서 선언된 멤버가 모두 포함됩니다. 이러한 예로 표준 라이브러리의 각 헤더 파일에서 선언된 std 네임스페이스가 있습니다.

정의된 이름의 명시적 정규화로 선언된 명명된 네임스페이스의 멤버는 해당 네임스페이스의 외부에서 정의될 수 있습니다. 그러나 정의는 선언의 네임스페이스를 포함하는 네임스페이스의 선언 위치 다음에 표시되어야 합니다. 예를 들어:

```cpp
// defining_namespace_members.cpp
// C2039 expected
namespace V {
    void f();
}

void V::f() { }        // ok
void V::g() { }        // C2039, g() is not yet a member of V

namespace V {
    void g();
}
```

이 오류는 여러 헤더 파일에서 네임스페이스 멤버가 선언되었으며 해당 헤더를 올바른 순서로 포함하지 않은 경우에 발생할 수 있습니다.

## <a name="the-global-namespace"></a>전역 네임스페이스

식별자가 명시적 네임스페이스에서 선언되지 않은 경우 암시적 전역 네임스페이스에 포함됩니다. 일반적으로 전역 네임 스페이스에 있어야 하는 진입점 [Main 함수](../c-language/main-function-and-program-execution.md)를 제외 하 고 가능 하면 전역 범위에서 선언을 만들지 마십시오. 전역 식별자를 명시적으로 한정하려면 `::SomeFunction(x);`과 같이 범위 확인 연산자를 이름 없이 사용합니다. 이렇게 하면 다른 네임스페이스에 있는 동일한 이름의 식별자와 해당 식별자가 구분되며, 다른 사용자가 코드를 더 쉽게 이해하는 데에도 도움이 됩니다.

## <a name="the-std-namespace"></a>std 네임스페이스

모든 c + + 표준 라이브러리 형식 및 함수는 `std` 내부에 중첩 된 네임 스페이스 또는 네임 스페이스에서 선언 됩니다 `std` .

## <a name="nested-namespaces"></a>중첩된 네임스페이스

네임스페이스를 중첩할 수 있습니다. 일반적인 중첩 된 네임 스페이스는 부모 멤버에 대 한 정규화 되지 않은 액세스를 갖지만, 부모 멤버는 다음 예제와 같이 인라인으로 선언 되지 않는 한 중첩 된 네임 스페이스에 대 한 정규화 되지 않은 액세스 권한을 갖지 않습니다.

```cpp
namespace ContosoDataServer
{
    void Foo();

    namespace Details
    {
        int CountImpl;
        void Ban() { return Foo(); }
    }

    int Bar(){...};
    int Baz(int i) { return Details::CountImpl; }
}
```

일반적인 중첩된 네임스페이스를 사용하여 부모 네임스페이스의 공용 인터페이스에 포함되지 않는 내부 구현 세부 정보를 캡슐화할 수 있습니다.

## <a name="inline-namespaces-c-11"></a>인라인 네임스페이스(C++ 11)

일반적인 중첩된 네임스페이스와 달리, 인라인 네임스페이스의 멤버는 부모 네임스페이스의 멤버로 처리됩니다. 이러한 특징 때문에 오버로드된 함수의 인수 종속 조회가 부모 및 중첩된 인라인 네임스페이스에 오버로드가 있는 함수에서 작동할 수 있습니다. 또한 인라인 네임스페이스에서 선언된 템플릿의 부모 네임스페이스에서 특수화를 선언할 수 있습니다. 다음 예제에서는 외부 코드가 기본적으로 인라인 네임스페이스에 바인딩하는 방법을 보여 줍니다.

```cpp
//Header.h
#include <string>

namespace Test
{
    namespace old_ns
    {
        std::string Func() { return std::string("Hello from old"); }
    }

    inline namespace new_ns
    {
        std::string Func() { return std::string("Hello from new"); }
    }
}

#include "header.h"
#include <string>
#include <iostream>

int main()
{
    using namespace Test;
    using namespace std;

    string s = Func();
    std::cout << s << std::endl; // "Hello from new"
    return 0;
}
```

다음 예제에서는 인라인 네임스페이스에서 선언된 템플릿의 부모에서 특수화를 선언할 수 있는 방법을 보여 줍니다.

```cpp
namespace Parent
{
    inline namespace new_ns
    {
         template <typename T>
         struct C
         {
             T member;
         };
    }
     template<>
     class C<int> {};
}
```

인라인 네임스페이스를 버전 관리 메커니즘으로 사용하여 라이브러리의 공용 인터페이스에 대한 변경 내용을 관리할 수 있습니다. 예를 들어 단일 부모 네임스페이스를 만들고 인터페이스의 각 버전을 부모 안에 중첩된 자체 네임스페이스에 캡슐화할 수 있습니다. 가장 최근 버전이나 기본 설정 버전을 보유한 네임스페이스는 인라인으로 한정되므로 부모 네임스페이스의 직접 멤버인 것처럼 노출됩니다. Parent::Class를 호출하는 클라이언트 코드는 자동으로 새 코드에 바인딩합니다. 이전 버전을 사용하려는 클라이언트는 해당 코드가 있는 중첩된 네임스페이스의 정규화된 경로를 사용하여 계속 액세스할 수 있습니다.

컴파일 단위에서 네임스페이스의 첫 번째 선언에 Inline 키워드를 적용해야 합니다.

다음 예제에서는 각각 중첩된 네임스페이스에 있는 각 인터페이스의 두 버전을 보여 줍니다. `v_20` 네임스페이스는 `v_10` 인터페이스에서 약간 수정되었으며 인라인으로 표시됩니다. 새 라이브러리를 사용하고 `Contoso::Funcs::Add`를 호출하는 클라이언트 코드는 v_20 버전을 호출합니다. 코드에서 `Contoso::Funcs::Divide`를 호출하려고 하면 이제 컴파일 타임 오류가 발생합니다. 해당 함수가 실제로 필요한 경우 명시적으로 `Contoso::v_10::Funcs::Divide`를 호출하여 `v_10` 버전에 계속 액세스할 수 있습니다.

```cpp
namespace Contoso
{
    namespace v_10
    {
        template <typename T>
        class Funcs
        {
        public:
            Funcs(void);
            T Add(T a, T b);
            T Subtract(T a, T b);
            T Multiply(T a, T b);
            T Divide(T a, T b);
        };
    }

    inline namespace v_20
    {
        template <typename T>
        class Funcs
        {
        public:
            Funcs(void);
            T Add(T a, T b);
            T Subtract(T a, T b);
            T Multiply(T a, T b);
            std::vector<double> Log(double);
            T Accumulate(std::vector<T> nums);
      };
    }
}
```

## <a name="namespace-aliases"></a><a id="namespace_aliases"></a> 네임 스페이스 별칭

네임스페이스 이름은 고유해야 하며, 이는 대체로 이름이 너무 짧지 않아야 함을 의미합니다. 이름 길이를 사용 하 여 코드를 읽을 수 없거나 using 지시문을 사용할 수 없는 헤더 파일을 입력 하는 것이 지루한 경우 실제 이름의 약어 역할을 하는 네임 스페이스 별칭을 만들 수 있습니다. 예를 들어:

```cpp
namespace a_very_long_namespace_name { class Foo {}; }
namespace AVLNN = a_very_long_namespace_name;
void Bar(AVLNN::Foo foo){ }
```

## <a name="anonymous-or-unnamed-namespaces"></a>익명 또는 명명되지 않은 네임스페이스

명시적 네임스페이스를 만들고 이름을 지정하지 않을 수 있습니다.

```cpp
namespace
{
    int MyFunc(){}
}
```

이를 명명 되지 않은 네임 스페이스 또는 익명 네임 스페이스 라고 하며, 명명 된 네임 스페이스를 만들지 않고도 다른 파일 (즉, 내부 링크 제공)에서 코드에 대 한 변수 선언을 표시 하지 않으려는 경우에 유용 합니다. 동일한 파일의 모든 코드에서 명명되지 않은 네임스페이스의 식별자를 볼 수 있지만, 해당 파일 외부 또는 보다 정확히 말해 변환 단위 외부에서는 네임스페이스 자체와 함께 식별자를 볼 수 없습니다.

## <a name="see-also"></a>참고 항목

[선언 및 정의](declarations-and-definitions-cpp.md)
