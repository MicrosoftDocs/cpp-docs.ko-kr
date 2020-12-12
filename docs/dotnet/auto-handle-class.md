---
description: Auto_handle 클래스에 대해 자세히 알아보세요.
title: auto_handle 클래스
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::auto_handle::auto_handle
- msclr::auto_handle::get
- msclr::auto_handle::release
- msclr::auto_handle::reset
- msclr::auto_handle::swap
- msclr::auto_handle::operator->
- msclr::auto_handle::operator=
- msclr::auto_handle::operator auto_handle
- msclr::auto_handle::operator!
helpviewer_keywords:
- msclr::auto_handle class
ms.assetid: a65604d1-ecbb-44fd-ae2f-696ddeeed9d6
ms.openlocfilehash: 9ac93d6b141f24a430aceb97f82fc90046622866
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282655"
---
# <a name="auto_handle-class"></a>auto_handle 클래스

자동 리소스 관리-가상 핸들을 관리 되는 형식에 포함 하는 데 사용할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
template<typename _element_type>
ref class auto_handle;
```

### <a name="parameters"></a>매개 변수

*_element_type*<br/>
포함할 관리 되는 형식입니다.

## <a name="members"></a><a name="members"></a> 멤버

### <a name="public-constructors"></a>Public 생성자  

|Name|설명|  
|---------|-----------|  
|[auto_handle::auto_handle](#auto-handle)|`auto_handle`생성자입니다.|  
|[auto_handle:: ~ auto_handle](#tilde-auto-handle)|`auto_handle`소멸자입니다.|  

### <a name="public-methods"></a>public 메서드  

|Name|설명|  
|---------|-----------|  
|[auto_handle::get](#get)|포함 된 개체를 가져옵니다.|  
|[auto_handle::release](#release)|관리에서 개체를 해제 `auto_handle` 합니다.|
|[auto_handle::reset](#reset)|현재 소유 하 고 있는 개체를 삭제 하 고 필요에 따라 새 개체를 소유 합니다.|
|[auto_handle::swap](#swap)|다른 개체와 개체를 교환 `auto_handle` 합니다.|  

### <a name="public-operators"></a>Public 연산자

|Name|설명|  
|---------|-----------|
|[auto_handle:: operator-&gt;](#operator-arrow)|멤버 액세스 연산자입니다.|
|[auto_handle::operator=](#operator-assign)|대입 연산자입니다.|
|[auto_handle::operator auto_handle](#operator-auto-handle)|와 호환 되는 형식 사이의 형식 캐스팅 연산자 `auto_handle` 입니다.|  
|[auto_handle::operator bool](#operator-bool)|조건식에 사용 하기 위한 연산자 `auto_handle` 입니다.|
|[auto_handle:: operator!](#operator-logical-not)|조건식에 사용 하기 위한 연산자 `auto_handle` 입니다.|  

## <a name="requirements"></a>요구 사항

**헤더 파일** \<msclr\auto_handle.h>

Msclr **네임 스페이스**

## <a name="auto_handleauto_handle"></a><a name="auto-handle"></a> auto_handle:: auto_handle

`auto_handle`생성자입니다.

```cpp
auto_handle();
auto_handle(
   _element_type ^ _ptr
);
auto_handle(
   auto_handle<_element_type> % _right
);
template<typename _other_type>
auto_handle(
   auto_handle<_other_type> % _right
);
```

### <a name="parameters"></a>매개 변수

*_ptr*<br/>
소유할 개체입니다.

*_right*<br/>
기존 `auto_handle`입니다.

### <a name="example"></a>예제

```cpp
// msl_auto_handle_auto_handle.cpp
// compile with: /clr
#include "msclr\auto_handle.h"

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

