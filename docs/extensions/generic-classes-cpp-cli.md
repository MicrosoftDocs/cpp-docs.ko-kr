---
description: '자세한 정보: 제네릭 클래스 (c + +/CLI)'
title: 제네릭 클래스(C++/CLI)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], generic
- generic classes [C++], about generic classes
- data types [C++], generic
- generic classes
- generics [C++], declaring generic classes
ms.assetid: 0beb99e1-1ec4-4fee-9836-ce9657d67a3a
ms.openlocfilehash: 6b27f5220ab45fb62858bca2cec9ba0e46e9ec0a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301765"
---
# <a name="generic-classes-ccli"></a>제네릭 클래스(C++/CLI)

제네릭 클래스는 다음 형식을 사용하여 선언됩니다.

## <a name="syntax"></a>구문

```cpp
[attributes]
generic <class-key type-parameter-identifier(s)>
[constraint-clauses]
[accessibility-modifiers] ref class identifier  [modifiers]
[: base-list]
{
class-body
} [declarators] [;]
```

## <a name="remarks"></a>설명

위의 구문에서는 다음 용어가 사용되었습니다.

*attributes*<br/>
(선택 사항) 추가 선언 정보입니다. 특성 및 특성 클래스에 대한 자세한 내용은 특성을 참조하십시오.

*class-key*<br/>
또는 중 하나입니다. **`class`****`typename`**

*type-parameter-identifier(s)* - 형식 매개 변수의 이름을 지정하는 식별자의 쉼표로 구분된 목록입니다.

*constraint-clauses*<br/>
형식 매개 변수에 대한 제약 조건을 지정하는 **where** 절의 목록(쉼표로 구분되지 않음)입니다. 다음 형식을 사용합니다.

> **여기서** *형식 매개 변수-식별자* **:** *제약 조건 목록*  **...**

*constraint-list*<br/>
*클래스 또는 인터페이스*[ `,` *...*]

*accessibility-modifiers*<br/>
제네릭 클래스의 접근성 한정자입니다. Windows 런타임의 경우 유일 하 게 허용 되는 한정자는 **`private`** 입니다. 공용 언어 런타임의 경우 허용 되는 한정자는 **`private`** 및 **`public`** 입니다.

*identifier*<br/>
제네릭 클래스의 이름으로, 유효한 모든 C++ 식별자입니다.

*수정자*<br/>
(선택 사항) 허용되는 한정자는 **sealed** 및 **abstract** 입니다.

*base-list*<br/>
하나의 기본 클래스와 구현된 모든 인터페이스가 쉼표로 구분된 목록입니다.

*class-body*<br/>
필드, 멤버 함수 등을 포함하는 클래스 본문입니다.

*declarators*<br/>
이 형식의 모든 변수 선언입니다. 예: `^` *identifier*[ `,` ...]

이와 같은 제네릭 클래스를 선언할 수 있습니다. 대신 키워드를 사용할 수 있습니다 **`class`** **`typename`** . 이 예제에서 `ItemType`, `KeyType` 및 `ValueType`은 형식과 동일한 지점에서 지정된 알 수 없는 형식입니다. `HashTable<int, int>`는 제네릭 형식 `HashTable<KeyType, ValueType>`에서 생성된 형식입니다. 단일 제네릭 형식에서 다양한 생성된 형식을 생성할 수 있습니다. 제네릭 클래스에서 생성된 형식은 다른 ref 클래스 형식처럼 처리됩니다.

```cpp
// generic_classes_1.cpp
// compile with: /clr
using namespace System;
generic <typename ItemType>
ref struct Stack {
   // ItemType may be used as a type here
   void Add(ItemType item) {}
};

generic <typename KeyType, typename ValueType>
ref class HashTable {};

// The keyword class may be used instead of typename:
generic <class ListItem>
ref class List {};

int main() {
   HashTable<int, Decimal>^ g1 = gcnew HashTable<int, Decimal>();
}
```

