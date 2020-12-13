---
description: '자세히 알아보기: 형식 특성에 대 한 컴파일러 지원 (c + +/CLI 및 c + +/CX)'
title: 형식 특성에 대한 컴파일러 지원(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- __is_simple_value_class
- __has_trivial_destructor
- __has_assign
- __is_union
- __is_class
- __is_abstract
- __has_trivial_assign
- __has_virtual_destructor
- __is_ref_array
- __is_base_of
- __has_copy
- __is_polymorphic
- __has_nothrow_constructor
- __is_ref_class
- __is_delegate
- __is_convertible_to
- __is_value_class
- __is_interface_class
- __has_nothrow_copy
- __is_sealed
- __has_trivial_constructor
- __has_trivial_copy
- __is_enum
- __has_nothrow_assign
- __has_finalizer
- __is_empty
- __is_pod
- __has_user_destructor
helpviewer_keywords:
- __is_class keyword [C++]
- __is_pod keyword [C++]
- __is_delegate keyword [C++]
- __is_value_class keyword [C++]
- __has_copy keyword [C++]
- __has_nothrow_copy keyword [C++]
- __is_interface_class keyword [C++]
- __is_sealed keyword [C++]
- __is_convertible_to keyword [C++]
- __is_ref_class keyword [C++]
- __has_trivial_copy keyword [C++]
- __has_user_destructor keyword [C++]
- __is_abstract keyword [C++]
- __is_empty keyword [C++]
- __has_trivial_assign keyword [C++]
- __has_nothrow_constructor keyword [C++]
- __is_ref_array keyword [C++]
- __is_base_of keyword [C++]
- __has_nothrow_assign keyword [C++]
- __has_virtual_destructor keyword [C++]
- __has_finalizer keyword [C++]
- __is_union keyword [C++]
- __has_assign keyword [C++]
- __has_trivial_destructor keyword [C++]
- __is_polymorphic keyword [C++]
- __is_enum keyword [C++]
- __is_simple_value_class keyword [C++]
- __has_trivial_constructor keyword [C++]
ms.assetid: cd440630-0394-48c0-a16b-1580b6ef5844
ms.openlocfilehash: ec9efe1305a844779b4848cbae155d2946488d11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176927"
---
# <a name="compiler-support-for-type-traits-ccli-and-ccx"></a>형식 특성에 대한 컴파일러 지원(C++/CLI 및 C++/CX)

Microsoft C++ 컴파일러는 컴파일 시간에 형식의 다양한 특성을 나타내는 *형식 특성* 을 C++/CLI 및 C++/CX 확장에서 지원합니다.

## <a name="all-runtimes"></a>모든 런타임

### <a name="remarks"></a>설명

형식 특성은 라이브러리를 작성하는 프로그래머에게 특히 유용합니다.

다음 목록에는 컴파일러에서 지원하는 형식 특성이 나와 있습니다. **`false`** 형식 특성의 이름으로 지정 된 조건이 충족 되지 않는 경우 모든 형식 특성은를 반환 합니다.

다음 목록에 있는 코드 예제는 C++/CLI로만 작성되었습니다. 그러나 해당 형식 특성은 달리 명시되지 않은 경우 C++/CX에서도 지원됩니다. “플랫폼 형식”이란 용어는 Windows 런타임 형식 또는 공용 언어 런타임 형식 중 하나를 가리킵니다.

- `__has_assign(`*유형*`)`

   **`true`** 플랫폼 또는 네이티브 형식에 복사 할당 연산자가 있는 경우를 반환 합니다.

    ```cpp
    ref struct R {
    void operator=(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_assign(R));
    }
    ```

- `__has_copy(`*유형*`)`

   **`true`** 플랫폼 또는 네이티브 형식에 복사 생성자가 있으면를 반환 합니다.

    ```cpp
    ref struct R {
    R(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_copy(R));
    }
    ```

- `__has_finalizer(`*유형*`)`

   (C + +/CX에서 지원 되지 않음) **`true`** CLR 형식에 종료 자가 있으면를 반환 합니다. 자세한 내용은 [방법: 클래스 및 구조체 정의 및 사용 (c + +/cli)의 소멸자 및 종료자](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) 를 참조 하세요.

    ```cpp
    using namespace System;
    ref struct R {
    ~R() {}
    protected:
    !R() {}
    };

    int main() {
    Console::WriteLine(__has_finalizer(R));
    }
    ```

- `__has_nothrow_assign(`*유형*`)`

   **`true`** 복사 할당 연산자에 빈 예외 사양이 있으면를 반환 합니다.

    ```cpp
    #include <stdio.h>
    struct S {
    void operator=(S& r) throw() {}
    };

    int main() {
    __has_nothrow_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_constructor(`*유형*`)`

   **`true`** 기본 생성자에 빈 예외 사양이 있으면를 반환 합니다.

    ```cpp
    #include <stdio.h>
    struct S {
    S() throw() {}
    };

    int main() {
    __has_nothrow_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_copy(`*유형*`)`

   **`true`** 복사 생성자에 빈 예외 사양이 있으면를 반환 합니다.

    ```cpp
    #include <stdio.h>
    struct S {
    S(S& r) throw() {}
    };

    int main() {
    __has_nothrow_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_assign(`*유형*`)`

   **`true`** 형식에 컴파일러에서 생성 된 trivial 할당 연산자가 있는 경우를 반환 합니다.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_constructor(`*유형*`)`

   **`true`** 형식에 컴파일러에서 생성 된 trivial 생성자가 있는 경우를 반환 합니다.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_copy(`*유형*`)`

   **`true`** 형식에 컴파일러에서 생성 된 trivial 복사 생성자가 있는 경우를 반환 합니다.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_destructor(`*유형*`)`

   **`true`** 형식에 컴파일러에서 생성 된 trivial 소멸자가 있는 경우를 반환 합니다.

    ``` cpp
    // has_trivial_destructor.cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_user_destructor(`*유형*`)`

   **`true`** 플랫폼 또는 네이티브 형식에 사용자가 선언한 소멸자가 있으면를 반환 합니다.

    ```cpp
    // has_user_destructor.cpp

    using namespace System;
    ref class R {
    ~R() {}
    };

    int main() {
    Console::WriteLine(__has_user_destructor(R));
    }
    ```

- `__has_virtual_destructor(`*유형*`)`

   **`true`** 형식에 가상 소멸자가 있으면를 반환 합니다.

   `__has_virtual_destructor`는 플랫폼 형식에 대해서도 작동하며, 플랫폼 형식의 모든 사용자 정의 소멸자는 가상 소멸자입니다.

    ```cpp
    // has_virtual_destructor.cpp
    #include <stdio.h>
    struct S {
    virtual ~S() {}
    };

    int main() {
    __has_virtual_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_abstract(`*유형*`)`

   **`true`** 형식이 추상 형식이 면를 반환 합니다. 네이티브 추상 형식에 대한 자세한 내용은 [추상 클래스](../cpp/abstract-classes-cpp.md)를 참조하세요.

   `__is_abstract`는 플랫폼 형식에 대해서도 작동합니다. 하나 이상의 멤버가 있는 인터페이스는 하나 이상의 추상 멤버가 있는 참조 형식과 마찬가지로 추상 형식입니다. 추상 플랫폼 형식에 대한 자세한 내용은 [abstract](abstract-cpp-component-extensions.md)를 참조하세요.

    ```cpp
    // is_abstract.cpp
    #include <stdio.h>
    struct S {
    virtual void Test() = 0;
    };

    int main() {
    __is_abstract(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_base_of(` `base` `,` `derived` `)`

   두 형식이 **`true`** 동일 하면 첫 번째 형식이 두 번째 형식의 기본 클래스 이면를 반환 하 고,

   `__is_base_of`는 플랫폼 형식에 대해서도 작동합니다. 예를 들어 **`true`** 첫 번째 형식이 [인터페이스 클래스](interface-class-cpp-component-extensions.md) 이 고 두 번째 형식이 인터페이스를 구현 하는 경우이 메서드는를 반환 합니다.

    ```cpp
    // is_base_of.cpp
    #include <stdio.h>
    struct S {};
    struct T : public S {};

    int main() {
    __is_base_of(S, T) == true ?
    printf("true\n") : printf("false\n");

    __is_base_of(S, S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_class(`*유형*`)`

   **`true`** 형식이 네이티브 클래스 또는 구조체 이면를 반환 합니다.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_class(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_convertible_to(` `from` `,`  `to` `)`

   **`true`** 첫 번째 형식을 두 번째 형식으로 변환할 수 있으면를 반환 합니다.

    ```cpp
    #include <stdio.h>
    struct S {};
    struct T : public S {};

    int main() {
    S * s = new S;
    T * t = new T;
    s = t;
    __is_convertible_to(T, S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_delegate(`*유형*`)`

   **`true`** `type` 가 대리자 이면를 반환 합니다. 자세한 내용은 [delegate(C++/CLI 및 C++/CX)](delegate-cpp-component-extensions.md)를 참조하세요.

    ```cpp
    delegate void MyDel();
    int main() {
    System::Console::WriteLine(__is_delegate(MyDel));
    }
    ```

- `__is_empty(`*유형*`)`

   **`true`** 형식에 인스턴스 데이터 멤버가 없으면를 반환 합니다.

    ```cpp
    #include <stdio.h>
    struct S {
    int Test() {}
    static int i;
    };
    int main() {
    __is_empty(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_enum(`*유형*`)`

   **`true`** 형식이 네이티브 열거형 이면를 반환 합니다.

    ```cpp
    // is_enum.cpp
    #include <stdio.h>
    enum E { a, b };

    struct S {
    enum E2 { c, d };
    };

    int main() {
    __is_enum(E) == true ?
    printf("true\n") : printf("false\n");

    __is_enum(S::E2) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_interface_class(`*유형*`)`

   **`true`** 플랫폼 인터페이스를 전달한 경우를 반환 합니다. 자세한 내용은 [인터페이스 클래스](interface-class-cpp-component-extensions.md)를 참조하세요.

    ```cpp
    // is_interface_class.cpp

    using namespace System;
    interface class I {};
    int main() {
    Console::WriteLine(__is_interface_class(I));
    }
    ```

- `__is_pod(`*유형*`)`

   **`true`** 형식이 생성자 또는 전용 또는 보호 된 비정적 멤버가 없는 클래스 또는 공용 구조체 이거나, 기본 클래스가 없고, 가상 함수가 없는 경우를 반환 합니다. POD에 대한 자세한 내용은 C++ 표준, 섹션 8.5.1/1, 9/4 및 3.9/10을 참조하세요.

   `__is_pod`는 기본 형식에 대해 false를 반환합니다.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_pod(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_polymorphic(`*유형*`)`

   **`true`** 네이티브 형식에 가상 함수가 있는 경우를 반환 합니다.

    ```cpp
    #include <stdio.h>
    struct S {
    virtual void Test(){}
    };

    int main() {
    __is_polymorphic(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_ref_array(`*유형*`)`

   **`true`** 플랫폼 배열이 전달 된 경우을 반환 합니다. 자세한 내용은 [배열](arrays-cpp-component-extensions.md)을 참조하세요.

    ```cpp
    using namespace System;
    int main() {
    array<int>^ x = gcnew array<int>(10);
    Console::WriteLine(__is_ref_array(array<int>));
    }
    ```

- `__is_ref_class(`*유형*`)`

   **`true`** 가 참조 클래스를 전달한 경우를 반환 합니다. 사용자 정의 참조 형식에 대한 자세한 내용은 [클래스 및 구조체](classes-and-structs-cpp-component-extensions.md)를 참조하세요.

    ```cpp
    using namespace System;
    ref class R {};
    int main() {
    Console::WriteLine(__is_ref_class(Buffer));
    Console::WriteLine(__is_ref_class(R));
    }
    ```

- `__is_sealed(`*유형*`)`

   **`true`** 전달 된 플랫폼 또는 네이티브 형식이 sealed로 표시 된 경우을 반환 합니다. 자세한 내용은 [sealed](sealed-cpp-component-extensions.md)를 참조하세요.

    ```cpp
    ref class R sealed{};
    int main() {
    System::Console::WriteLine(__is_sealed(R));
    }
    ```

- `__is_simple_value_class(`*유형*`)`

   **`true`** 가비지 수집 된 힙에 대 한 참조가 포함 되지 않은 값 형식이 전달 된 경우을 반환 합니다. 사용자 정의 값 형식에 대한 자세한 내용은 [클래스 및 구조체](classes-and-structs-cpp-component-extensions.md)를 참조하세요.

    ```cpp
    using namespace System;
    ref class R {};
    value struct V {};
    value struct V2 {
    R ^ r;   // not a simnple value type
    };

    int main() {
    Console::WriteLine(__is_simple_value_class(V));
    Console::WriteLine(__is_simple_value_class(V2));
    }
    ```

- `__is_union(`*유형*`)`

   **`true`** 형식이 공용 구조체 이면를 반환 합니다.

    ```cpp
    #include <stdio.h>
    union A {
    int i;
    float f;
    };

    int main() {
    __is_union(A) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_value_class(`*유형*`)`

   **`true`** 값 형식이 전달 된 경우을 반환 합니다. 사용자 정의 값 형식에 대한 자세한 내용은 [클래스 및 구조체](classes-and-structs-cpp-component-extensions.md)를 참조하세요.

    ```cpp
    value struct V {};

    int main() {
    System::Console::WriteLine(__is_value_class(V));
    }
    ```

## <a name="windows-runtime"></a>Windows 런타임

### <a name="remarks"></a>설명

`__has_finalizer(`  `)` 이 플랫폼에서는 종료자를 지원 하지 않으므로 형식 형식 특성을 지원 하지 않습니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

### <a name="remarks"></a>설명

(이 기능에는 플랫폼별 설명이 없습니다.)

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예제

**예제**

다음 코드 예제에서는 클래스 템플릿을 사용하여 `/clr` 컴파일에 대한 컴파일러 형식 특성을 노출하는 방법을 보여 줍니다. 자세한 내용은 [Windows 런타임 및 관리형 템플릿](windows-runtime-and-managed-templates-cpp-component-extensions.md)을 참조하세요.

```cpp
// compiler_type_traits.cpp
// compile with: /clr
using namespace System;

template <class T>
ref struct is_class {
   literal bool value = __is_ref_class(T);
};

ref class R {};

int main () {
   if (is_class<R>::value)
      Console::WriteLine("R is a ref class");
   else
      Console::WriteLine("R is not a ref class");
}
```

```Output
R is a ref class
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
