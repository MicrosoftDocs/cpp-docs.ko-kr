---
description: '자세한 정보: 방법: c + +/CLI에서 safe_cast 사용'
title: '방법: C++/CLI에서 safe_cast 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- safe_cast keyword [C++], upcasting
ms.assetid: 0fbc87d8-ecdf-4cd5-81f4-0d8cc18e2aff
ms.openlocfilehash: f921371f97f967f9517121aaa163f79769781211
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145576"
---
# <a name="how-to-use-safe_cast-in-ccli"></a>방법: C++/CLI에서 safe_cast 사용

이 문서에서는 c + +/CLI 응용 프로그램에서 safe_cast를 사용 하는 방법을 보여 줍니다. C + +/CX의 safe_cast에 대 한 자세한 내용은 [safe_cast](../extensions/safe-cast-cpp-component-extensions.md)을 참조 하세요.

## <a name="upcasting"></a>업캐스팅

업 캐스트는 파생 된 형식에서 기본 클래스 중 하나로 캐스팅 됩니다. 이 캐스팅은 안전 하며 명시적인 캐스트 표기법이 필요 하지 않습니다. 다음 샘플에서는 업 캐스트를 사용 하거나 사용 하지 않고 수행 하는 방법을 보여 줍니다 `safe_cast` .

```cpp
// safe_upcast.cpp
// compile with: /clr
using namespace System;
interface class A {
   void Test();
};

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test");
   }

   void Test2() {
      Console::WriteLine("in B::Test2");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test");
   };
};

int main() {
   C ^ c = gcnew C;

   // implicit upcast
   B ^ b = c;
   b->Test();
   b->Test2();

   // upcast with safe_cast
   b = nullptr;
   b = safe_cast<B^>(c);
   b->Test();
   b->Test2();
}
```

```Output
in C::Test
in B::Test2
in C::Test
in B::Test2
```

## <a name="downcasting"></a>좋기는

다운 캐스트는 기본 클래스에서 기본 클래스에서 파생 된 클래스로의 캐스트입니다.  다운 캐스트는 런타임에 처리 된 개체가 실제로 파생 클래스 개체의 주소를 지정 하는 경우에만 안전 합니다.  와 달리는 **`static_cast`** `safe_cast` 동적 검사를 수행 하 고 <xref:System.InvalidCastException> 변환이 실패 하는 경우을 throw 합니다.

```cpp
// safe_downcast.cpp
// compile with: /clr
using namespace System;

interface class A { void Test(); };

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test()");
   }

   void Test2() {
      Console::WriteLine("in B::Test2()");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test()");
   }
};

interface class I {};

value struct V : public I {};

int main() {
   A^ a = gcnew C();
   a->Test();
   B^ b = safe_cast<B^>(a);
   b->Test();
   b->Test2();

   V v;
   I^ i = v;   // i boxes V
   V^ refv = safe_cast<V^>(i);

   Object^ o = gcnew B;
   A^ a2= safe_cast<A^>(o);
}
```

```Output
in C::Test()
in C::Test()
in B::Test2()
```

## <a name="safe_cast-with-user-defined-conversions"></a>사용자 정의 변환으로 safe_cast

다음 샘플에서는를 사용 하 여 `safe_cast` 사용자 정의 변환을 호출할 수 있는 방법을 보여 줍니다.

```cpp
// safe_cast_udc.cpp
// compile with: /clr
using namespace System;
value struct V;

ref struct R {
   int x;
   R() {
      x = 1;
   }

   R(int argx) {
      x = argx;
   }

   static operator R::V^(R^ r);
};

value struct V {
   int x;
   static operator R^(V& v) {
      Console::WriteLine("in operator R^(V& v)");
      R^ r = gcnew R();
      r->x = v.x;
      return r;
   }

   V(int argx) {
      x = argx;
   }
};

   R::operator V^(R^ r) {
      Console::WriteLine("in operator V^(R^ r)");
      return gcnew V(r->x);
   }

int main() {
   bool fReturnVal = false;
   V v(2);
   R^ r = safe_cast<R^>(v);   // should invoke UDC
   V^ v2 = safe_cast<V^>(r);   // should invoke UDC
}
```

