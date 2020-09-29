---
title: '방법: C++/CLI에서 속성 사용'
ms.date: 07/21/2017
helpviewer_keywords:
- simple properties
- properties [C++], simple
ms.assetid: f5d82547-e214-4f05-9e1b-ddb6d0dc5e4c
ms.openlocfilehash: c786c7746cd40a970af3a5ae4436119def4c805b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499678"
---
# <a name="how-to-use-properties-in-ccli"></a>방법: C++/CLI에서 속성 사용

이 문서에서는 c + +/CLI에서 속성을 사용 하는 방법을 보여 줍니다.

## <a name="basic-properties"></a>기본 속성

단순히 전용 데이터 멤버를 할당 하 고 검색 하는 기본 속성의 경우 get 및 set 접근자 함수를 명시적으로 정의 하지 않아도 됩니다. 속성의 데이터 형식을 지정 하는 경우 컴파일러에서 자동으로이 함수를 제공 하기 때문입니다. 이 코드는 기본 속성을 보여 줍니다.

```cpp
// SimpleProperties.cpp
// compile with: /clr
using namespace System;

ref class C {
public:
   property int Size;
};

int main() {
   C^ c = gcnew C;
   c->Size = 111;
   Console::WriteLine("c->Size = {0}", c->Size);
}
```

```Output
c->Size = 111
```

## <a name="static-properties"></a>정적 속성

이 코드 샘플은 정적 속성을 선언 하 고 사용 하는 방법을 보여 줍니다.  정적 속성은 클래스의 정적 멤버에만 액세스할 수 있습니다.

```cpp
// mcppv2_property_3.cpp
// compile with: /clr
using namespace System;

ref class StaticProperties {
   static int MyInt;
   static int MyInt2;

public:
   static property int Static_Data_Member_Property;

   static property int Static_Block_Property {
      int get() {
         return MyInt;
      }

      void set(int value) {
         MyInt = value;
      }
   }
};

int main() {
   StaticProperties::Static_Data_Member_Property = 96;
   Console::WriteLine(StaticProperties::Static_Data_Member_Property);

   StaticProperties::Static_Block_Property = 47;
   Console::WriteLine(StaticProperties::Static_Block_Property);
}
```

```Output
96
47
```

## <a name="indexed-properties"></a>인덱싱된 속성

인덱싱된 속성은 일반적으로 첨자 연산자를 사용 하 여 액세스 되는 데이터 구조를 노출 합니다.

인덱싱된 기본 속성을 사용 하는 경우 클래스 이름을 참조 하 여 데이터 구조에 액세스할 수 있지만 사용자 정의 인덱싱된 속성을 사용 하는 경우 속성 이름을 지정 하 여 데이터 구조에 액세스 해야 합니다.

C #으로 작성 된 인덱서를 사용 하는 방법에 대 한 자세한 내용은 [방법: c # 인덱서 사용 (c + +/cli)](./interoperability-with-other-dotnet-languages-cpp-cli.md#consume_indexer)을 참조 하세요.

이 코드 예제에서는 기본 및 사용자 정의 인덱싱된 속성을 사용 하는 방법을 보여 줍니다.

```cpp
// mcppv2_property_2.cpp
// compile with: /clr
using namespace System;
public ref class C {
   array<int>^ MyArr;

public:
   C() {
      MyArr = gcnew array<int>(5);
   }

   // default indexer
   property int default[int] {
      int get(int index) {
         return MyArr[index];
      }
      void set(int index, int value) {
         MyArr[index] = value;
      }
   }

   // user-defined indexer
   property int indexer1[int] {
      int get(int index) {
         return MyArr[index];
      }
      void set(int index, int value) {
         MyArr[index] = value;
      }
   }
};

int main() {
   C ^ MyC = gcnew C();

   // use the default indexer
   Console::Write("[ ");
   for (int i = 0 ; i < 5 ; i++) {
      MyC[i] = i;
      Console::Write("{0} ", MyC[i]);
   }

   Console::WriteLine("]");

   // use the user-defined indexer
   Console::Write("[ ");
   for (int i = 0 ; i < 5 ; i++) {
      MyC->indexer1[i] = i * 2;
      Console::Write("{0} ", MyC->indexer1[i]);
   }

   Console::WriteLine("]");
}
```

```Output
[ 0 1 2 3 4 ]
[ 0 2 4 6 8 ]
```

다음 샘플에서는 포인터를 사용 하 여 기본 인덱서를 호출 하는 방법을 보여 줍니다 **`this`** .

```cpp
// call_default_indexer_through_this_pointer.cpp
// compile with: /clr /c
value class Position {
public:
   Position(int x, int y) : position(gcnew array<int, 2>(100, 100)) {
      this->default[x, y] = 1;
   }

   property int default[int, int] {
      int get(int x, int y) {
         return position[x, y];
      }

      void set(int x, int y, int value) {}
   }

private:
   array<int, 2> ^ position;
};
```

이 샘플에서는를 사용 하 여 기본 인덱서를 지정 하는 방법을 보여 줍니다 <xref:System.Reflection.DefaultMemberAttribute> .

