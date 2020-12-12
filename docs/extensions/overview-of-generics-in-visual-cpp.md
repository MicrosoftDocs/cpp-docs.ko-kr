---
description: '자세한 정보: c + +/CLI의 제네릭 개요'
title: C++/CLI의 제네릭 개요
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], about generics
- default initializers [C++]
- type parameters [C++]
- constructed types
- type arguments [C++]
- constructed types, open [C++]
- open constructed types [C++]
- constructed types, closed [C++]
ms.assetid: 21f10637-0fce-4916-b925-6c86a126d3aa
ms.openlocfilehash: 4b84d16f7d76824f732865e3bf8b7bbfe674a1bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274153"
---
# <a name="overview-of-generics-in-ccli"></a>C++/CLI의 제네릭 개요

제네릭은 공용 언어 런타임에서 지원하는 매개 변수화된 형식입니다. 매개 변수화된 형식은 제네릭이 사용될 때 지정되는 알 수 없는 형식 매개 변수로 정의된 형식입니다.

## <a name="why-generics"></a>왜 제네릭인가?

C++은 템플릿을 지원하고 템플릿과 제네릭은 모두 매개 변수화된 형식을 지원하여 형식화된 컬렉션 클래스를 만듭니다. 그러나 템플릿은 컴파일 타임 매개 변수화를 제공합니다. 템플릿 정의가 포함된 어셈블리를 참조하고 해당 템플릿의 새 특수화를 만들 수는 없습니다. 컴파일되면 특수화된 템플릿은 다른 클래스나 메서드처럼 보입니다. 반면에, 제네릭은 매개 변수화된 형식이 되기 위해 런타임으로 알려진 매개 변수화된 형식으로 MSIL에서 출력됩니다. 제네릭 형식이 포함된 어셈블리를 참조하는 소스 코드는 특수화된 제네릭 형식을 만들 수 있습니다. 표준 C++ 템플릿과 제네릭의 비교에 대한 자세한 내용은 [제네릭 및 템플릿(C++/CLI)](generics-and-templates-visual-cpp.md)을 참조하세요.

## <a name="generic-functions-and-types"></a>제네릭 함수 및 형식

클래스 형식은 관리되는 형식인 경우 제네릭일 수 있습니다. 이러한 경우에 대한 예로 `List` 클래스를 들 수 있습니다. 목록에 있는 개체의 형식은 형식 매개 변수입니다. 다양한 개체 형식에 대한 `List` 클래스가 필요한 경우, 제네릭 이전에 항목 종류로 `System::Object`를 사용하는 `List`를 사용했을 수도 있습니다. 하지만 그런 경우 모든 개체(잘못된 형식의 개체 포함)를 목록에서 사용할 수 있도록 허용하게 됩니다. 그러한 목록은 형식화되지 않은 컬렉션 클래스라고 합니다. 기껏해야 런타임에서 형식을 확인하고 예외를 throw할 수 있습니다. 또는 어셈블리로 컴파일되면 제네릭 품질을 잃을 수 있는 템플릿을 사용했을 수도 있습니다. 어셈블리의 소비자는 직접 템플릿의 특수화를 만들 수 없습니다. 제네릭을 사용하면, 컬렉션에서 적용되도록 설계되지 않은 형식을 형식화된 컬렉션에 배치하려고 할 경우 컴파일 시간 오류를 생성하는 `List<int>`(“List of int”), `List<double>`(“List of double”) 등의 형식화된 컬렉션 클래스를 만들 수 있습니다. 또한, 이러한 형식은 컴파일된 후 제네릭으로 남아 있습니다.

제네릭 클래스의 구문 설명은 [제네릭 클래스(C++/CLI)](generic-classes-cpp-cli.md)에서 확인할 수 있습니다. 새로운 <xref:System.Collections.Generic> 네임스페이스는 <xref:System.Collections.Generic.Dictionary%602>, <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>를 포함하여 매개 변수가 있는 컬렉션 형식 집합을 도입합니다.

