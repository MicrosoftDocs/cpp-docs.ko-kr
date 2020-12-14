---
description: '자세한 정보: nullptr (c + +/CLI 및 c + +/CX)'
title: nullptr(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
ms.openlocfilehash: cf531e81e31af2e3f3790b9f57b54278ad574733
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257643"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr(C++/CLI 및 C++/CX)

**`nullptr`** 키워드가 *null 포인터 값* 을 나타냅니다. Null 포인터 값은 개체 핸들, 내부 포인터 또는 네이티브 포인터 형식이 개체를 가리키지 않음을 나타내는 데 사용합니다.

**`nullptr`** 관리 코드 또는 네이티브 코드와 함께 사용 합니다. 컴파일러는 관리형 및 네이티브 Null 포인터 값에 대해 서로 다른 적절한 명령을 내보냅니다. 이 키워드의 ISO 표준 C++ 버전을 사용하는 방법에 대한 자세한 내용은 [nullptr](../cpp/nullptr.md)을 참조하세요.

**__Nullptr** 키워드는와 동일한 의미를 가지 며 **`nullptr`** 네이티브 코드에만 적용 되는 Microsoft 전용 키워드입니다. 를 **`nullptr`** 네이티브 C/c + + 코드와 함께 사용 하 고 [/clr](../build/reference/clr-common-language-runtime-compilation.md) 컴파일러 옵션을 사용 하 여 컴파일하면 컴파일러가 **`nullptr`** 네이티브 또는 관리 되는 null 포인터 값을 표시 하는지 여부를 확인할 수 없습니다. 컴파일러에 대 한 의도를 명확 하 게 하려면를 사용 **`nullptr`** 하 여 관리 되는 값을 지정 하거나 **__nullptr** 를 사용 하 여 네이티브 값을 지정 합니다.

**`nullptr`** 키워드는 Visual Basic의 **Nothing** 과 같으며 c #의 경우 **null** 입니다.

## <a name="usage"></a>사용

**`nullptr`** 키워드는 핸들, 네이티브 포인터 또는 함수 인수를 사용할 수 있는 모든 위치에서 사용할 수 있습니다.

**`nullptr`** 키워드는 형식이 아니므로에서 사용할 수 없습니다.

- [sizeof](../cpp/sizeof-operator.md)

- [typeid](../cpp/typeid-operator.md)

- `throw nullptr`(단, `throw (Object^)nullptr;`은 사용 가능함)

**`nullptr`** 키워드는 다음 포인터 형식을 초기화 하는 데 사용할 수 있습니다.

- 네이티브 포인터

- Windows 런타임 핸들

- 관리형 핸들

- 관리형 내부 포인터

**`nullptr`** 키워드를 사용 하 여 참조를 사용 하기 전에 포인터나 핸들 참조가 null 인지 여부를 테스트할 수 있습니다.

오류 검사에 Null 포인터 값을 사용하는 언어 간의 함수 호출을 올바르게 해석해야 합니다.

핸들을 0으로 초기화할 수 없습니다. 만 **`nullptr`** 사용할 수 있습니다. 개체 핸들에 상수 0을 할당하면 boxed `Int32` 및 `Object^`로의 캐스트가 생성됩니다.

## <a name="example-nullptr-keyword"></a>예: `nullptr` 키워드

다음 코드 예제에서는 **`nullptr`** 핸들, 네이티브 포인터 또는 함수 인수를 사용할 수 있는 모든 위치에 키워드를 사용할 수 있는 방법을 보여 줍니다. 이 예에서는 키워드를 사용 하 여 참조를 확인 하는 방법을 보여 줍니다 **`nullptr`** .

```cpp
// mcpp_nullptr.cpp
// compile with: /clr
value class V {};
ref class G {};
void f(System::Object ^) {}

int main() {
// Native pointer.
   int *pN = nullptr;
// Managed handle.
   G ^pG = nullptr;
   V ^pV1 = nullptr;
// Managed interior pointer.
   interior_ptr<V> pV2 = nullptr;
// Reference checking before using a pointer.
   if (pN == nullptr) {}
   if (pG == nullptr) {}
   if (pV1 == nullptr) {}
   if (pV2 == nullptr) {}
// nullptr can be used as a function argument.
   f(nullptr);   // calls f(System::Object ^)
}
```

## <a name="example-use-nullptr-and-zero-interchangeably"></a>예: `nullptr` 및 0을 교대로 사용

다음 코드 예제에서는 **`nullptr`** 및 0을 네이티브 포인터에서 교대로 사용할 수 있음을 보여 줍니다.

```cpp
// mcpp_nullptr_1.cpp
// compile with: /clr
class MyClass {
public:
   int i;
};

int main() {
   MyClass * pMyClass = nullptr;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");

   pMyClass = 0;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");
}
```

```Output
pMyClass == nullptr

pMyClass == 0

pMyClass == nullptr

pMyClass == 0
```

## <a name="example-interpret-nullptr-as-a-handle"></a>예: `nullptr` 핸들로 해석

다음 코드 예제에서는가 모든 형식에 **`nullptr`** 대 한 핸들 또는 임의의 형식에 대 한 네이티브 포인터로 해석 됨을 보여 줍니다. 여러 형식에 대한 핸들이 있는 함수 오버로드의 경우 모호성 오류가 생성됩니다. 는 **`nullptr`** 형식으로 명시적으로 캐스팅 되어야 합니다.

```cpp
// mcpp_nullptr_2.cpp
// compile with: /clr /LD
void f(int *){}
void f(int ^){}

void f_null() {
   f(nullptr);   // C2668
   // try one of the following lines instead
   f((int *) nullptr);
   f((int ^) nullptr);
}
```

## <a name="example-cast-nullptr"></a>예: Cast `nullptr`

다음 코드 예제에서는 캐스팅이 허용 되 **`nullptr`** 고 값을 포함 하는 캐스트 형식에 대 한 포인터 또는 핸들을 반환 하는 방법을 보여 줍니다 **`nullptr`** .

```cpp
// mcpp_nullptr_3.cpp
// compile with: /clr /LD
using namespace System;
template <typename T>
void f(T) {}   // C2036 cannot deduce template type because nullptr can be any type

int main() {
   f((Object ^) nullptr);   // T = Object^, call f(Object ^)

   // Delete the following line to resolve.
   f(nullptr);

   f(0);   // T = int, call f(int)
}
```

## <a name="example-pass-nullptr-as-a-function-parameter"></a>예: `nullptr` 함수 매개 변수로 전달

다음 코드 예제에서는를 **`nullptr`** 함수 매개 변수로 사용할 수 있음을 보여 줍니다.

```cpp
// mcpp_nullptr_4.cpp
// compile with: /clr
using namespace System;
void f(Object ^ x) {
   Console::WriteLine("test");
}

int main() {
   f(nullptr);
}
```

```Output
test
```

## <a name="example-default-initialization"></a>예: 기본 초기화

다음 코드 예제에서는 핸들이 선언 되 고 명시적으로 초기화 되지 않은 경우 기본적으로로 초기화 됨을 보여 줍니다 **`nullptr`** .

```cpp
// mcpp_nullptr_5.cpp
// compile with: /clr
using namespace System;
ref class MyClass {
public:
   void Test() {
      MyClass ^pMyClass;   // gc type
      if (pMyClass == nullptr)
         Console::WriteLine("NULL");
   }
};

int main() {
   MyClass ^ x = gcnew MyClass();
   x -> Test();
}
```

```Output
NULL
```

## <a name="example-assign-nullptr-to-a-native-pointer"></a>예: `nullptr` 네이티브 포인터에 할당

다음 코드 예제에서는를 사용 하 여 **`nullptr`** 컴파일할 때를 네이티브 포인터에 할당할 수 있음을 보여 줍니다 `/clr` .

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>요구 사항

컴파일러 옵션: (필수 아님, 및를 비롯 한 모든 코드 생성 옵션에서 지원 됨 `/ZW` `/clr` )

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)