두 값 형식 ( **`int`** 또는 **`double`** , 또는 사용자 정의 값 형식 등의 기본 제공 형식)과 참조 형식을 모두 제네릭 형식 인수로 사용할 수 있습니다. 제네릭 정의 내의 구문은 동일합니다. 구문상 알 수 없는 형식은 참조 형식인 것처럼 처리됩니다. 그러나 런타임에서 실제로 사용되는 형식이 값 형식인지 확인하고, 멤버에 직접 액세스하는 대신 적절하게 생성된 코드를 사용할 수 있습니다. 제네릭 형식 인수로 사용되는 값 형식은 boxing되지 않으므로 boxing과 관련된 성능 저하가 발생하지 않습니다. 제네릭 본문 내에서 사용되는 구문은 `.` 대신 `T^` 및 `->`이어야 합니다. 형식 매개 변수에 [ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md)를 사용하는 경우, 형식 인수가 값 형식이면 런타임에서 간단한 값 형식 생성으로 적절하게 해석됩니다.

형식 매개 변수에 사용할 수 있는 형식에서 [제네릭 형식 매개 변수에 대한 제약 조건(C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)을 사용하여 제네릭 클래스를 선언할 수도 있습니다. 다음 예제에서는 `ItemType`에 사용되는 모든 형식이 `IItem` 인터페이스를 구현해야 합니다. 예를 들어를 구현 하지 않는를 사용 하려고 하면 **`int`** `IItem` 형식 인수가 제약 조건을 충족 하지 않으므로 컴파일 시간 오류가 발생 합니다.

```cpp
// generic_classes_2.cpp
// compile with: /clr /c
interface class IItem {};
generic <class ItemType>
where ItemType : IItem
ref class Stack {};
```

동일한 네임스페이스의 제네릭 클래스를 형식 매개 변수의 개수나 형식만 변경하여 오버로드할 수 없습니다. 그러나 각 클래스가 다른 네임스페이스에 있는 경우에는 오버로드할 수 있습니다. 예를 들어 `MyClass` 및 `MyClass<ItemType>`이라는 두 클래스가 `A` 및 `B` 네임스페이스에 있다고 가정합니다. 이 경우 세 번째 네임스페이스 C에서 두 클래스를 오버로드할 수 있습니다.

```cpp
// generic_classes_3.cpp
// compile with: /clr /c
namespace A {
   ref class MyClass {};
}

namespace B {
   generic <typename ItemType>
   ref class MyClass2 { };
}

namespace C {
   using namespace A;
   using namespace B;

   ref class Test {
      static void F() {
         MyClass^ m1 = gcnew MyClass();   // OK
         MyClass2<int>^ m2 = gcnew MyClass2<int>();   // OK
      }
   };
}
```

기본 클래스와 기본 인터페이스는 형식 매개 변수가 될 수 없습니다. 그러나 다음 경우와 같이 기본 클래스에서 형식 매개 변수를 인수로 사용할 수 있습니다.

```cpp
// generic_classes_4.cpp
// compile with: /clr /c
generic <typename ItemType>
interface class IInterface {};

generic <typename ItemType>
ref class MyClass : IInterface<ItemType> {};
```

생성자와 소멸자는 평소대로 각 개체 인스턴스에 대해 한 번 실행되고, 정적 생성자는 생성된 각 형식에 대해 한 번 실행됩니다.

## <a name="fields-in-generic-classes"></a>제네릭 클래스의 필드

이 섹션에서는 제네릭 클래스에 인스턴스 및 정적 필드를 사용하는 방법을 보여 줍니다.

### <a name="instance-variables"></a>인스턴스 변수

제네릭 클래스의 인스턴스 변수에 바깥쪽 클래스의 형식 매개 변수가 포함된 형식 및 변수 이니셜라이저를 사용할 수 있습니다.

## <a name="example-different-generic-classes"></a>예: 다른 제네릭 클래스

다음 예제에서는 \<ItemType> 적절 한 형식 인수 ( **`int`** , **`double`** 및 **문자열**)를 사용 하 여 제네릭 클래스 MyClass의 세 가지 인스턴스를 만듭니다.

```cpp
// generics_instance_fields1.cpp
// compile with: /clr
// Instance fields on generic classes
using namespace System;

generic <typename ItemType>
ref class MyClass {
// Field of the type ItemType:
public :
   ItemType field1;
   // Constructor using a parameter of the type ItemType:
   MyClass(ItemType p) {
   field1 = p;
   }
};

int main() {
   // Instantiate an instance with an integer field:
   MyClass<int>^ myObj1 = gcnew MyClass<int>(123);
   Console::WriteLine("Integer field = {0}", myObj1->field1);

   // Instantiate an instance with a double field:
   MyClass<double>^ myObj2 = gcnew MyClass<double>(1.23);
   Console::WriteLine("Double field = {0}", myObj2->field1);

   // Instantiate an instance with a String field:
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>("ABC");
   Console::WriteLine("String field = {0}", myObj3->field1);
   }
```

```Output
Integer field = 123
Double field = 1.23
String field = ABC
```

## <a name="static-variables"></a>정적 변수

새 제네릭 형식을 만들 때 모든 정적 변수의 새 인스턴스가 생성되고, 해당 형식의 정적 생성자가 모두 실행됩니다.

정적 변수는 바깥쪽 클래스의 형식 매개 변수를 모두 사용할 수 있습니다.

## <a name="example-use-static-variables"></a>예: 정적 변수 사용

다음 예제에서는 제네릭 클래스 내에서 정적 필드 및 정적 생성자를 사용하는 방법을 보여 줍니다.

```cpp
// generics_static2.cpp
// compile with: /clr
using namespace System;

interface class ILog {
   void Write(String^ s);
};

ref class DateTimeLog : ILog {
public:
   virtual void Write(String^ s) {
      Console::WriteLine( "{0}\t{1}", DateTime::Now, s);
   }
};

ref class PlainLog : ILog {
public:
   virtual void Write(String^ s) { Console::WriteLine(s); }
};

generic <typename LogType>
where LogType : ILog
ref class G {
   static LogType s_log;

public:
   G(){}
   void SetLog(LogType log) { s_log = log; }
   void F() { s_log->Write("Test1"); }
   static G() { Console::WriteLine("Static constructor called."); }
};

int main() {
   G<PlainLog^>^ g1 = gcnew G<PlainLog^>();
   g1->SetLog(gcnew PlainLog());
   g1->F();

   G<DateTimeLog^>^ g2 = gcnew G<DateTimeLog^>();
   g2->SetLog(gcnew DateTimeLog());

   // prints date
   // g2->F();
}
```

```Output
Static constructor called.
Static constructor called.
Static constructor called.
Test1
```

## <a name="methods-in-generic-classes"></a>제네릭 클래스의 메서드

제네릭 클래스의 메서드 자체도 제네릭일 수 있습니다. 제네릭이 아닌 메서드는 클래스 형식 매개 변수에 의해 암시적으로 매개 변수화됩니다.

제네릭 클래스 내의 메서드에는 다음과 같은 특수 규칙이 적용됩니다.

- 제네릭 클래스의 메서드는 형식 매개 변수를 매개 변수, 반환 형식 또는 지역 변수로 사용할 수 있습니다.

- 제네릭 클래스의 메서드는 생성된 개방형 또는 폐쇄형 형식을 매개 변수, 반환 형식 또는 지역 변수로 사용할 수 있습니다.

### <a name="non-generic-methods-in-generic-classes"></a>제네릭 클래스의 제네릭이 아닌 메서드

추가적인 형식 매개 변수가 없는 제네릭 클래스의 메서드는 바깥쪽 제네릭 클래스에 의해 암시적으로 매개 변수화되지만, 일반적으로 제네릭이 아닌 것으로 참조됩니다.

제네릭이 아닌 메서드의 시그니처에는 바깥쪽 클래스의 형식 매개 변수가 직접 또는 생성된 개방형 형식을 통해 하나 이상 포함될 수 있습니다. 예를 들어:

`void MyMethod(MyClass<ItemType> x) {}`

해당 메서드의 본문에서도 이러한 형식 매개 변수를 사용할 수 있습니다.

## <a name="example-declare-non-generic-method"></a>예제: 제네릭이 아닌 메서드 선언

다음 예제에서는 제네릭 클래스 `MyClass<ItemType>` 내에서 제네릭이 아닌 메서드 `ProtectData`를 선언합니다. 이 메서드는 생성된 개방형 형식을 통해 시그니처에 클래스 형식 매개 변수 `ItemType`을 사용합니다.

```cpp
// generics_non_generic_methods1.cpp
// compile with: /clr
// Non-generic methods within a generic class.
using namespace System;

generic <typename ItemType>
ref class MyClass {
public:
   String^ name;
   ItemType data;

   MyClass(ItemType x) {
      data = x;
   }

   // Non-generic method using the type parameter:
   virtual void ProtectData(MyClass<ItemType>^ x) {
      data = x->data;
   }
};

// ItemType defined as String^
ref class MyMainClass: MyClass<String^> {
public:
   // Passing "123.00" to the constructor:
   MyMainClass(): MyClass<String^>("123.00") {
      name = "Jeff Smith";
   }

   virtual void ProtectData(MyClass<String^>^ x) override {
      x->data = String::Format("${0}**", x->data);
   }

   static void Main() {
      MyMainClass^ x1 = gcnew MyMainClass();

      x1->ProtectData(x1);
      Console::WriteLine("Name: {0}", x1->name);
      Console::WriteLine("Amount: {0}", x1->data);
   }
};

int main() {
   MyMainClass::Main();
}
```

```Output
Name: Jeff Smith
Amount: $123.00**
```

## <a name="generic-methods-in-generic-classes"></a>제네릭 클래스의 제네릭 메서드

제네릭 클래스와 제네릭이 아닌 클래스 둘 다에서 제네릭 메서드를 선언할 수 있습니다. 예를 들어:

## <a name="example-declare-generic-and-non-generic-methods"></a>예제: 제네릭 및 제네릭이 아닌 메서드 선언

```cpp
// generics_method2.cpp
// compile with: /clr /c
generic <typename Type1>
ref class G {
public:
   // Generic method having a type parameter
   // from the class, Type1, and its own type
   // parameter, Type2
   generic <typename Type2>
   void Method1(Type1 t1, Type2 t2) { F(t1, t2); }

   // Non-generic method:
   // Can use the class type param, Type1, but not Type2.
   void Method2(Type1 t1) { F(t1, t1); }

   void F(Object^ o1, Object^ o2) {}
};
```

제네릭이 아닌 메서드도 클래스의 형식 매개 변수에 의해 매개 변수화된다는 점에서 제네릭이지만, 추가적인 형식 매개 변수가 없습니다.

정적, 인스턴스, 가상 메서드 등 제네릭 클래스의 모든 메서드 유형이 제네릭일 수 있습니다.

## <a name="example-declare-and-use-generic-methods"></a>예제: 제네릭 메서드 선언 및 사용

다음 예제에서는 제네릭 클래스 내에서 제네릭 메서드를 선언하고 사용하는 방법을 보여 줍니다.

```cpp
// generics_generic_method2.cpp
// compile with: /clr
using namespace System;
generic <class ItemType>
ref class MyClass {
public:
   // Declare a generic method member.
   generic <class Type1>
   String^ MyMethod(ItemType item, Type1 t) {
      return String::Concat(item->ToString(), t->ToString());
   }
};

int main() {
   // Create instances using different types.
   MyClass<int>^ myObj1 = gcnew MyClass<int>();
   MyClass<String^>^ myObj2 = gcnew MyClass<String^>();
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>();

   // Calling MyMethod using two integers.
   Console::WriteLine("MyMethod returned: {0}",
            myObj1->MyMethod<int>(1, 2));

   // Calling MyMethod using an integer and a string.
   Console::WriteLine("MyMethod returned: {0}",
            myObj2->MyMethod<int>("Hello #", 1));

   // Calling MyMethod using two strings.
   Console::WriteLine("MyMethod returned: {0}",
       myObj3->MyMethod<String^>("Hello ", "World!"));

   // generic methods can be called without specifying type arguments
   myObj1->MyMethod<int>(1, 2);
   myObj2->MyMethod<int>("Hello #", 1);
   myObj3->MyMethod<String^>("Hello ", "World!");
}
```

```Output
MyMethod returned: 12
MyMethod returned: Hello #1
MyMethod returned: Hello World!
```

## <a name="using-nested-types-in-generic-classes"></a>제네릭 클래스에 중첩 형식 사용

일반 클래스와 마찬가지로 제네릭 클래스 내에서 다른 형식을 선언할 수 있습니다. 중첩 클래스 선언은 외부 클래스 선언의 형식 매개 변수에 의해 암시적으로 매개 변수화됩니다. 따라서 생성된 각 외부 형식에 대해 고유한 중첩 클래스가 정의됩니다. 예를 들어 다음과 같은 선언이 있다고 가정합니다.

```cpp
// generic_classes_5.cpp
// compile with: /clr /c
generic <typename ItemType>
ref struct Outer {
   ref class Inner {};
};
```

`Outer<int>::Inner` 형식은 `Outer<double>::Inner` 형식과 다릅니다.

제네릭 클래스의 제네릭 메서드와 마찬가지로, 중첩 형식에 대해 추가적인 형식 매개 변수를 정의할 수 있습니다. 내부 및 외부 클래스에 동일한 형식 매개 변수 이름을 사용하면 내부 형식 매개 변수가 외부 형식 매개 변수를 숨깁니다.

```cpp
// generic_classes_6.cpp
// compile with: /clr /c
generic <typename ItemType>
ref class Outer {
   ItemType outer_item;   // refers to outer ItemType

   generic <typename ItemType>
   ref class Inner {
      ItemType inner_item;   // refers to Inner ItemType
   };
};
```

외부 형식 매개 변수를 참조할 수 없으므로 이 경우 컴파일러에서 경고가 발생합니다.

생성된 중첩 제네릭 형식을 명명하는 경우, 내부 형식이 외부 형식의 형식 매개 변수에 의해 암시적으로 매개 변수화되었더라도 내부 형식의 형식 매개 변수 목록에 외부 형식의 형식 매개 변수가 포함되지 않습니다. 위의 경우에서 생성된 형식의 이름은 `Outer<int>::Inner<string>`가 됩니다.

## <a name="example-build-and-read-linked-list"></a>예: 빌드 및 링크 된 목록 읽기

다음 예제에서는 제네릭 클래스에 중첩 형식을 사용하여 연결된 목록을 작성하고 읽는 방법을 보여 줍니다.

```cpp
// generics_linked_list.cpp
// compile with: /clr
using namespace System;
generic <class ItemType>
ref class LinkedList {
// The node class:
public:
   ref class Node {
   // The link field:
   public:
      Node^ next;
      // The data field:
      ItemType item;
   } ^first, ^current;
};

ref class ListBuilder {
public:
   void BuildIt(LinkedList<double>^ list) {
      /* Build the list */
      double m[5] = {0.1, 0.2, 0.3, 0.4, 0.5};
      Console::WriteLine("Building the list:");

      for (int n=0; n<=4; n++) {
         // Create a new node:
         list->current = gcnew LinkedList<double>::Node();

         // Assign a value to the data field:
         list->current->item = m[n];

         // Set the link field "next" to be the same as
         // the "first" field:
         list->current->next = list->first;

         // Redirect "first" to the new node:
         list->first = list->current;

         // Display node's data as it builds:
         Console::WriteLine(list->current->item);
      }
   }

   void ReadIt(LinkedList<double>^ list) {
      // Read the list
      // Make "first" the "current" link field:
      list->current = list->first;
      Console::WriteLine("Reading nodes:");

      // Read nodes until current == null:
      while (list->current != nullptr) {
         // Display the node's data field:
         Console::WriteLine(list->current->item);

         // Move to the next node:
         list->current = list->current->next;
      }
   }
};

int main() {
   // Create a list:
   LinkedList<double>^ aList = gcnew LinkedList<double>();

   // Initialize first node:
   aList->first = nullptr;

   // Instantiate the class, build, and read the list:
   ListBuilder^ myListBuilder = gcnew ListBuilder();
   myListBuilder->BuildIt(aList);
   myListBuilder->ReadIt(aList);
}
```

```Output
Building the list:
0.1
0.2
0.3
0.4
0.5
Reading nodes:
0.5
0.4
0.3
0.2
0.1
```

## <a name="properties-events-indexers-and-operators-in-generic-classes"></a>제네릭 클래스의 속성, 이벤트, 인덱서 및 연산자

- `ItemType`이 클래스의 형식 매개 변수인 경우와 같이 속성, 이벤트, 인덱서 및 연산자가 바깥쪽 제네릭 클래스의 형식 매개 변수를 반환 값, 매개 변수 또는 지역 변수로 사용할 수 있습니다.

    ```cpp
    public ItemType MyProperty {}
    ```

- 속성, 이벤트, 인덱서 및 연산자 자체는 매개 변수화할 수 없습니다.

## <a name="example-declare-instance-property"></a>예: instance 속성 선언

이 예제에서는 제네릭 클래스 내의 인스턴스 속성 선언을 보여 줍니다.

```cpp
// generics_generic_properties1.cpp
// compile with: /clr
using namespace System;

generic <typename ItemType>
ref class MyClass {
private:
   property ItemType myField;

public:
   property ItemType MyProperty {
      ItemType get() {
         return myField;
      }
      void set(ItemType value) {
         myField = value;
      }
   }
};

int main() {
   MyClass<String^>^ c = gcnew MyClass<String^>();
   MyClass<int>^ c1 = gcnew MyClass<int>();

   c->MyProperty = "John";
   c1->MyProperty = 234;

   Console::Write("{0}, {1}", c->MyProperty, c1->MyProperty);
}
```

```Output
John, 234
```

## <a name="example-generic-class-with-event"></a>예: 이벤트를 포함 하는 제네릭 클래스

다음 예제에서는 이벤트가 포함된 제네릭 클래스를 보여 줍니다.

```cpp
// generics_generic_with_event.cpp
// compile with: /clr
// Declare a generic class with an event and
// invoke events.
using namespace System;

// declare delegates
generic <typename ItemType>
delegate void ClickEventHandler(ItemType);

// generic class that defines events
generic <typename ItemType>
ref class EventSource {
public:
   // declare the event OnClick
   event ClickEventHandler<ItemType>^ OnClick;
   void FireEvents(ItemType item) {
      // raises events
      OnClick(item);
   }
};

// generic class that defines methods that will called when
// event occurs
generic <typename ItemType>
ref class EventReceiver {
public:
   void OnMyClick(ItemType item) {
   Console::WriteLine("OnClick: {0}", item);
   }
};

int main() {
   EventSource<String^>^ MyEventSourceString =
                   gcnew EventSource<String^>();
   EventSource<int>^ MyEventSourceInt = gcnew EventSource<int>();
   EventReceiver<String^>^ MyEventReceiverString =
                   gcnew EventReceiver<String^>();
   EventReceiver<int>^ MyEventReceiverInt = gcnew EventReceiver<int>();

   // hook handler to event
   MyEventSourceString->OnClick += gcnew ClickEventHandler<String^>(
       MyEventReceiverString, &EventReceiver<String^>::OnMyClick);
   MyEventSourceInt->OnClick += gcnew ClickEventHandler<int>(
             MyEventReceiverInt, &EventReceiver<int>::OnMyClick);

   // invoke events
   MyEventSourceString->FireEvents("Hello");
   MyEventSourceInt->FireEvents(112);

   // unhook handler to event
   MyEventSourceString->OnClick -= gcnew ClickEventHandler<String^>(
        MyEventReceiverString, &EventReceiver<String^>::OnMyClick);
   MyEventSourceInt->OnClick -= gcnew ClickEventHandler<int>(
        MyEventReceiverInt, &EventReceiver<int>::OnMyClick);
}
```

## <a name="generic-structs"></a>제네릭 구조체

Visual C++ 언어 참조에 명시된 차이점을 제외하고, 제네릭 구조체 선언 및 사용 규칙은 제네릭 클래스와 같습니다.

## <a name="example-declare-generic-struct"></a>예제: 제네릭 구조체 선언

다음 예제에서는 하나의 필드인를 사용 하 여 제네릭 구조체를 선언 `MyGenStruct` `myField` 하 고 다른 형식 ( **`int`** ,,)의 값을 **`double`** `String^` 이 필드에 할당 합니다.

```cpp
// generics_generic_struct1.cpp
// compile with: /clr
using namespace System;

generic <typename ItemType>
ref struct MyGenStruct {
public:
   ItemType myField;

   ItemType AssignValue(ItemType item) {
      myField = item;
      return myField;
   }
};

int main() {
   int myInt = 123;
   MyGenStruct<int>^ myIntObj = gcnew MyGenStruct<int>();
   myIntObj->AssignValue(myInt);
   Console::WriteLine("The field is assigned the integer value: {0}",
            myIntObj->myField);

   double myDouble = 0.123;
   MyGenStruct<double>^ myDoubleObj = gcnew MyGenStruct<double>();
   myDoubleObj->AssignValue(myDouble);
   Console::WriteLine("The field is assigned the double value: {0}",
            myDoubleObj->myField);

   String^ myString = "Hello Generics!";
   MyGenStruct<String^>^ myStringObj = gcnew MyGenStruct<String^>();
   myStringObj->AssignValue(myString);
   Console::WriteLine("The field is assigned the string: {0}",
            myStringObj->myField);
}
```

```Output
The field is assigned the integer value: 123
The field is assigned the double value: 0.123
The field is assigned the string: Hello Generics!
```

## <a name="see-also"></a>참고 항목

[제네릭](generics-cpp-component-extensions.md)
