---
description: '자세한 정보: 제네릭 형식 매개 변수에 대 한 제약 조건 (c + +/CLI)'
title: 제네릭 형식 매개 변수에 대한 제약 조건(C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- where
helpviewer_keywords:
- where keyword [C++]
- constraints, C++
ms.assetid: eb828cc9-684f-48a3-a898-b327700c0a63
ms.openlocfilehash: c9e340c229736cbe1c679b931e52f68b0971f8f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333746"
---
# <a name="constraints-on-generic-type-parameters-ccli"></a>제네릭 형식 매개 변수에 대한 제약 조건(C++/CLI)

제네릭 형식 또는 메서드 선언에는 제약 조건이 있는 형식 매개 변수를 한정할 수 있습니다. 제약 조건은 형식 인수로 사용되는 형식이 충족해야 하는 요구 사항입니다. 예를 들어, 형식 인수가 특정 인터페이스를 구현하거나 특정 클래스에서 상속해야 제한할 수 있습니다.

제약 조건은 선택적입니다. 매개 변수에 제약 조건을 지정하지 않는 것은 해당 매개 변수를 <xref:System.Object>로 제한하는 것과 동일합니다.

## <a name="syntax"></a>구문

```cpp
where type-parameter: constraint list
```

### <a name="parameters"></a>매개 변수

*유형-매개 변수*<br/>
제한되는 형식 매개 변수 중 하나입니다.

*constraint list*<br/>
*constraint list* 는 제약 조건 사양의 쉼표로 구분된 목록입니다. 이 목록은 형식 매개 변수로 구현해야 하는 인터페이스를 포함할 수 있습니다.

이 목록은 클래스를 포함할 수도 있습니다. 형식 인수가 기본 클래스 제약 조건을 만족하려면 제약 조건과 같은 클래스이거나 제약 조건에서 파생되어야 합니다.

**gcnew()** 를 지정하여 형식 인수에 매개 변수가 없는 public 생성자가 있어야 함을 나타내거나, **ref class** 를 지정하여 형식 인수가 클래스, 인터페이스, 대리자 또는 배열 형식을 비롯한 참조 형식이어야 함을 나타내거나, **value class** 를 지정하여 형식 인수가 값 형식이어야 함을 나타낼 수도 있습니다. Nullable를 제외한 모든 값 형식을 \<T> 지정할 수 있습니다.

제네릭 매개 변수를 제약 조건으로 지정할 수도 있습니다. 제한된 형식에 대해 제공되는 형식 인수는 제약 조건의 형식이거나 제약 조건의 형식에서 파생되어야 합니다. 이를 naked 형식 제약 조건이라고 합니다.

## <a name="remarks"></a>설명

제약 조건 절은 **where**, 형식 매개 변수, 콜론(**:**), 형식 매개 변수에 대한 제한 특성을 지정하는 제약 조건을 순서대로 결합하여 구성합니다. **where** 는 상황에 맞는 키워드입니다. 자세한 내용은 [상황에 맞는 키워드](context-sensitive-keywords-cpp-component-extensions.md)를 참조하세요. **where** 절이 여러 개이면 공백으로 구분합니다.

제약 조건은 제네릭 형식 또는 메서드의 인수로 사용할 수 있는 형식에 대한 제한을 배치하기 위해 형식 매개 변수에 적용됩니다.

클래스 및 인터페이스 제약 조건은 인수 형식이 지정된 클래스이거나 지정된 클래스에서 상속되거나 지정된 인터페이스를 구현해야 함을 지정합니다.

제네릭 형식 또는 메서드에 제약 조건을 적용하면 해당 형식 또는 메서드의 코드에서 제약 조건이 있는 형식의 알려진 기능을 사용할 수 있습니다. 예를 들어 형식 매개 변수가 `IComparable<T>` 인터페이스를 구현하도록 제네릭 클래스를 선언할 수 있습니다.

```cpp
// generics_constraints_1.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : IComparable<T>
ref class List {};
```

이 제약 조건은 `T`에 사용되는 형식 인수가 컴파일 시간에 `IComparable<T>`을 구현하도록 요구합니다. 또한 `CompareTo`와 같은 인터페이스 메서드의 호출을 허용합니다. 인터페이스 메서드를 호출하기 위해 형식 매개 변수의 인스턴스를 캐스팅할 필요가 없습니다.

형식 인수의 클래스의 정적 메서드는 형식 매개 변수를 통해 호출할 수 없고, 실제 명명된 형식을 통해서만 호출할 수 있습니다.

제약 조건은 또는와 같은 기본 제공 형식을 포함 하는 값 형식일 수 없습니다 **`int`** **`double`** . 값 형식은 파생된 클래스를 가질 수 없기 때문에, 하나의 클래스만 제약 조건을 만족할 수 있을 것입니다. 이러한 경우에 해당 제네릭을 특정 값 형식으로 대체한 형식 매개 변수를 사용하여 다시 작성할 수 있습니다.

제약 조건은 알 수 없는 형식이 메서드나 인터페이스를 지원함을 나타내지 않을 경우 컴파일러에서 메서드나 알 수 없는 형식의 다른 기능을 사용할 수 없으므로 일부 경우에 있어 필요합니다.

동일한 형식 매개 변수에 대한 여러 제약 조건은 쉼표로 구분된 목록에 지정할 수 있습니다.

```cpp
// generics_constraints_2.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;
generic <typename T>
where T : List<T>, IComparable<T>
ref class List {};
```

형식 매개 변수가 여러 개이면, 형식 매개 변수마다 하나의 **where** 절을 사용합니다. 예를 들어:

```cpp
// generics_constraints_3.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;

generic <typename K, typename V>
   where K: IComparable<K>
   where V: IComparable<K>
ref class Dictionary {};
```

요약하면, 다음 규칙에 따라 코드에서 제약 조건을 사용합니다.

- 여러 제약 조건이 나열될 경우 순서에 상관없이 표시될 수 있습니다.

- 제약 조건은 추상 기본 클래스와 같은 클래스 형식일 수도 있습니다. 그러나 제약 조건은 값 형식 또는 sealed 클래스일 수 없습니다.

- 제약 조건 자체가 형식 매개 변수가 될 수 없지만, 개방형 생성 형식에 형식 매개 변수를 포함할 수 있습니다. 다음은 그 예입니다.

    ```cpp
    // generics_constraints_4.cpp
    // compile with: /c /clr
    generic <typename T>
    ref class G1 {};

    generic <typename Type1, typename Type2>
    where Type1 : G1<Type2>   // OK, G1 takes one type parameter
    ref class G2{};
    ```

## <a name="examples"></a>예

다음 예제에서는 제약 조건을 사용하여 형식 매개 변수에서 인스턴스 메서드를 호출하는 방법을 보여 줍니다.

```cpp
// generics_constraints_5.cpp
// compile with: /clr
using namespace System;

interface class IAge {
   int Age();
};

ref class MyClass {
public:
   generic <class ItemType> where ItemType : IAge
   bool isSenior(ItemType item) {
      // Because of the constraint,
      // the Age method can be called on ItemType.
      if (item->Age() >= 65)
         return true;
      else
         return false;
   }
};

ref class Senior : IAge {
public:
   virtual int Age() {
      return 70;
   }
};

ref class Adult: IAge {
public:
   virtual int Age() {
      return 30;
   }
};

int main() {
   MyClass^ ageGuess = gcnew MyClass();
   Adult^ parent = gcnew Adult();
   Senior^ grandfather = gcnew Senior();

   if (ageGuess->isSenior<Adult^>(parent))
      Console::WriteLine("\"parent\" is a senior");
   else
      Console::WriteLine("\"parent\" is not a senior");

   if (ageGuess->isSenior<Senior^>(grandfather))
      Console::WriteLine("\"grandfather\" is a senior");
   else
      Console::WriteLine("\"grandfather\" is not a senior");
}
```

```Output
"parent" is not a senior
"grandfather" is a senior
```

제네릭 형식 매개 변수를 제약 조건으로 사용하면 naked 형식 제약이라고 합니다. 고유한 형식 매개 변수가 있는 멤버 함수가 포함 형식의 형식 매개 변수에 해당 매개 변수를 제한할 필요가 있을 때 naked 형식 제약 조건이 유용합니다.

다음 예제에서 `T`는 `Add` 메서드 컨텍스트의 naked 형식 제약 조건입니다.

naked 형식 제약 조건은 제네릭 클래스 정의에서 사용할 수도 있습니다. 컴파일러에서는 naked 형식 제약 조건이 <xref:System.Object>에서 파생된다는 점을 제외하고는 이 제약 조건에 대해 어떠한 정보도 알 수 없으므로 제네릭 클래스가 있는 naked 형식 제약 조건의 유용성에는 한계가 있습니다. 두 형식 매개 변수 사이의 상속 관계를 적용하려는 시나리오에서 제네릭 클래스에 naked 형식 제약 조건을 사용합니다.

```cpp
// generics_constraints_6.cpp
// compile with: /clr /c
generic <class T>
ref struct List {
   generic <class U>
   where U : T
   void Add(List<U> items)  {}
};

generic <class A, class B, class C>
where A : C
ref struct SampleClass {};
```

## <a name="see-also"></a>참고 항목

[제네릭](generics-cpp-component-extensions.md)