```Output
in operator R^(V& v
in operator V^(R^ r)
```

## <a name="safe_cast-and-boxing-operations"></a>safe_cast 및 boxing 작업

### <a name="boxing"></a>boxing

Boxing은 컴파일러가 삽입 한 사용자 정의 변환으로 정의 됩니다.  따라서를 사용 하 여 `safe_cast` CLR 힙의 값을 box 할 수 있습니다.

다음 샘플에서는 단순 및 사용자 정의 값 형식을 사용 하 여 boxing을 보여 줍니다.  `safe_cast`가비지 수집 힙의 변수에 할당 될 수 있도록 네이티브 스택에 있는 값 형식 변수를 boxing 합니다.

```cpp
// safe_cast_boxing.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct V : public I {
   int m_x;

   V(int i) : m_x(i) {}
};

int main() {
   // box a value type
   V v(100);
   I^ i = safe_cast<I^>(v);

   int x = 100;
   V^ refv = safe_cast<V^>(v);
   int^ refi = safe_cast<int^>(x);
}
```

다음 샘플에서는 작업의 사용자 정의 변환 보다 boxing이 우선 함을 보여 줍니다 `safe_cast` .

```cpp
// safe_cast_boxing_2.cpp
// compile with: /clr
static bool fRetval = true;

interface struct I {};
value struct V : public I {
   int x;

   V(int argx) {
      x = argx;
   }

   static operator I^(V v) {
      fRetval = false;
      I^ pi = v;
      return pi;
   }
};

ref struct R {
   R() {}
   R(V^ pv) {}
};

int main() {
   V v(10);
   I^ pv = safe_cast<I^>(v);   // boxing will occur, not UDC "operator I^"
}
```

### <a name="unboxing"></a>unboxing

Unboxing은 컴파일러에 삽입 된 사용자 정의 변환으로 정의 됩니다.  따라서를 사용 하 여 `safe_cast` CLR 힙의 값을 unbox 수 있습니다.

Unboxing은 사용자 정의 변환 이지만 boxing과 달리 unboxing은 명시적 이어야 합니다. 즉, C 스타일 캐스트 또는에서 수행 해야 합니다. **`static_cast`** `safe_cast` unboxing은 암시적으로 수행할 수 없습니다.

```cpp
// safe_cast_unboxing.cpp
// compile with: /clr
int main() {
   System::Object ^ o = 42;
   int x = safe_cast<int>(o);
}
```

다음 샘플에서는 값 형식 및 기본 형식에 대 한 unboxing을 보여 줍니다.

```cpp
// safe_cast_unboxing_2.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct VI : public I {};

void test1() {
   Object^ o = 5;
   int x = safe_cast<Int32>(o);
}

value struct V {
   int x;
   String^ s;
};

void test2() {
   V localv;
   Object^ o = localv;
   V unboxv = safe_cast<V>(o);
}

void test3() {
   V localv;
   V^ o2 = localv;
   V unboxv2 = safe_cast<V>(o2);
}

void test4() {
   I^ refi = VI();
   VI vi  = safe_cast<VI>(refi);
}

int main() {
   test1();
   test2();
   test3();
   test4();
}
```

## <a name="safe_cast-and-generic-types"></a>safe_cast 및 제네릭 형식

다음 샘플에서는를 사용 하 여 `safe_cast` 제네릭 형식으로 다운 캐스트를 수행 하는 방법을 보여 줍니다.

```cpp
// safe_cast_generic_types.cpp
// compile with: /clr
interface struct I {};

generic<class T> where T:I
ref struct Base {
   T t;
   void test1() {}
};

generic<class T> where T:I
ref struct Derived:public Base <T> {};

ref struct R:public I {};

typedef Base<R^> GBase_R;
typedef Derived<R^> GDerived_R;

int main() {
   GBase_R^ br = gcnew GDerived_R();
   GDerived_R^ dr = safe_cast<GDerived_R^>(br);
}
```

## <a name="see-also"></a>참고 항목

[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)
