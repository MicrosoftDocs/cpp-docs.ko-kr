---
description: '자세한 정보: &lt; 예외 &gt; 함수'
title: '&lt;exception&gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- exception/std::current_exception
- exception/std::get_terminate
- exception/std::get_unexpected
- exception/std::make_exception_ptr
- exception/std::rethrow_exception
- exception/std::set_terminate
- exception/std::set_unexpected
- exception/std::terminate
- exception/std::uncaught_exception
- exception/std::unexpected
ms.assetid: c09ac569-5e35-4fe8-872d-ca5810274dd7
helpviewer_keywords:
- std::current_exception [C++]
- std::get_terminate [C++]
- std::get_unexpected [C++]
- std::make_exception_ptr [C++]
- std::rethrow_exception [C++]
- std::set_terminate [C++]
- std::set_unexpected [C++]
- std::terminate [C++]
- std::uncaught_exception [C++]
- std::unexpected [C++]
ms.openlocfilehash: f885b75462c2c7e20552d33e63048e7a55a51d67
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232566"
---
# <a name="ltexceptiongt-functions"></a>&lt;exception&gt; 함수

## <a name="current_exception"></a><a name="current_exception"></a> current_exception

현재 예외에 대한 스마트 포인터를 가져옵니다.

```cpp
exception_ptr current_exception();
```

### <a name="return-value"></a>반환 값

현재 예외를 가리키는 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) 개체입니다.

### <a name="remarks"></a>설명

catch 블록에서 `current_exception` 함수를 호출합니다. 예외가 발생하고 catch 블록이 예외를 catch할 경우, `current_exception` 함수는 예외를 참조하는 `exception_ptr` 개체를 반환합니다. 그렇지 않으면 인수가 null `exception_ptr` 개체를 반환합니다.

`current_exception`함수는 **`catch`** 문이 [예외 선언](../cpp/try-throw-and-catch-statements-cpp.md) 문을 지정 하는지 여부에 관계 없이 비행 중인 예외를 캡처합니다.

예외를 다시 throw 하지 않는 경우 현재 예외에 대 한 소멸자가 블록의 끝에 호출 됩니다 **`catch`** . 그러나 소멸자에 있는`current_exception` 함수를 호출하는 경우, 함수는 현재 예외를 참조하는 `exception_ptr` 개체를 반환합니다.

`current_exception` 수식에 대한 연속 호출은 현재 예외 건의 다른 복사본을 뜻하는 `exception_ptr` 개체를 반환합니다. 따라서 개체는 복사본에 같은 이진 값이 있더라도 다른 복사본을 참조하기 때문에 같지 않은 것으로 비교합니다.

## <a name="make_exception_ptr"></a><a name="make_exception_ptr"></a> make_exception_ptr

예외 복사본이 들어 있는 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) 개체를 생성합니다.

```cpp
template <class E>
    exception_ptr make_exception_ptr(E Except);
```

### <a name="parameters"></a>매개 변수

*남기고*\
복사할 예외가 있는 클래스입니다. 모든 클래스 개체를 인수로 사용할 수 있지만, 일반적으로 [예외 클래스](../standard-library/exception-class.md) 개체를 `make_exception_ptr` 함수의 인수로 지정합니다.

### <a name="return-value"></a>반환 값

*제외* 에 대 한 현재 예외의 복사본을 가리키는 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) 개체입니다.

### <a name="remarks"></a>설명

