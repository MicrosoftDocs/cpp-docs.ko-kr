---
description: Auto_gcroot 클래스에 대해 자세히 알아보세요.
title: auto_gcroot 클래스
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot::auto_gcroot
- msclr::auto_gcroot::attach
- msclr::auto_gcroot::get
- msclr::auto_gcroot::release
- msclr::auto_gcroot::reset
- msclr::auto_gcroot::swap
- msclr::auto_gcroot::operator=
- msclr::auto_gcroot::operator->
- msclr::auto_gcroot::operator!
- msclr::auto_gcroot::operator auto_gcroot
helpviewer_keywords:
- msclr::auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
ms.openlocfilehash: 9c763883a10906a8f63b7ba265576ab547750b66
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282798"
---
# <a name="auto_gcroot-class"></a>auto_gcroot 클래스

네이티브 형식에 가상 핸들을 포함 하는 데 사용할 수 있는 자동 리소스 관리 (예: [Auto_ptr 클래스](../standard-library/auto-ptr-class.md))입니다.

## <a name="syntax"></a>구문

```cpp
template<typename _element_type>
class auto_gcroot;
```

### <a name="parameters"></a>매개 변수

*_element_type*<br/>
포함할 관리 되는 형식입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|Name|설명|
|---------|-----------|
|[auto_gcroot:: auto_gcroot](#auto-gcroot)|`auto_gcroot`생성자입니다.|
|[auto_gcroot::~auto_gcroot](#tilde-auto-gcroot)|`auto_gcroot`소멸자입니다.
|

### <a name="public-methods"></a>public 메서드

|Name|설명|
|---------|-----------|
|[auto_gcroot::attach](#attach)|`auto_gcroot`개체에 연결 합니다.|
|[auto_gcroot::get](#get)|포함 된 개체를 가져옵니다.|
|[auto_gcroot::release](#release)|관리에서 개체를 해제 `auto_gcroot` 합니다.|
|[auto_gcroot::reset](#reset)|현재 소유 하 고 있는 개체를 삭제 하 고 필요에 따라 새 개체를 소유 합니다.|
|[auto_gcroot::swap](#swap)|다른 개체와 개체를 교환 `auto_gcroot` 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|---------|-----------|
|[auto_gcroot:: operator-&gt;](#operator-arrow)|멤버 액세스 연산자입니다.|  
|[auto_gcroot:: operator =](#operator-assign)|대입 연산자입니다.|
|[auto_gcroot:: operator &nbsp; auto_gcroot](#operator-auto-gcroot)|와 호환 되는 형식 사이의 형식 캐스팅 연산자 `auto_gcroot` 입니다.|
|[auto_gcroot:: operator &nbsp; bool](#operator-bool)|조건식에 사용 하기 위한 연산자 `auto_gcroot` 입니다.|  
|[auto_gcroot::operator!](#operator-logical-not)|조건식에 사용 하기 위한 연산자 `auto_gcroot` 입니다.|

## <a name="requirements"></a>요구 사항

**헤더 파일** \<msclr\auto_gcroot.h>

Msclr **네임 스페이스**

## <a name="auto_gcrootauto_gcroot"></a><a name="auto-gcroot"></a> auto_gcroot:: auto_gcroot

`auto_gcroot`생성자입니다.

```cpp
auto_gcroot(
   _element_type _ptr = nullptr
);
auto_gcroot(
   auto_gcroot<_element_type> & _right
);
template<typename _other_type>
auto_gcroot(
   auto_gcroot<_other_type> & _right
);
```

### <a name="parameters"></a>매개 변수

*_ptr*<br/>
소유할 개체입니다.

*_right*<br/>
기존 `auto_gcroot`입니다.

### <a name="remarks"></a>설명

기존에서을 생성할 때 `auto_gcroot` `auto_gcroot` 기존은 `auto_gcroot` 개체의 소유권을 새로 전송 하기 전에 해당 개체를 해제 합니다 `auto_gcroot` .

### <a name="example"></a>예제

```cpp
// msl_auto_gcroot_auto_gcroot.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class RefClassA {
protected:
   String^ m_s;
public:
   RefClassA(String^ s) : m_s(s) {
      Console::WriteLine( "in RefClassA constructor: " + m_s );
   }
   ~RefClassA() {
      Console::WriteLine( "in RefClassA destructor: " + m_s );
   }

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class RefClassB : RefClassA {
public:
   RefClassB( String^ s ) : RefClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

class ClassA { //unmanaged class
private:
   auto_gcroot<RefClassA^> m_a;

public:
   ClassA() : m_a( gcnew RefClassA( "unmanaged" ) ) {}
   ~ClassA() {} //no need to delete m_a

   void DoSomething() {
      m_a->PrintHello();
   }
};

int main()
{
   {
      ClassA a;
      a.DoSomething();
   } // a.m_a is automatically destroyed as a goes out of scope

   {
      auto_gcroot<RefClassA^> a(gcnew RefClassA( "first" ) );
      a->PrintHello();
   }

   {
      auto_gcroot<RefClassB^> b(gcnew RefClassB( "second" ) );
      b->PrintHello();
      auto_gcroot<RefClassA^> a(b); //construct from derived type
      a->PrintHello();
      auto_gcroot<RefClassA^> a2(a); //construct from same type
      a2->PrintHello();
   }

   Console::WriteLine("done");
}
```

```Output
in RefClassA constructor: unmanaged
Hello from unmanaged A!
in RefClassA destructor: unmanaged
in RefClassA constructor: first
Hello from first A!
in RefClassA destructor: first
in RefClassA constructor: second
Hello from second B!
Hello from second A!
Hello from second A!
in RefClassA destructor: second
done
```

## <a name="auto_gcrootauto_gcroot"></a><a name="tilde-auto-gcroot"></a> auto_gcroot:: ~ auto_gcroot

`auto_gcroot`소멸자입니다.

```cpp
~auto_gcroot();
```

### <a name="remarks"></a>설명

소멸자는 소유 된 개체도 destructs 합니다.

### <a name="example"></a>예제

```cpp
// msl_auto_gcroot_dtor.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
public:
   ClassA() { Console::WriteLine( "ClassA constructor" ); }
   ~ClassA() { Console::WriteLine( "ClassA destructor" ); }
};

int main()
{
   // create a new scope for a:
   {
      auto_gcroot<ClassA^> a = gcnew ClassA;
   }
   // a goes out of scope here, invoking its destructor
   // which in turns destructs the ClassA object.

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor
ClassA destructor
done
```

## <a name="auto_gcrootattach"></a><a name="attach"></a> auto_gcroot:: attach

`auto_gcroot`개체에 연결 합니다.

```cpp
auto_gcroot<_element_type> & attach(
   _element_type _right
);
auto_gcroot<_element_type> & attach(
   auto_gcroot<_element_type> & _right
);
template<typename _other_type>
auto_gcroot<_element_type> & attach(
   auto_gcroot<_other_type> & _right
);
```

### <a name="parameters"></a>매개 변수

*_right*<br/>
연결할 개체 이거나 `auto_gcroot` 연결할 개체를 포함 하는입니다.

### <a name="return-value"></a>반환 값

현재 `auto_gcroot`입니다.

### <a name="remarks"></a>설명

`_right`가 이면 `auto_gcroot` 개체가 현재에 연결 되기 전에 해당 개체의 소유권을 해제 `auto_gcroot` 합니다.

### <a name="example"></a>예제

```cpp
// msl_auto_gcroot_attach.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {
      Console::WriteLine( "in ClassA constructor:" + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "in ClassA destructor:" + m_s );
   }

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class ClassB : ClassA {
public:
   ClassB( String ^ s) : ClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main() {
   auto_gcroot<ClassA^> a( gcnew ClassA( "first" ) );
   a->PrintHello();
   a.attach( gcnew ClassA( "second" ) ); // attach same type
   a->PrintHello();
   ClassA^ ha = gcnew ClassA( "third" );
   a.attach( ha ); // attach raw handle
   a->PrintHello();
   auto_gcroot<ClassB^> b( gcnew ClassB("fourth") );
   b->PrintHello();
   a.attach( b ); // attach derived type
   a->PrintHello();
}
```

```Output
in ClassA constructor:first
Hello from first A!
in ClassA constructor:second
in ClassA destructor:first
Hello from second A!
in ClassA constructor:third
in ClassA destructor:second
Hello from third A!
in ClassA constructor:fourth
Hello from fourth B!
in ClassA destructor:third
Hello from fourth A!
in ClassA destructor:fourth
```

## <a name="auto_gcrootget"></a><a name="get"></a> auto_gcroot:: get

포함 된 개체를 가져옵니다.

```cpp
_element_type get() const;
```

### <a name="return-value"></a>반환 값

포함된 개체입니다.

### <a name="example"></a>예제

```cpp
// msl_auto_gcroot_get.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ){
      Console::WriteLine( "in ClassA constructor:" + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "in ClassA destructor:" + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

void PrintA( ClassA^ a ) {
   a->PrintHello();
}

int main() {
   auto_gcroot<ClassA^> a = gcnew ClassA( "first" );
   a->PrintHello();

   ClassA^ a2 = a.get();
   a2->PrintHello();

   PrintA( a.get() );
}
```

```Output
in ClassA constructor:first
Hello from first A!
Hello from first A!
Hello from first A!
in ClassA destructor:first
```

## <a name="auto_gcrootrelease"></a><a name="release"></a> auto_gcroot:: release

관리에서 개체를 해제 `auto_gcroot` 합니다.

```cpp
_element_type release();
```

### <a name="return-value"></a>반환 값

릴리스된 개체입니다.

### <a name="example"></a>예제

```cpp
// msl_auto_gcroot_release.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {
      Console::WriteLine( "ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "ClassA destructor: " + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

int main()
{
   ClassA^ a;

   // create a new scope:
   {
      auto_gcroot<ClassA^> agc1 = gcnew ClassA( "first" );
      auto_gcroot<ClassA^> agc2 = gcnew ClassA( "second" );
      a = agc1.release();
   }
   // agc1 and agc2 go out of scope here

   a->PrintHello();

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor: first
ClassA constructor: second
ClassA destructor: second
Hello from first A!
done
```

## <a name="auto_gcrootreset"></a><a name="reset"></a> auto_gcroot:: reset

현재 소유 하 고 있는 개체를 삭제 하 고 필요에 따라 새 개체를 소유 합니다.

```cpp
void reset(
   _element_type _new_ptr = nullptr
);
```

### <a name="parameters"></a>매개 변수

*_new_ptr*<br/>
필드 새 개체입니다.

### <a name="example"></a>예제

```cpp
// msl_auto_gcroot_reset.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {
      Console::WriteLine( "ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "ClassA destructor: " + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

int main()
{
   auto_gcroot<ClassA^> agc1 = gcnew ClassA( "first" );
   agc1->PrintHello();

   ClassA^ ha = gcnew ClassA( "second" );
   agc1.reset( ha ); // release first object, reference second
   agc1->PrintHello();

   agc1.reset(); // release second object, set to nullptr

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor: first
Hello from first A!
ClassA constructor: second
ClassA destructor: first
Hello from second A!
ClassA destructor: second
done
```

## <a name="auto_gcrootswap"></a><a name="swap"></a> auto_gcroot:: swap

다른 개체와 개체를 교환 `auto_gcroot` 합니다.

```cpp
void swap(
   auto_gcroot<_element_type> & _right
);
```

### <a name="parameters"></a>매개 변수

*_right*<br/>
`auto_gcroot`개체를 교환 하는 데 사용할입니다.

### <a name="example"></a>예제

```cpp
// msl_auto_gcroot_swap.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

int main() {
   auto_gcroot<String^> s1 = "string one";
   auto_gcroot<String^> s2 = "string two";

   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
   s1.swap( s2 );
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
}
```

```Output
s1 = 'string one', s2 = 'string two'
s1 = 'string two', s2 = 'string one'
```

## <a name="auto_gcrootoperator-gt"></a><a name="operator-arrow"></a> auto_gcroot:: operator-&gt;

멤버 액세스 연산자입니다.

```cpp
_element_type operator->() const;
```

### <a name="return-value"></a>반환 값

로 래핑된 개체입니다 `auto_gcroot` .

### <a name="example"></a>예제

```cpp
// msl_auto_gcroot_op_arrow.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {}

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }

   int m_i;
};

int main() {
   auto_gcroot<ClassA^> a( gcnew ClassA( "first" ) );
   a->PrintHello();

   a->m_i = 5;
   Console::WriteLine( "a->m_i = {0}", a->m_i );
}
```

```Output
Hello from first A!
a->m_i = 5
```

## <a name="auto_gcrootoperator"></a><a name="operator-assign"></a> auto_gcroot:: operator =

대입 연산자입니다.

```cpp
auto_gcroot<_element_type> & operator=(
   _element_type _right
);
auto_gcroot<_element_type> & operator=(
   auto_gcroot<_element_type> & _right
);
template<typename _other_type>
auto_gcroot<_element_type> & operator=(
   auto_gcroot<_other_type> & _right
);
```

### <a name="parameters"></a>매개 변수

*_right*<br/>
현재에 할당할 개체 또는 `auto_gcroot` `auto_gcroot` 입니다.

### <a name="return-value"></a>반환 값

현재 `auto_gcroot` 소유 하 고 있는 `_right` 입니다.

### <a name="example"></a>예제

```cpp
// msl_auto_gcroot_operator_equals.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA(String^ s) : m_s(s) {
      Console::WriteLine( "in ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "in ClassA destructor: " + m_s );
   }

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class ClassB : ClassA {
public:
   ClassB( String^ s ) : ClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main()
{
   auto_gcroot<ClassA^> a;
   auto_gcroot<ClassA^> a2(gcnew ClassA( "first" ) );
   a = a2; // assign from same type
   a->PrintHello();

   ClassA^ ha = gcnew ClassA( "second" );
   a = ha; // assign from raw handle

   auto_gcroot<ClassB^> b(gcnew ClassB( "third" ) );
   b->PrintHello();
   a = b; // assign from derived type
   a->PrintHello();

   Console::WriteLine("done");
}
```

```Output
in ClassA constructor: first
Hello from first A!
in ClassA constructor: second
in ClassA destructor: first
in ClassA constructor: third
Hello from third B!
in ClassA destructor: second
Hello from third A!
done
in ClassA destructor: third
```

## <a name="auto_gcrootoperator-auto_gcroot"></a><a name="operator-auto-gcroot"></a> auto_gcroot:: operator auto_gcroot

와 호환 되는 형식 사이의 형식 캐스팅 연산자 `auto_gcroot` 입니다.

```cpp
template<typename _other_type>
operator auto_gcroot<_other_type>();
```

### <a name="return-value"></a>반환 값

`auto_gcroot`로 캐스팅 된 현재 `auto_gcroot<_other_type>` 입니다.

### <a name="example"></a>예제

```cpp
// msl_auto_gcroot_op_auto_gcroot.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {}

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class ClassB : ClassA {
public:
   ClassB( String ^ s) : ClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main() {
   auto_gcroot<ClassB^> b = gcnew ClassB("first");
   b->PrintHello();
   auto_gcroot<ClassA^> a = (auto_gcroot<ClassA^>)b;
   a->PrintHello();
}
```

```Output
Hello from first B!
Hello from first A!
```

## <a name="auto_gcrootoperator-bool"></a><a name="operator-bool"></a> auto_gcroot:: operator bool

조건식에 사용 하기 위한 연산자 `auto_gcroot` 입니다.

```cpp
operator bool() const;
```

### <a name="return-value"></a>반환 값

**`true`** 래핑된 개체가 유효 하면이 고, 그렇지 않으면입니다. **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

이 연산자 `_detail_class::_safe_bool` 는 실제 형식으로 변환할 수 없기 때문에 보다 안전한로 변환 됩니다 **`bool`** .

### <a name="example"></a>예제

```cpp
// msl_auto_gcroot_operator_bool.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

int main() {
   auto_gcroot<String^> s;
   if ( s ) Console::WriteLine( "s is valid" );
   if ( !s ) Console::WriteLine( "s is invalid" );
   s = "something";
   if ( s ) Console::WriteLine( "now s is valid" );
   if ( !s ) Console::WriteLine( "now s is invalid" );
   s.reset();
   if ( s ) Console::WriteLine( "now s is valid" );
   if ( !s ) Console::WriteLine( "now s is invalid" );
}
```

```Output
s is invalid
now s is valid
now s is invalid
```

## <a name="auto_gcrootoperator"></a><a name="operator-logical-not"></a> auto_gcroot:: operator!

조건식에 사용 하기 위한 연산자 `auto_gcroot` 입니다.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>반환 값

**`true`** 래핑된 개체가 잘못 된 경우 **`false`** 그렇지 않으면입니다.

### <a name="example"></a>예제

```cpp
// msl_auto_gcroot_operator_not.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

int main() {
   auto_gcroot<String^> s;
   if ( s ) Console::WriteLine( "s is valid" );
   if ( !s ) Console::WriteLine( "s is invalid" );
   s = "something";
   if ( s ) Console::WriteLine( "now s is valid" );
   if ( !s ) Console::WriteLine( "now s is invalid" );
   s.reset();
   if ( s ) Console::WriteLine( "now s is valid" );
   if ( !s ) Console::WriteLine( "now s is invalid" );
}
```

```Output
s is invalid
now s is valid
now s is invalid
```