int main()
{
   {
      auto_handle<RefClassA> a(gcnew RefClassA( "first" ) );
      a->PrintHello();
   }

   {
      auto_handle<RefClassB> b(gcnew RefClassB( "second" ) );
      b->PrintHello();
      auto_handle<RefClassA> a(b); //construct from derived type
      a->PrintHello();
      auto_handle<RefClassA> a2(a); //construct from same type
      a2->PrintHello();
   }

   Console::WriteLine("done");
}
```

```Output
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

## <a name="auto_handleauto_handle"></a><a name="tilde-auto-handle"></a> auto_handle:: ~ auto_handle

`auto_handle`소멸자입니다.

```cpp
~auto_handle();
```

### <a name="remarks"></a>설명

소멸자는 소유 된 개체도 destructs 합니다.

### <a name="example"></a>예제

```cpp
// msl_auto_handle_dtor.cpp
// compile with: /clr
#include "msclr\auto_handle.h"

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
      auto_handle<ClassA> a = gcnew ClassA;
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

## <a name="auto_handleget"></a><a name="get"></a> auto_handle:: get

포함 된 개체를 가져옵니다.

```cpp
_element_type ^ get();
```

### <a name="return-value"></a>반환 값

포함된 개체입니다.

### <a name="example"></a>예제

```cpp
// msl_auto_handle_get.cpp
// compile with: /clr
#include "msclr\auto_handle.h"

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
   auto_handle<ClassA> a = gcnew ClassA( "first" );
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

## <a name="auto_handlerelease"></a><a name="release"></a> auto_handle:: release

관리에서 개체를 해제 `auto_handle` 합니다.

```cpp
_element_type ^ release();
```

### <a name="return-value"></a>반환 값

릴리스된 개체입니다.

### <a name="example"></a>예제

```cpp
// msl_auto_handle_release.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

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
      auto_handle<ClassA> agc1 = gcnew ClassA( "first" );
      auto_handle<ClassA> agc2 = gcnew ClassA( "second" );
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

## <a name="auto_handlereset"></a><a name="reset"></a> auto_handle:: reset

현재 소유 하 고 있는 개체를 삭제 하 고 필요에 따라 새 개체를 소유 합니다.

```cpp
void reset(
   _element_type ^ _new_ptr
);
void reset();
```

### <a name="parameters"></a>매개 변수

*_new_ptr*<br/>
필드 새 개체입니다.

### <a name="example"></a>예제

```cpp
// msl_auto_handle_reset.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

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
   auto_handle<ClassA> agc1 = gcnew ClassA( "first" );
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

## <a name="auto_handleswap"></a><a name="swap"></a> auto_handle:: swap

다른 개체와 개체를 교환 `auto_handle` 합니다.

```cpp
void swap(
   auto_handle<_element_type> % _right
);
```

### <a name="parameters"></a>매개 변수

*_right*<br/>
`auto_handle`개체를 교환 하는 데 사용할입니다.

### <a name="example"></a>예제

