---
description: '자세한 정보: 특성 대상 (c + +/CLI 및 c + +/CX)'
title: 특성 대상(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- custom attributes, targets
ms.assetid: b4e6e224-da77-4520-b6e6-b96846e0ebc1
ms.openlocfilehash: 2c14f80c277feb7fc540eed8735a8a78e1cb1907
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177031"
---
# <a name="attribute-targets-ccli-and-ccx"></a>특성 대상(C++/CLI 및 C++/CX)

특성 사용 지정자를 사용하여 특성 대상을 지정할 수 있습니다.  각 특성을 정의하여 특정 언어 요소에 적용합니다. 예를 들어, 특성을 정의하여 클래스와 구조체에만 적용할 수도 있습니다.  다음 목록에서는 사용자 지정 특성을 사용할 수 있는 가능한 구문 요소를 보여 줍니다. 이러한 값의 조합(논리적 OR)을 사용할 수 있습니다.

특성 대상을 지정하려면 특성을 정의할 때 하나 이상의 <xref:System.AttributeTargets> 열거자를 <xref:System.AttributeUsageAttribute>에 전달합니다.

다음은 유효한 특성 대상 목록입니다.

- `All`(모든 구문에 적용)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::All)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Assembly`(전체 어셈블리에 적용)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Assembly)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Module`(전체 모듈에 적용)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Module)]
    ref class Attr : public Attribute {};

    [module:Attr];
    ```

- `Class`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Class)]
    ref class Attr : public System::Attribute {};

    [Attr]   // same as [class:Attr]
    ref class MyClass {};
    ```

- `Struct`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Struct)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [struct:Attr]
    value struct MyStruct{};
    ```

- `enum`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Enum)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [enum:Attr]
    enum struct MyEnum{e, d};
    ```

- `Constructor`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Constructor)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] MyStruct(){}   // same as [constructor:Attr]
    };
    ```

- `Method`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Method)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] void Test(){}   // same as [method:Attr]
    };
    ```

- `Property`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Property)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] property int Test;   // same as [property:Attr]
    };
    ```

- `Field`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Field)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] int Test;   // same as [field:Attr]
    };
    ```

- `Event`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Event)]
    ref class Attr : public Attribute {};

    delegate void ClickEventHandler(int, double);

    ref struct MyStruct{
    [Attr] event ClickEventHandler^ OnClick;   // same as [event:Attr]
    };
    ```

- `Interface`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Interface)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [event:Attr]
    interface struct MyStruct{};
    ```

- `Parameter`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Parameter)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    void Test([Attr] int i);
    void Test2([parameter:Attr] int i);
    };
    ```

- `Delegate`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Delegate)]
    ref class Attr : public Attribute {};

    [Attr] delegate void Test();
    [delegate:Attr] delegate void Test2();
    ```

- `ReturnValue`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::ReturnValue)]
    ref class Attr : public Attribute {};

    ref struct MyStruct {
    // Note required specifier
    [returnvalue:Attr] int Test() { return 0; }
    };
    ```

일반적으로, 특성은 적용되는 언어 요소 바로 앞에 옵니다. 그러나 일부의 경우, 특성의 위치만으로 특성의 의도된 대상을 결정하기에 충분하지 않습니다. 다음 예제를 고려해 보세요.

```cpp
[Attr] int MyFn(double x)...
```

구문적으로 특성이 메서드 또는 메서드의 반환 값(이 경우 기본값은 메서드)에 적용되도록 구성되었는지 확인할 수 있는 방법은 없습니다. 이러한 경우, 특성 사용 지정자를 사용할 수 있습니다. 예를 들어 특성을 반환 값에 적용하게 하려면 다음과 같이 `returnvalue` 지정자를 사용합니다.

```cpp
[returnvalue:Attr] int MyFn(double x)... // applies to return value
```

특성 사용 지정자는 다음과 같은 경우 필요합니다.

- 어셈블리 또는 모듈 수준 특성을 지정할 경우

- 특성을 메서드가 아닌 메서드의 반환 값에 적용하도록 지정할 경우

    ```cpp
    [method:Attr] int MyFn(double x)...     // Attr applies to method
    [returnvalue:Attr] int MyFn(double x)...// Attr applies to return value
    [Attr] int MyFn(double x)...            // default: method
    ```

- 특성을 속성이 아닌 속성의 접근자에 적용하도록 지정할 경우

    ```cpp
    [method:MyAttr(123)] property int Property()
    [property:MyAttr(123)] property int Property()
    [MyAttr(123)] property int get_MyPropy() // default: property
    ```

- 특성을 이벤트가 아닌 이벤트의 접근자에 적용하도록 지정할 경우

    ```cpp
    delegate void MyDel();
    ref struct X {
       [field:MyAttr(123)] event MyDel* MyEvent;   //field
       [event:MyAttr(123)] event MyDel* MyEvent;   //event
       [MyAttr(123)] event MyDel* MyEvent;   // default: event
    }
    ```

특성 사용 지정자는 바로 뒤에 오는 특성에만 적용됩니다. 즉,

```cpp
[returnvalue:Attr1, Attr2]
```

위는 아래와 다릅니다.

```cpp
[returnvalue:Attr1, returnvalue:Attr2]
```

## <a name="example"></a>예제

### <a name="description"></a>설명

이 샘플에서는 여러 대상을 지정하는 방법을 보여 줍니다.

### <a name="code"></a>코드

```cpp
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Struct, AllowMultiple = true )]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};

[Attr]
[Attr(true)]
value struct MyStruct {};
```

## <a name="see-also"></a>참조

[사용자 정의 특성](user-defined-attributes-cpp-component-extensions.md)