`make_exception_ptr` 함수 호출은 C++ 예외를 throw하고 catch 블록에서 catch한 다음 [current_exception](../standard-library/exception-functions.md#current_exception) 함수를 호출하여 예외를 참조하는 `exception_ptr` 개체를 반환하는 것과 동일합니다. `make_exception_ptr` 함수의 Microsoft 구현은 예외를 throw한 후 catch하는 것보다 더 효율적입니다.

애플리케이션에는 일반적으로 `make_exception_ptr` 함수가 필요하지 않으며 이 함수를 사용하지 않는 것이 좋습니다.

## <a name="rethrow_exception"></a><a name="rethrow_exception"></a> rethrow_exception

매개 변수로 전달되는 예외를 throw합니다.

```cpp
void rethrow_exception(exception_ptr P);
```

### <a name="parameters"></a>매개 변수

*®*\
다시 throw할 catch된 예외입니다. *P* 가 null [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)경우 함수는 [std:: bad_exception](../standard-library/bad-exception-class.md)을 throw 합니다.

### <a name="remarks"></a>설명

`exception_ptr` 개체에서 catch된 예외를 저장한 후 기본 스레드에서 개체를 처리할 수 있습니다. 기본 스레드에서 `rethrow_exception` 개체와 함께 작동하는 `exception_ptr` 함수를 호출합니다. `rethrow_exception` 함수는 `exception_ptr` 개체에서 예외를 추출하고, 주 스레드의 컨텍스트에서 예외를 throw합니다.

## <a name="get_terminate"></a><a name="get_terminate"></a> get_terminate

현재 `terminate_handler` 함수를 가져옵니다.

```cpp
terminate_handler get_terminate();
```

## <a name="set_terminate"></a><a name="set_terminate"></a> set_terminate

프로그램을 종료할 때 호출할 새 `terminate_handler`를 설정합니다.

```cpp
terminate_handler set_terminate(terminate_handler fnew) throw();
```

### <a name="parameters"></a>매개 변수

*fnew*\
종료 시 호출할 함수입니다.

### <a name="return-value"></a>반환 값

종료 시 호출에 사용된 이전 함수의 주소입니다.

### <a name="remarks"></a>설명

함수는 새 [terminate_handler](../standard-library/exception-typedefs.md#terminate_handler) 를 * *fnew* 함수로 설정 합니다. 따라서 *fnew* 는 null 포인터가 아니어야 합니다. 함수는 이전 terminate 처리기의 주소를 반환합니다.

### <a name="example"></a>예제

```cpp
// exception_set_terminate.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void termfunction()
{
    cout << "My terminate function called." << endl;
    abort();
}

int main()
{
    terminate_handler oldHandler = set_terminate(termfunction);

    // Throwing an unhandled exception would also terminate the program
    // or we could explicitly call terminate();

    //throw bad_alloc();
    terminate();
}
```

## <a name="get_unexpected"></a><a name="get_unexpected"></a> get_unexpected

현재 `unexpected_handler` 함수를 가져옵니다.

```cpp
unexpected_handler get_unexpected();
```

## <a name="rethrow_if_nested"></a><a name="rethrow_if_nested"></a> rethrow_if_nested

```cpp
template <class E>
    void rethrow_if_nested(const E& e);
```

### <a name="remarks"></a>설명

다형 클래스 형식이 아니거나에 `nested_exception` 액세스할 수 없거나 모호한 경우에는 아무런 영향도 주지 않습니다. 그렇지 않으면에서 동적 캐스트를 수행 합니다.

## <a name="set_unexpected"></a><a name="set_unexpected"></a> set_unexpected

예기치 않은 예외가 발생할 경우를 위해 새 `unexpected_handler`를 설정합니다.

```cpp
unexpected_handler set_unexpected(unexpected_handler fnew) throw();
```

### <a name="parameters"></a>매개 변수

*fnew*\
예기치 않은 예외가 발생할 경우를 호출할 함수입니다.

### <a name="return-value"></a>반환 값

이전 `unexpected_handler`의 주소입니다.

### <a name="remarks"></a>설명

*fnew* 는 null 포인터가 아니어야 합니다.

C++ 표준의 경우 함수가 throw 목록에 없는 예외를 throw할 경우 `unexpected`가 호출되어야 합니다. 현재 구현은 이 기능을 지원하지 않습니다. 다음 예제에서는 `unexpected`를 직접 호출하고 나서 `unexpected_handler`를 호출합니다.

### <a name="example"></a>예제

```cpp
// exception_set_unexpected.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void uefunction()
{
    cout << "My unhandled exception function called." << endl;
    terminate(); // this is what unexpected() calls by default
}

int main()
{
    unexpected_handler oldHandler = set_unexpected(uefunction);

    unexpected(); // library function to force calling the
                  // current unexpected handler
}
```

## <a name="terminate"></a><a name="terminate"></a> 끝나야

종료 처리기를 호출합니다.

```cpp
void terminate();
```

### <a name="remarks"></a>설명

함수는 형식의 함수인 terminate 처리기를 호출 합니다 **`void`** . `terminate`프로그램이 프로그램에 의해 직접 호출 되는 경우 terminate 처리기는 [set_terminate](../standard-library/exception-functions.md#set_terminate)에 대 한 호출에 의해 가장 최근에 설정 된 것입니다. `terminate`Throw 식을 평가 하는 동안 다른 여러 가지 이유로를 호출 하는 경우에는 throw 식을 평가한 후 즉시 terminate 핸들러가 적용 됩니다.

terminate 처리기는 호출자로 반환되지 않을 수 있습니다. 프로그램을 시작할 때 terminate 처리기는를 호출 하는 함수입니다 `abort` .

### <a name="example"></a>예제

`terminate` 사용에 대한 예제는 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)를 참조하세요.

## <a name="throw_with_nested"></a><a name="throw_with_nested"></a> throw_with_nested

```cpp
template <class T> [[noreturn]]
    void throw_with_nested(T&& t);
```

### <a name="remarks"></a>설명

예외를 throw 하는 예외를 throw 합니다.

## <a name="uncaught_exception"></a><a name="uncaught_exception"></a> uncaught_exception

**`true`** Throw 된 예외가 현재 처리 되 고 있는 경우에만를 반환 합니다.

```cpp
bool uncaught_exception();
```

### <a name="return-value"></a>반환 값

**`true`** Throw 식의 계산을 완료 한 후와 일치 하는 처리기에서 예외 선언의 초기화를 완료 하거나 throw 식의 결과로 [예기치 않은](../standard-library/exception-functions.md#unexpected) 을 호출 하기 전에를 반환 합니다. 특히 `uncaught_exception` 는 **`true`** 예외 해제 중에 호출 되는 소멸자에서 호출 될 때를 반환 합니다. 디바이스의 경우 `uncaught_exception`은 Windows Mobile 2005 플랫폼을 포함하여 Windows CE 5.00 이상 버전에서만 지원됩니다.

### <a name="example"></a>예제

```cpp
// exception_uncaught_exception.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>
#include <string>

class Test
{
public:
   Test( std::string msg ) : m_msg( msg )
   {
      std::cout << "In Test::Test(\"" << m_msg << "\")" << std::endl;
   }
   ~Test( )
   {
      std::cout << "In Test::~Test(\"" << m_msg << "\")" << std::endl
         << "        std::uncaught_exception( ) = "
         << std::uncaught_exception( )
         << std::endl;
   }
private:
    std::string m_msg;
};

// uncaught_exception will be true in the destructor
// for the object created inside the try block because
// the destructor is being called as part of the unwind.

int main( void )
   {
      Test t1( "outside try block" );
      try
      {
         Test t2( "inside try block" );
         throw 1;
      }
      catch (...) {
   }
}
```

```Output
In Test::Test("outside try block")
In Test::Test("inside try block")
In Test::~Test("inside try block")
        std::uncaught_exception( ) = 1
In Test::~Test("outside try block")
        std::uncaught_exception( ) = 0
```

## <a name="unexpected"></a><a name="unexpected"></a> 없는

unexpected 처리기를 호출합니다.

```cpp
void unexpected();
```

### <a name="remarks"></a>설명

C++ 표준의 경우 함수가 throw 목록에 없는 예외를 throw할 경우 `unexpected`가 호출되어야 합니다. 현재 구현은 이 기능을 지원하지 않습니다. 이 예제에서는 unexpected 처리기를 호출하는 `unexpected`를 직접 호출합니다.

함수는 형식의 함수인 예기치 않은 처리기를 호출 합니다 **`void`** . `unexpected`가 프로그램에 의해 직접 호출될 경우 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)에 대한 호출을 통해 가장 최근 설정된 unexpected 처리기가 호출됩니다.

unexpected 처리기는 호출자로 반환되지 않을 수 있습니다. 다음과 같은 경우 실행을 종료할 수 있습니다.

- 예외 사양에 나열된 형식의 개체 또는 unexpected 처리기가 프로그램에서 직접 호출될 경우 모든 형식의 개체를 throw할 경우.

- 형식 [bad_exception](../standard-library/bad-exception-class.md)의 개체를 throw할 경우.

- [Terminate](../standard-library/exception-functions.md#terminate)또는를 `abort` 호출 `exit` 합니다.

프로그램 시작 시 [terminate](../standard-library/exception-functions.md#terminate)를 호출하는 함수가 unexpected 처리기입니다.

### <a name="example"></a>예제

`unexpected` 사용에 대한 예제는 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)를 참조하세요.