인스턴스 및 정적 클래스 멤버 함수, 대리자 및 전역 함수도 제네릭일 수 있습니다. 제네릭 함수는 함수의 매개 변수가 알 수 없는 형식이거나 함수 자체에서 제네릭 형식으로 작업해야 할 경우 필요할 수 있습니다. 이전에 알 수 없는 개체 형식의 매개 변수로 `System::Object`를 사용했던 대부분의 경우에 제네릭 형식 매개 변수를 대신 사용하여 보다 형식이 안전한 코드를 만들 수 있습니다. 함수에 사용할 수 없는 형식으로 전달하려는 시도는 컴파일 타임에 오류로 플래그가 지정될 수 있습니다. `System::Object`를 함수 매개 변수로 사용하면 함수에서 처리할 수 없는 개체가 실수로 전달되는 경우를 감지할 수 없으며, 함수 본문에서 알 수 없는 개체 형식을 특정 형식으로 캐스팅하고 InvalidCastException의 가능성을 고려해야 합니다. 제네릭을 사용하여, 개체를 함수에 전달하려는 코드 시도는 형식 충돌을 일으켜서 함수 본문은 올바른 형식을 갖도록 보장됩니다.

동일한 이점은 제네릭을 기반으로 하는 컬렉션 클래스에도 적용됩니다. 이전의 컬렉션 클래스는 `System::Object`를 사용하여 컬렉션에 요소를 저장했습니다. 컬렉션에 사용되지 않는 형식의 개체 삽입은 컴파일 타임에 플래그가 지정되지 않았고 심지어 개체가 삽입될 때에도 대개 플래그 지정되지 않았습니다. 일반적으로, 개체는 컬렉션에서 액세스하는 경우 일부 다른 형식으로 캐스팅될 것입니다. 캐스팅에 실패했을 때만 예기치 않은 형식이 감지됩니다. 제네릭은 컴파일 타임에 제네릭 컬렉션의 형식 매개 변수와 일치하지 않는 (또는 암시적으로 변환) 형식을 삽입하는 코드를 감지함으로써 이 문제를 해결합니다.

구문 설명은 [제네릭 함수(C++/CLI)](generic-functions-cpp-cli.md)를 참조하세요.

## <a name="terminology-used-with-generics"></a>제네릭을 사용하는 용어

### <a name="type-parameters"></a>형식 매개 변수

제네릭 선언에는 ‘형식 매개 변수’라는 알 수 없는 형식이 하나 이상 포함되어 있습니다. 형식 매개 변수는 제네릭 선언의 본문 안에 있는 형식을 나타내는 이름 입니다. 형식 매개 변수는 제네릭 선언의 본문 안에 있는 형식으로 사용됩니다. `List<T>`에 대한 제네릭 선언은 형식 매개 변수 T를 포함합니다.

### <a name="type-arguments"></a>형식 인수

‘형식 인수’는 제네릭이 하나 이상의 특정 형식용으로 특별히 고안된 경우 형식 매개 변수 대신 사용되는 실제 형식입니다. 예를 들어 **`int`** 는의 형식 인수입니다 `List<int>` . 값 형식과 핸들 형식은 제네릭 형식 인수로 허용 되는 유일한 형식입니다.

### <a name="constructed-type"></a>생성된 형식

제네릭 형식에서 생성된 형식을 ‘생성된 형식’이라고 합니다. `List<T>`와 같이 완전히 지정되지 않은 형식은 ‘개방형 생성 형식’이고, `List<double>,`과 같이 완전히 지정된 형식은 ‘폐쇄형 생성 형식’ 또는 ‘특수화된 형식’입니다. 개방형 생성 형식이 다른 제네릭 형식 또는 메서드 정의에 사용될 수 있고 바깥쪽 제네릭 자체가 지정될 때까지 완전히 지정되지 않습니다. 예를 들어, 다음은 제네릭에 대한 기본 클래스로 개방형 생성 형식의 사용입니다.

