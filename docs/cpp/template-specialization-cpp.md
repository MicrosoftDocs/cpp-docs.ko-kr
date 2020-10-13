---
title: 템플릿 특수화(C++)
ms.date: 11/04/2016
helpviewer_keywords:
- partial specialization of class templates
ms.assetid: f3c67c0b-3875-434a-b8d8-bb47e99cf4f0
ms.openlocfilehash: 7f71c2c3862bd015ba3edcd17aeac85472eb2562
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008911"
---
# <a name="template-specialization-c"></a>템플릿 특수화(C++)

클래스 템플릿은 부분적으로 특수화될 수 있으며 결과 클래스는 여전히 템플릿입니다. 부분 특수화를 사용하면 다음과 같은 상황에서 특정 형식에 대해 템플릿 코드를 부분적으로 사용자 지정할 수 있습니다.

- 템플릿에 여러 형식이 있으며 그 중 일부만 특수화되어야 하는 경우. 결과는 나머지 형식에 대해 매개 변수화된 템플릿입니다.

- 템플릿에 형식이 하나만 있지만 포인터, 참조, 멤버에 대한 포인터 또는 함수 포인터 형식에 대한 특수화가 필요한 경우. 특수화 자체는 여전히 가리켜지거나 참조된 형식에 대한 템플릿입니다.

## <a name="example-partial-specialization-of-class-templates"></a>예제: 클래스 템플릿의 부분 특수화

```cpp
// partial_specialization_of_class_templates.cpp
template <class T> struct PTS {
   enum {
      IsPointer = 0,
      IsPointerToDataMember = 0
   };
};

template <class T> struct PTS<T*> {
   enum {
      IsPointer = 1,
      IsPointerToDataMember = 0
   };
};

template <class T, class U> struct PTS<T U::*> {
   enum {
      IsPointer = 0,
      IsPointerToDataMember = 1
   };
};

struct S{};

extern "C" int printf_s(const char*,...);

int main() {
   printf_s("PTS<S>::IsPointer == %d PTS<S>::IsPointerToDataMember == %d\n",
           PTS<S>::IsPointer, PTS<S>:: IsPointerToDataMember);
   printf_s("PTS<S*>::IsPointer == %d PTS<S*>::IsPointerToDataMember ==%d\n"
           , PTS<S*>::IsPointer, PTS<S*>:: IsPointerToDataMember);
   printf_s("PTS<int S::*>::IsPointer == %d PTS"
           "<int S::*>::IsPointerToDataMember == %d\n",
           PTS<int S::*>::IsPointer, PTS<int S::*>::
           IsPointerToDataMember);
}
```

```Output
PTS<S>::IsPointer == 0 PTS<S>::IsPointerToDataMember == 0
PTS<S*>::IsPointer == 1 PTS<S*>::IsPointerToDataMember ==0
PTS<int S::*>::IsPointer == 0 PTS<int S::*>::IsPointerToDataMember == 1
```

## <a name="example-partial-specialization-for-pointer-types"></a>예제: 포인터 형식에 대 한 부분 특수화

형식을 사용 하는 템플릿 컬렉션 클래스가 있는 경우 `T` 포인터 형식을 사용 하는 부분 특수화를 만들 수 있습니다 `T*` . 다음 코드에서는 컬렉션 클래스 템플릿 `Bag`와 컬렉션이 포인터 형식을 배열에 복사하기 전에 역참조하는 포인터 형식에 대한 부분 특수화를 보여 줍니다. 그런 다음 컬렉션은 가리켜진 값을 저장합니다. 원래 템플릿을 사용했다면 포인터 자체만 컬렉션에 저장되고 데이터는 삭제나 수정에 취약한 상태가 되었을 것입니다. 이 컬렉션의 특수 포인터 버전에서는 `add` 메서드에서 null 포인터를 검사하는 코드가 추가되었습니다.

```cpp
// partial_specialization_of_class_templates2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

// Original template collection class.
template <class T> class Bag {
   T* elem;
   int size;
   int max_size;

public:
   Bag() : elem(0), size(0), max_size(1) {}
   void add(T t) {
      T* tmp;
      if (size + 1 >= max_size) {
         max_size *= 2;
         tmp = new T [max_size];
         for (int i = 0; i < size; i++)
            tmp[i] = elem[i];
         tmp[size++] = t;
         delete[] elem;
         elem = tmp;
      }
      else
         elem[size++] = t;
   }

   void print() {
      for (int i = 0; i < size; i++)
         cout << elem[i] << " ";
      cout << endl;
   }
};

// Template partial specialization for pointer types.
// The collection has been modified to check for NULL
// and store types pointed to.
template <class T> class Bag<T*> {
   T* elem;
   int size;
   int max_size;

public:
   Bag() : elem(0), size(0), max_size(1) {}
   void add(T* t) {
      T* tmp;
      if (t == NULL) {   // Check for NULL
         cout << "Null pointer!" << endl;
         return;
      }

      if (size + 1 >= max_size) {
         max_size *= 2;
         tmp = new T [max_size];
         for (int i = 0; i < size; i++)
            tmp[i] = elem[i];
         tmp[size++] = *t;  // Dereference
         delete[] elem;
         elem = tmp;
      }
      else
         elem[size++] = *t; // Dereference
   }

   void print() {
      for (int i = 0; i < size; i++)
         cout << elem[i] << " ";
      cout << endl;
   }
};

int main() {
   Bag<int> xi;
   Bag<char> xc;
   Bag<int*> xp; // Uses partial specialization for pointer types.

   xi.add(10);
   xi.add(9);
   xi.add(8);
   xi.print();

   xc.add('a');
   xc.add('b');
   xc.add('c');
   xc.print();

   int i = 3, j = 87, *p = new int[2];
   *p = 8;
   *(p + 1) = 100;
   xp.add(&i);
   xp.add(&j);
   xp.add(p);
   xp.add(p + 1);
   p = NULL;
   xp.add(p);
   xp.print();
}
```

