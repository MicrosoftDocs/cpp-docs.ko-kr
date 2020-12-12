---
description: '자세한 정보: 제네릭 함수 (c + +/CLI)'
title: 제네릭 함수(C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
ms.openlocfilehash: cd2c5390499e6858824fae7a3368afe6de8c6c56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301739"
---
# <a name="generic-functions-ccli"></a>제네릭 함수(C++/CLI)

제네릭 함수는 형식 매개 변수를 사용하여 선언된 함수입니다. 제네릭 함수를 호출하면 형식 매개 변수 대신 실제 형식이 사용됩니다.

## <a name="all-platforms"></a>모든 플랫폼

### <a name="remarks"></a>설명

일부 플랫폼에는 이 기능이 적용되지 않습니다.

## <a name="windows-runtime"></a>Windows 런타임

### <a name="remarks"></a>설명

Windows 런타임에서는 이 기능이 지원되지 않습니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

제네릭 함수는 형식 매개 변수를 사용하여 선언된 함수입니다. 제네릭 함수를 호출하면 형식 매개 변수 대신 실제 형식이 사용됩니다.

### <a name="syntax"></a>구문

```cpp
[attributes] [modifiers]
return-type identifier<type-parameter identifier(s)>
[type-parameter-constraints clauses]

([formal-parameters])
{function-body}
```

### <a name="parameters"></a>매개 변수

*attributes*<br/>
(선택 사항) 추가 선언 정보입니다. 특성 및 특성 클래스에 대한 자세한 내용은 특성을 참조하세요.

*수정자*<br/>
(선택 사항) static 등의 함수 한정자입니다.  **`virtual`** 가상 메서드는 제네릭일 수 없으므로 허용 되지 않습니다.

*반환 형식*<br/>
메서드에서 반환되는 형식입니다. 반환 형식이 void이면 반환 값이 필요하지 않습니다.

*identifier*<br/>
함수 이름입니다.

*type-parameter identifier(s)*<br/>
쉼표로 구분된 식별자 목록입니다.

*formal-parameters*<br/>
(선택 사항) 매개 변수 목록입니다.

*type-parameter-constraints-clauses*<br/>
형식 인수로 사용할 수 있는 형식에 대한 제한을 지정하며, [제네릭 형식 매개 변수에 대한 제약 조건(C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)에 지정된 형식을 사용합니다.

*함수 본문*<br/>
형식 매개 변수 식별자를 참조할 수 있는 메서드 본문입니다.

### <a name="remarks"></a>설명

제네릭 함수는 제네릭 형식 매개 변수를 사용하여 선언된 함수입니다. 클래스 또는 구조체의 메서드이거나 독립 실행형 함수일 수 있습니다. 단일 제네릭 선언에서 제네릭 형식 매개 변수를 대체하는 실제 형식만 다른 함수 제품군을 암시적으로 선언합니다.

제네릭 형식 매개 변수를 사용하여 클래스 또는 구조체 생성자를 선언할 수 없습니다.

호출 시 제네릭 형식 매개 변수가 실제 형식으로 대체됩니다. 템플릿 함수 호출과 유사한 구문을 사용하여 꺾쇠 괄호 안에 실제 형식을 명시적으로 지정할 수 있습니다. 형식 매개 변수 없이 호출하면, 컴파일러에서 함수 호출에 제공된 매개 변수를 통해 실제 형식을 유추하려고 합니다. 사용된 매개 변수에서 의도한 형식 인수를 추론할 수 없는 경우 컴파일러에서 오류를 보고합니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예제

다음 코드 샘플에서는 제네릭 함수를 보여 줍니다.

```cpp
// generics_generic_function_1.cpp
// compile with: /clr
generic <typename ItemType>
void G(int i) {}

ref struct A {
   generic <typename ItemType>
   void G(ItemType) {}

   generic <typename ItemType>
   static void H(int i) {}
};

int main() {
   A myObject;

   // generic function call
   myObject.G<int>(10);

   // generic function call with type parameters deduced
   myObject.G(10);

   // static generic function call
   A::H<int>(10);

   // global generic function call
   G<int>(10);
}
```

시그니처 또는 인자 수, 함수의 형식 매개 변수 개수에 따라 제네릭 함수를 오버로드할 수 있습니다. 함수의 일부 형식 매개 변수가 다르기만 하면, 동일한 이름의 제네릭이 아닌 함수를 사용하여 제네릭 함수를 오버로드할 수도 있습니다. 예를 들어 다음 함수를 오버로드할 수 있습니다.

```cpp
// generics_generic_function_2.cpp
// compile with: /clr /c
ref struct MyClass {
   void MyMythod(int i) {}

   generic <class T>
   void MyMythod(int i) {}

   generic <class T, class V>
   void MyMythod(int i) {}
};
```

다음 예제에서는 제네릭 함수를 사용하여 배열의 첫 번째 요소를 찾습니다. 기본 클래스 `MyBaseClass`에서 상속받는 `MyClass`를 선언합니다. `MyClass`에 포함된 제네릭 함수 `MyFunction`은 기본 클래스 내에서 다른 제네릭 함수 `MyBaseClassFunction`을 호출합니다. `main`에서 다양한 형식 인수를 사용하여 제네릭 함수 `MyFunction`을 호출합니다.

```cpp
// generics_generic_function_3.cpp
// compile with: /clr
using namespace System;

ref class MyBaseClass {
protected:
   generic <class ItemType>
   ItemType MyBaseClassFunction(ItemType item) {
      return item;
   }
};

ref class MyClass: public MyBaseClass {
public:
   generic <class ItemType>
   ItemType MyFunction(ItemType item) {
      return MyBaseClass::MyBaseClassFunction<ItemType>(item);
   }
};

int main() {
   MyClass^ myObj = gcnew MyClass();

   // Call MyFunction using an int.
   Console::WriteLine("My function returned an int: {0}",
                           myObj->MyFunction<int>(2003));

   // Call MyFunction using a string.
   Console::WriteLine("My function returned a string: {0}",
   myObj->MyFunction<String^>("Hello generic functions!"));
}
```

```Output
My function returned an int: 2003
My function returned a string: Hello generic functions!
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)<br/>
[제네릭](generics-cpp-component-extensions.md)
