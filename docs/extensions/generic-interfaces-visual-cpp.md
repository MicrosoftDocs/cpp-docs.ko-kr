---
description: '자세한 정보: 제네릭 인터페이스 (c + +/CLI)'
title: 제네릭 인터페이스(C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generic interfaces
- interfaces, generic [C++}
ms.assetid: f3da788a-ba83-4db7-9dcf-9b95a8fb9d1a
ms.openlocfilehash: 7ba7cec76d23262977180a050326a0c5cf2966e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301700"
---
# <a name="generic-interfaces-ccli"></a>제네릭 인터페이스(C++/CLI)

클래스의 형식 매개 변수에 적용되는 제한은 인터페이스의 형식 매개 변수에 적용되는 제한과 같습니다([제네릭 클래스(C++/CLI)](generic-classes-cpp-cli.md) 참조).

함수 오버로드를 제어하는 규칙은 제네릭 클래스 내의 함수 또는 제네릭 인터페이스 내의 함수에서 동일합니다.

명시적 인터페이스 멤버 구현은 단순 인터페이스 형식(다음 예제 참조)과 생성된 인터페이스 형식에서 동일한 방식으로 실행됩니다.

인터페이스에 대한 자세한 내용은 [인터페이스 클래스](interface-class-cpp-component-extensions.md)를 참조하세요.

## <a name="syntax"></a>구문

```cpp
[attributes] generic <class-key type-parameter-identifier[, ...]>
[type-parameter-constraints-clauses][accesibility-modifiers] interface class identifier [: base-list] {   interface-body} [declarators] ;
```

## <a name="remarks"></a>설명

*attributes*<br/>
(선택 사항) 추가 선언 정보입니다. 특성 및 특성 클래스에 대한 자세한 내용은 **특성** 을 참조하세요.

*class-key*<br/>
**`class`** 또는 **`typename`**

*type-parameter-identifier(s)*<br/>
쉼표로 구분된 식별자 목록입니다.

*type-parameter-constraints-clauses*<br/>
[제네릭 형식 매개 변수에 대한 제약 조건(C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)에 지정된 형식을 사용합니다.

*accessibility-modifiers*<br/>
필드 액세스 가능성 한정자 (예: **public, private**).

*identifier*<br/>
인터페이스 이름입니다.

*base-list*<br/>
(선택 사항) 하나 이상의 명시적 기본 인터페이스가 쉼표로 구분된 목록입니다.

*interface-body*<br/>
인터페이스 멤버 선언입니다.

*declarators*<br/>
(선택 사항) 이 형식을 기반으로 하는 변수 선언입니다.

## <a name="example-how-to-declare-and-instantiate-a-generic-interface"></a>예: 제네릭 인터페이스를 선언 하 고 인스턴스화하는 방법

다음 예제에서는 제네릭 인터페이스를 선언하고 인스턴스화하는 방법을 보여 줍니다. 예제에서는 제네릭 인터페이스 `IList<ItemType>`을 선언합니다. 그런 다음, 두 제네릭 클래스 `List1<ItemType>` 및 `List2<ItemType>`에서 서로 다른 구현을 사용하여 구현합니다.

```cpp
// generic_interface.cpp
// compile with: /clr
using namespace System;

// An exception to be thrown by the List when
// attempting to access elements beyond the
// end of the list.
ref class ElementNotFoundException : Exception {};

// A generic List interface
generic <typename ItemType>
public interface class IList {
   ItemType MoveFirst();
   bool Add(ItemType item);
   bool AtEnd();
   ItemType Current();
   void MoveNext();
};

// A linked list implementation of IList
generic <typename ItemType>
public ref class List1 : public IList<ItemType> {
   ref class Node {
      ItemType m_item;

   public:
      ItemType get_Item() { return m_item; };
      void set_Item(ItemType value) { m_item = value; };

      Node^ next;

      Node(ItemType item) {
         m_item = item;
         next = nullptr;
      }
   };

   Node^ first;
   Node^ last;
   Node^ current;

   public:
   List1() {
      first = nullptr;
      last = first;
      current = first;
   }

   virtual ItemType MoveFirst() {
      current = first;
      if (first != nullptr)
        return first->get_Item();
      else
         return ItemType();
   }

   virtual bool Add(ItemType item) {
      if (last != nullptr) {
         last->next = gcnew Node(item);
         last = last->next;
      }
      else {
         first = gcnew Node(item);
         last = first;
         current = first;
      }
      return true;
   }

   virtual bool AtEnd() {
      if (current == nullptr )
        return true;
      else
        return false;
   }

   virtual ItemType Current() {
       if (current != nullptr)
         return current->get_Item();
       else
         throw gcnew ElementNotFoundException();
   }

   virtual void MoveNext() {
      if (current != nullptr)
       current = current->next;
      else
        throw gcnew ElementNotFoundException();
   }
};

// An array implementation of IList
generic <typename ItemType>
ref class List2 : public IList<ItemType> {
   array<ItemType>^ item_array;
   int count;
   int current;

   public:

   List2() {
      // not yet possible to declare an
      // array of a generic type parameter
      item_array = gcnew array<ItemType>(256);
      count = current = 0;
   }

   virtual ItemType MoveFirst() {
      current = 0;
      return item_array[0];
   }

   virtual bool Add(ItemType item) {
      if (count < 256)
         item_array[count++] = item;
      else
        return false;
      return true;
   }

   virtual bool AtEnd() {
      if (current >= count)
        return true;
      else
        return false;
   }

   virtual ItemType Current() {
      if (current < count)
        return item_array[current];
      else
        throw gcnew ElementNotFoundException();
   }

   virtual void MoveNext() {
      if (current < count)
         ++current;
      else
         throw gcnew ElementNotFoundException();
   }
};

// Add elements to the list and display them.
generic <typename ItemType>
void AddStringsAndDisplay(IList<ItemType>^ list, ItemType item1, ItemType item2) {
   list->Add(item1);
   list->Add(item2);
   for (list->MoveFirst(); ! list->AtEnd(); list->MoveNext())
   Console::WriteLine(list->Current());
}

int main() {
   // Instantiate both types of list.

   List1<String^>^ list1 = gcnew List1<String^>();
   List2<String^>^ list2 = gcnew List2<String^>();

   // Use the linked list implementation of IList.
   AddStringsAndDisplay<String^>(list1, "Linked List", "List1");

   // Use the array implementation of the IList.
   AddStringsAndDisplay<String^>(list2, "Array List", "List2");
}
```

```Output
Linked List
List1
Array List
List2
```

## <a name="example-declare-a-generic-interface"></a>예: 제네릭 인터페이스 선언

이 예제에서는 제네릭 인터페이스 `IMyGenIface`와 `IMyGenIface`를 특수화하는, 제네릭이 아닌 두 인터페이스 `IMySpecializedInt` 및 `ImySpecializedString`을 선언합니다. 그런 다음, 두 클래스 `MyIntClass` 및 `MyStringClass`에서 특수화된 두 인터페이스를 구현합니다. 예제에서는 제네릭 인터페이스를 특수화하고, 제네릭 인터페이스와 제네릭이 아닌 인터페이스를 인스턴스화하고, 인터페이스에서 명시적으로 구현된 멤버를 호출하는 방법을 보여 줍니다.

```cpp
// generic_interface2.cpp
// compile with: /clr
// Specializing and implementing generic interfaces.
using namespace System;

generic <class ItemType>
public interface class IMyGenIface {
   void Initialize(ItemType f);
};

public interface class IMySpecializedInt: public IMyGenIface<int> {
   void Display();
};

public interface class IMySpecializedString: public IMyGenIface<String^> {
   void Display();
};

public ref class MyIntClass: public IMySpecializedInt {
   int myField;

public:
   virtual void Initialize(int f) {
      myField = f;
   }

   virtual void Display() {
      Console::WriteLine("The integer field contains: {0}", myField);
   }
};

public ref struct MyStringClass: IMySpecializedString {
   String^ myField;

public:
   virtual void Initialize(String^ f) {
      myField = f;
    }

   virtual void Display() {
      Console::WriteLine("The String field contains: {0}", myField);
   }
};

int main() {
   // Instantiate the generic interface.
   IMyGenIface<int>^ myIntObj = gcnew MyIntClass();

   // Instantiate the specialized interface "IMySpecializedInt."
   IMySpecializedInt^ mySpIntObj = (IMySpecializedInt^) myIntObj;

   // Instantiate the generic interface.
   IMyGenIface<String^>^ myStringObj = gcnew MyStringClass();

   // Instantiate the specialized interface "IMySpecializedString."
   IMySpecializedString^ mySpStringObj =
            (IMySpecializedString^) myStringObj;

   // Call the explicitly implemented interface members.
   myIntObj->Initialize(1234);
   mySpIntObj->Display();

   myStringObj->Initialize("My string");
   mySpStringObj->Display();
}
```

```Output
The integer field contains: 1234
The String field contains: My string
```

## <a name="see-also"></a>참고 항목

[제네릭](generics-cpp-component-extensions.md)