```Output
10 9 8
a b c
Null pointer!
3 87 8 100
```

## <a name="example-define-partial-specialization-so-one-type-is-int"></a>예: 부분 특수화를 정의 하 여 한 형식이 `int`

다음 예제에서는 두 형식의 쌍을 사용 하는 템플릿 클래스를 정의한 다음 형식 중 하나를 사용 하도록 특수화 된 해당 템플릿 클래스의 부분 특수화를 정의 합니다 **`int`** . 특수화에서는 정수 기반의 간단한 거품 정렬을 구현하는 추가 정렬 메서드를 정의합니다.

```cpp
// partial_specialization_of_class_templates3.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class Key, class Value> class Dictionary {
   Key* keys;
   Value* values;
   int size;
   int max_size;
public:
   Dictionary(int initial_size) :  size(0) {
      max_size = 1;
      while (initial_size >= max_size)
         max_size *= 2;
      keys = new Key[max_size];
      values = new Value[max_size];
   }
   void add(Key key, Value value) {
      Key* tmpKey;
      Value* tmpVal;
      if (size + 1 >= max_size) {
         max_size *= 2;
         tmpKey = new Key [max_size];
         tmpVal = new Value [max_size];
         for (int i = 0; i < size; i++) {
            tmpKey[i] = keys[i];
            tmpVal[i] = values[i];
         }
         tmpKey[size] = key;
         tmpVal[size] = value;
         delete[] keys;
         delete[] values;
         keys = tmpKey;
         values = tmpVal;
      }
      else {
         keys[size] = key;
         values[size] = value;
      }
      size++;
   }

   void print() {
      for (int i = 0; i < size; i++)
         cout << "{" << keys[i] << ", " << values[i] << "}" << endl;
   }
};

// Template partial specialization: Key is specified to be int.
template <class Value> class Dictionary<int, Value> {
   int* keys;
   Value* values;
   int size;
   int max_size;
public:
   Dictionary(int initial_size) :  size(0) {
      max_size = 1;
      while (initial_size >= max_size)
         max_size *= 2;
      keys = new int[max_size];
      values = new Value[max_size];
   }
   void add(int key, Value value) {
      int* tmpKey;
      Value* tmpVal;
      if (size + 1 >= max_size) {
         max_size *= 2;
         tmpKey = new int [max_size];
         tmpVal = new Value [max_size];
         for (int i = 0; i < size; i++) {
            tmpKey[i] = keys[i];
            tmpVal[i] = values[i];
         }
         tmpKey[size] = key;
         tmpVal[size] = value;
         delete[] keys;
         delete[] values;
         keys = tmpKey;
         values = tmpVal;
      }
      else {
         keys[size] = key;
         values[size] = value;
      }
      size++;
   }

   void sort() {
      // Sort method is defined.
      int smallest = 0;
      for (int i = 0; i < size - 1; i++) {
         for (int j = i; j < size; j++) {
            if (keys[j] < keys[smallest])
               smallest = j;
         }
         swap(keys[i], keys[smallest]);
         swap(values[i], values[smallest]);
      }
   }

   void print() {
      for (int i = 0; i < size; i++)
         cout << "{" << keys[i] << ", " << values[i] << "}" << endl;
   }
};

int main() {
   Dictionary<char*, char*>* dict = new Dictionary<char*, char*>(10);
   dict->print();
   dict->add("apple", "fruit");
   dict->add("banana", "fruit");
   dict->add("dog", "animal");
   dict->print();

   Dictionary<int, char*>* dict_specialized = new Dictionary<int, char*>(10);
   dict_specialized->print();
   dict_specialized->add(100, "apple");
   dict_specialized->add(101, "banana");
   dict_specialized->add(103, "dog");
   dict_specialized->add(89, "cat");
   dict_specialized->print();
   dict_specialized->sort();
   cout << endl << "Sorted list:" << endl;
   dict_specialized->print();
}
```

```Output
{apple, fruit}
{banana, fruit}
{dog, animal}
{100, apple}
{101, banana}
{103, dog}
{89, cat}

Sorted list:
{89, cat}
{100, apple}
{101, banana}
{103, dog}
```