```cpp
// generics_overview.cpp
// compile with: /clr /c
generic <typename T>

ref class List {};

generic <typename T>

ref class Queue : public List<T> {};
```

### <a name="constraint"></a>제약 조건

제약 조건은 형식 매개 변수로 사용할 수 있는 형식에 대한 제한입니다. 예를 들어, 주어진 제네릭 클래스는 지정된 클래스에서 상속되는 클래스만 허용되고 지정된 인터페이스를 구현할 수 있습니다. 자세한 내용은 [제네릭 형식 매개 변수에 대한 제약 조건(C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)을 참조하세요.

## <a name="reference-types-and-value-types"></a>참조 형식 및 값 형식

핸들 형식 및 값 형식을 형식 인수로 사용할 수 있습니다. 어느 한 형식이 사용될 수 있는 제네릭 정의에서 구문은 참조 형식입니다. 예를 들어 `->` 연산자는 궁극적으로 사용되는 형식이 참조 형식인지, 값 형식인지에 관계없이 형식 매개 변수의 형식 멤버에 액세스하는 데 사용됩니다. 값 형식이 형식 인수로 사용되면, 런타임은 값 형식을 직접 boxing하지 않고 값 형식을 사용하는 코드를 생성합니다.

참조 형식을 제네릭 형식 인수로 사용하는 경우, 핸들 구문을 사용합니다. 값 형식을 제네릭 형식 인수로 사용할 경우, 직접 형식 이름을 사용합니다.

```cpp
// generics_overview_2.cpp
// compile with: /clr
generic <typename T>

ref class GenericType {};
ref class ReferenceType {};

value struct ValueType {};

int main() {
    GenericType<ReferenceType^> x;
    GenericType<ValueType> y;
}
```

## <a name="type-parameters"></a>형식 매개 변수

제네릭 클래스의 형식 매개 변수는 다른 식별자처럼 취급됩니다. 그러나, 형식을 알 수 없기 때문에 사용에 제한이 있습니다. 예를 들어, 이러한 멤버를 지원하기 위해 형식 매개 변수가 알려지지 않은 경우 형식 매개 변수 클래스의 멤버와 메서드를 사용할 수 없습니다. 즉, 형식 매개 변수를 통해 멤버에 액세스하려면 멤버를 포함한 형식을 형식 매개 변수의 제약 조건 목록에 추가해야 합니다.

```cpp
// generics_overview_3.cpp
// compile with: /clr
interface class I {
   void f1();
   void f2();
};

ref struct R : public I {
   virtual void f1() {}
   virtual void f2() {}
   virtual void f3() {}
};

generic <typename T>
where T : I
void f(T t) {
   t->f1();
   t->f2();
   safe_cast<R^>(t)->f3();
}

int main() {
   f(gcnew R());
}
```

이러한 제한은 연산자에도 적용됩니다. 제한되지 않은 제네릭 형식 매개 변수는 `==` 및 `!=` 연산자를 지원하지 않는 형식인 경우에 형식 매개 변수의 두 인스턴스를 비교하기 위해 사용하지 않습니다. 이러한 검사는 템플릿이 아닌 제네릭에 필요합니다. 제네릭은 유효하지 않은 멤버 사용을 확인하기에 너무 늦을 때, 런타임에 제약 조건을 만족시키는 클래스를 사용하여 특수화될 수 있기 때문입니다.

형식 매개 변수의 기본 인스턴스는 `()` 연산자를 사용하여 만들어질 수 있습니다. 예를 들어:

`T t = T();`

여기서 `T`는 제네릭 클래스 또는 메서드 정의에서 형식 매개 변수로, 변수를 기본값으로 초기화합니다. `T`가 ref 클래스인 경우, null 포인터가 됩니다. `T`가 값 클래스인 경우, 개체가 0으로 초기화됩니다. 이 프로세스를 ‘기본 이니셜라이저’라고 합니다.

## <a name="see-also"></a>참고 항목

[제네릭](generics-cpp-component-extensions.md)