```cpp
// msl_auto_handle_swap.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1 = "string one";
   auto_handle<String> s2 = "string two";

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

## <a name="auto_handleoperator-gt"></a><a name="operator-arrow"></a> auto_handle:: operator-&gt;

멤버 액세스 연산자입니다.

```cpp
_element_type ^ operator->();
```

### <a name="return-value"></a>반환 값

로 래핑된 개체입니다 `auto_handle` .

### <a name="example"></a>예제

```cpp
// msl_auto_handle_op_arrow.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

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
   auto_handle<ClassA> a( gcnew ClassA( "first" ) );
   a->PrintHello();

   a->m_i = 5;
   Console::WriteLine( "a->m_i = {0}", a->m_i );
}
```

```Output
Hello from first A!
a->m_i = 5
```

## <a name="auto_handleoperator"></a><a name="operator-assign"></a> auto_handle:: operator =

대입 연산자입니다.

```cpp
auto_handle<_element_type> % operator=(
   auto_handle<_element_type> % _right
);
template<typename _other_type>
auto_handle<_element_type> % operator=(
   auto_handle<_other_type> % _right
);
```

### <a name="parameters"></a>매개 변수

*_right*<br/>
`auto_handle`현재에 할당할 `auto_handle` 입니다.

### <a name="return-value"></a>반환 값

현재 `auto_handle` 소유 하 고 있는 `_right` 입니다.

### <a name="example"></a>예제

```cpp
// msl_auto_handle_op_assign.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

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
   auto_handle<ClassA> a;
   auto_handle<ClassA> a2(gcnew ClassA( "first" ) );
   a = a2; // assign from same type
   a->PrintHello();

   auto_handle<ClassB> b(gcnew ClassB( "second" ) );
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
Hello from second B!
in ClassA destructor: first
Hello from second A!
done
in ClassA destructor: second
```

## <a name="auto_handleoperator-auto_handle"></a><a name="operator-auto-handle"></a> auto_handle:: operator auto_handle

와 호환 되는 형식 사이의 형식 캐스팅 연산자 `auto_handle` 입니다.

```cpp
template<typename _other_type>
operator auto_handle<_other_type>();
```

### <a name="return-value"></a>반환 값

`auto_handle`로 캐스팅 된 현재 `auto_handle<_other_type>` 입니다.

### <a name="example"></a>예제

```cpp
// msl_auto_handle_op_auto_handle.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

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
   auto_handle<ClassB> b = gcnew ClassB("first");
   b->PrintHello();
   auto_handle<ClassA> a = (auto_handle<ClassA>)b;
   a->PrintHello();
}
```

```Output
Hello from first B!
Hello from first A!
```

## <a name="auto_handleoperator-bool"></a><a name="operator-bool"></a> auto_handle:: operator bool

조건식에 사용 하기 위한 연산자 `auto_handle` 입니다.

```cpp
operator bool();
```

### <a name="return-value"></a>반환 값

**`true`** 래핑된 개체가 유효 하면이 고, 그렇지 않으면입니다. **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

이 연산자는를 `_detail_class::_safe_bool` **`bool`** 정수 계열 형식으로 변환할 수 없기 때문에 보다 안전한로 변환 됩니다.

### <a name="example"></a>예제

```cpp
// msl_auto_handle_operator_bool.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1;
   auto_handle<String> s2 = "hi";
   if ( s1 ) Console::WriteLine( "s1 is valid" );
   if ( !s1 ) Console::WriteLine( "s1 is invalid" );
   if ( s2 ) Console::WriteLine( "s2 is valid" );
   if ( !s2 ) Console::WriteLine( "s2 is invalid" );
   s2.reset();
   if ( s2 ) Console::WriteLine( "s2 is now valid" );
   if ( !s2 ) Console::WriteLine( "s2 is now invalid" );
}
```

```Output
s1 is invalid
s2 is valid
s2 is now invalid
```

## <a name="auto_handleoperator"></a><a name="operator-logical-not"></a> auto_handle:: operator!

조건식에 사용 하기 위한 연산자 `auto_handle` 입니다.

```cpp
bool operator!();
```

### <a name="return-value"></a>반환 값

**`true`** 래핑된 개체가 잘못 된 경우 **`false`** 그렇지 않으면입니다.

### <a name="example"></a>예제

```cpp
// msl_auto_handle_operator_not.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1;
   auto_handle<String> s2 = "something";
   if ( s1) Console::WriteLine( "s1 is valid" );
   if ( !s1 ) Console::WriteLine( "s1 is invalid" );
   if ( s2 ) Console::WriteLine( "s2 is valid" );
   if ( !s2 ) Console::WriteLine( "s2 is invalid" );
   s2.reset();
   if ( s2 ) Console::WriteLine( "s2 is now valid" );
   if ( !s2 ) Console::WriteLine( "s2 is now invalid" );
}
```

```Output
s1 is invalid
s2 is valid
s2 is now invalid
```