```cpp
// specify_default_indexer.cpp
// compile with: /LD /clr
using namespace System;
[Reflection::DefaultMember("XXX")]
public ref struct Squares {
   property Double XXX[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
};
```

다음 샘플에서는 이전 예제에서 만든 메타 데이터를 사용 합니다.

```cpp
// consume_default_indexer.cpp
// compile with: /clr
#using "specify_default_indexer.dll"
int main() {
   Squares ^ square = gcnew Squares();
   System::Console::WriteLine("{0}", square[3]);
}
```

```Output
9
```

## <a name="virtual-properties"></a>가상 속성

이 코드 샘플에서는 가상 속성을 선언 하 고 사용 하는 방법을 보여 줍니다.

```cpp
// mcppv2_property_4.cpp
// compile with: /clr
using namespace System;
interface struct IEFace {
public:
   property int VirtualProperty1;
   property int VirtualProperty2 {
      int get();
      void set(int i);
   }
};

// implement virtual events
ref class PropImpl : public IEFace {
   int MyInt;
public:
   virtual property int VirtualProperty1;

   virtual property int VirtualProperty2 {
      int get() {
         return MyInt;
      }
      void set(int i) {
         MyInt = i;
      }
   }
};

int main() {
   PropImpl ^ MyPI = gcnew PropImpl();
   MyPI->VirtualProperty1 = 93;
   Console::WriteLine(MyPI->VirtualProperty1);

   MyPI->VirtualProperty2 = 43;
   Console::WriteLine(MyPI->VirtualProperty2);
}
```

```Output
93
43
```

## <a name="abstract-and-sealed-properties"></a>추상 및 봉인 된 속성

Microsoft c + + 컴파일러의 경우에는 [abstract](../extensions/abstract-cpp-component-extensions.md) 및 [SEALED](../extensions/sealed-cpp-component-extensions.md) 키워드를 ECMA c + +/cli 사양에 유효한 것으로 지정 하더라도 trivial 속성에는 지정할 수 없으며 trivial 속성의 속성 선언에는 지정할 수 없습니다.

Sealed 또는 abstract 속성을 선언 하려면 trivial 속성을 정의한 다음 **`abstract`** **`sealed`** get 및 set 접근자 함수에서 또는 키워드를 지정 해야 합니다.

```cpp
// properties_abstract_sealed.cpp
// compile with: /clr
ref struct A {
protected:
   int m_i;

public:
   A() { m_i = 87; }

   // define abstract property
   property int Prop_1 {
      virtual int get() abstract;
      virtual void set(int i) abstract;
   }
};

ref struct B : A {
private:
   int m_i;

public:
   B() { m_i = 86; }

   // implement abstract property
   property int Prop_1 {
      virtual int get() override { return m_i; }
      virtual void set(int i) override { m_i = i; }
   }
};

ref struct C {
private:
   int m_i;

public:
   C() { m_i = 87; }

   // define sealed property
   property int Prop_2 {
      virtual int get() sealed { return m_i; }
      virtual void set(int i) sealed { m_i = i; };
   }
};

int main() {
   B b1;
   // call implementation of abstract property
   System::Console::WriteLine(b1.Prop_1);

   C c1;
   // call sealed property
   System::Console::WriteLine(c1.Prop_2);
}
```

```Output
86
87
```

## <a name="multidimensional-properties"></a>다차원 속성

다차원 속성을 사용 하 여 비표준 개수의 매개 변수를 사용 하는 속성 접근자 메서드를 정의할 수 있습니다.

```cpp
// mcppv2_property_5.cpp
// compile with: /clr
ref class X {
   double d;
public:
   X() : d(0) {}
   property double MultiDimProp[int, int, int] {
      double get(int, int, int) {
         return d;
      }
      void set(int i, int j, int k, double l) {
         // do something with those ints
         d = l;
      }
   }

   property double MultiDimProp2[int] {
      double get(int) {
         return d;
      }
      void set(int i, double l) {
         // do something with those ints
         d = l;
      }
   }

};

int main() {
   X ^ MyX = gcnew X();
   MyX->MultiDimProp[0,0,0] = 1.1;
   System::Console::WriteLine(MyX->MultiDimProp[0, 0, 0]);
}
```

```Output
1.1
```

## <a name="overloading-property-accessors"></a>속성 접근자 오버 로드

다음 예제에서는 인덱싱된 속성을 오버 로드 하는 방법을 보여 줍니다.

```cpp
// mcppv2_property_6.cpp
// compile with: /clr
ref class X {
   double d;
public:
   X() : d(0.0) {}
   property double MyProp[int] {
      double get(int i) {
         return d;
      }

      double get(System::String ^ i) {
         return 2*d;
      }

      void set(int i, double l) {
         d = i * l;
      }
   }   // end MyProp definition
};

int main() {
   X ^ MyX = gcnew X();
   MyX->MyProp[2] = 1.7;
   System::Console::WriteLine(MyX->MyProp[1]);
   System::Console::WriteLine(MyX->MyProp["test"]);
}
```

```Output
3.4
6.8
```

## <a name="see-also"></a>참고 항목

[property](../extensions/property-cpp-component-extensions.md)
