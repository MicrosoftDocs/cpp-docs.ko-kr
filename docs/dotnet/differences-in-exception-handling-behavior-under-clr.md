---
description: 자세한 정보:/CLR에서 예외 처리 동작의 차이점
title: -CLR에서 예외 처리 동작의 차이점
ms.date: 11/04/2016
helpviewer_keywords:
- EXCEPTION_CONTINUE_EXECUTION macro
- set_se_translator function
ms.assetid: 2e7e8daf-d019-44b0-a51c-62d7aaa89104
ms.openlocfilehash: e7e07778e894448fea3d29acb3a32d71884be57c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97252196"
---
# <a name="differences-in-exception-handling-behavior-under-clr"></a>/CLR을 지정하는 경우 예외 처리 동작의 차이점

관리 [되는 예외 사용의 기본 개념](../dotnet/basic-concepts-in-using-managed-exceptions.md) 에서는 관리 되는 응용 프로그램의 예외 처리에 대해 설명 합니다. 이 항목에서는 예외 처리의 표준 동작과 다른 몇 가지 제한 사항에 대해 자세히 설명 합니다. 자세한 내용은 [_Set_se_translator 함수](../c-runtime-library/reference/set-se-translator.md)를 참조 하세요.

## <a name="jumping-out-of-a-finally-block"></a><a name="vcconjumpingoutofafinallyblock"></a> Finally 블록 밖으로 점프

네이티브 C/c + + 코드에서 SEH (구조적 예외 처리)를 사용 하는 __ **finally** 블록 밖으로 점프 하면 경고가 생성 되지만  [/Clr](../build/reference/clr-common-language-runtime-compilation.md)에서 **finally** 블록 밖으로 점프 하면 오류가 발생 합니다.

```cpp
// clr_exception_handling_4.cpp
// compile with: /clr
int main() {
   try {}
   finally {
      return 0;   // also fails with goto, break, continue
    }
}   // C3276
```

## <a name="raising-exceptions-within-an-exception-filter"></a><a name="vcconraisingexceptionswithinanexceptionfilter"></a> 예외 필터 내에서 예외 발생

관리 코드 내에서 [예외 필터](../cpp/writing-an-exception-filter.md) 를 처리 하는 동안 예외가 발생 하면 예외가 catch 되 고 필터에서 0을 반환 하는 것 처럼 처리 됩니다.

이는 중첩 된 예외가 발생 하 고, [Getexceptioninformation](/windows/win32/Debug/getexceptioninformation)에서 반환 된 **EXCEPTION_RECORD** 구조체의 **exceptionrecord** 필드가 설정 되 고, **exceptionrecord** 필드가 0x10 비트를 설정 하는 네이티브 코드의 동작과는 대조적입니다. 다음 예에서는 이러한 동작의 차이를 보여 줍니다.

```cpp
// clr_exception_handling_5.cpp
#include <windows.h>
#include <stdio.h>
#include <assert.h>

#ifndef false
#define false 0
#endif

int *p;

int filter(PEXCEPTION_POINTERS ExceptionPointers) {
   PEXCEPTION_RECORD ExceptionRecord =
                     ExceptionPointers->ExceptionRecord;

   if ((ExceptionRecord->ExceptionFlags & 0x10) == 0) {
      // not a nested exception, throw one
      *p = 0; // throw another AV
   }
   else {
      printf("Caught a nested exception\n");
      return 1;
    }

   assert(false);

   return 0;
}

void f(void) {
   __try {
      *p = 0;   // throw an AV
   }
   __except(filter(GetExceptionInformation())) {
      printf_s("We should execute this handler if "
                 "compiled to native\n");
    }
}

int main() {
   __try {
      f();
   }
   __except(1) {
      printf_s("The handler in main caught the "
               "exception\n");
    }
}
```

### <a name="output"></a>출력

```Output
Caught a nested exception
We should execute this handler if compiled to native
```

## <a name="disassociated-rethrows"></a><a name="vccondisassociatedrethrows"></a> 연결이 끊긴 다시 throw

**/clr** 은 catch 처리기 외부에서 예외를 다시 throw 하는 것을 지원 하지 않습니다 (연결이 끊긴 다시 throw 라고 함). 이 형식의 예외는 표준 c + + 다시 throw로 처리 됩니다. 활성 관리 되는 예외가 있을 때 연결이 끊긴 다시 throw가 발생 하면 예외가 c + + 예외로 래핑되어 다시 throw 됩니다. 이 형식의 예외는 형식의 예외로 catch 될 수 있습니다 <xref:System.Runtime.InteropServices.SEHException> .

다음 예제에서는 c + + 예외로 다시 throw 된 관리 되는 예외를 보여 줍니다.

```cpp
// clr_exception_handling_6.cpp
// compile with: /clr
using namespace System;
#include <assert.h>
#include <stdio.h>

void rethrow( void ) {
   // This rethrow is a dissasociated rethrow.
   // The exception would be masked as SEHException.
   throw;
}

int main() {
   try {
      try {
         throw gcnew ApplicationException;
      }
      catch ( ApplicationException^ ) {
         rethrow();
         // If the call to rethrow() is replaced with
         // a throw statement within the catch handler,
         // the rethrow would be a managed rethrow and
         // the exception type would remain
         // System::ApplicationException
      }
   }

    catch ( ApplicationException^ ) {
      assert( false );

      // This will not be executed since the exception
      // will be masked as SEHException.
    }
   catch ( Runtime::InteropServices::SEHException^ ) {
      printf_s("caught an SEH Exception\n" );
    }
}
```

### <a name="output"></a>출력

```Output
caught an SEH Exception
```

## <a name="exception-filters-and-exception_continue_execution"></a><a name="vcconexceptionfiltersandexception_continue_execution"></a> 예외 필터 및 EXCEPTION_CONTINUE_EXECUTION

필터가 `EXCEPTION_CONTINUE_EXECUTION` 관리 되는 응용 프로그램에서 반환 되는 경우 필터가 반환 된 것 처럼 처리 됩니다 `EXCEPTION_CONTINUE_SEARCH` . 이러한 상수에 대 한 자세한 내용은 [try-Except 문](../cpp/try-except-statement.md)을 참조 하십시오.

다음 예제에서는 이러한 차이를 보여 줍니다.

```cpp
// clr_exception_handling_7.cpp
#include <windows.h>
#include <stdio.h>
#include <assert.h>

int main() {
   int Counter = 0;
   __try {
      __try  {
         Counter -= 1;
         RaiseException (0xe0000000|'seh',
                         0, 0, 0);
         Counter -= 2;
      }
      __except (Counter) {
         // Counter is negative,
         // indicating "CONTINUE EXECUTE"
         Counter -= 1;
      }
    }
    __except(1) {
      Counter -= 100;
   }

   printf_s("Counter=%d\n", Counter);
}
```

### <a name="output"></a>출력

```Output
Counter=-3
```

## <a name="the-_set_se_translator-function"></a><a name="vcconthe_set_se_translatorfunction"></a> _Set_se_translator 함수

에 대 한 호출로 설정 된 translator 함수는 `_set_se_translator` 비관리 코드의 catch에만 영향을 줍니다. 다음 예에서는 이러한 제한 사항을 보여 줍니다.

```cpp
// clr_exception_handling_8.cpp
// compile with: /clr /EHa
#include <iostream>
#include <windows.h>
#include <eh.h>
#pragma warning (disable: 4101)
using namespace std;
using namespace System;

#define MYEXCEPTION_CODE 0xe0000101

class CMyException {
public:
   unsigned int m_ErrorCode;
   EXCEPTION_POINTERS * m_pExp;

   CMyException() : m_ErrorCode( 0 ), m_pExp( NULL ) {}

   CMyException( unsigned int i, EXCEPTION_POINTERS * pExp )
         : m_ErrorCode( i ), m_pExp( pExp ) {}

   CMyException( CMyException& c ) : m_ErrorCode( c.m_ErrorCode ),
                                      m_pExp( c.m_pExp ) {}

   friend ostream& operator <<
                 ( ostream& out, const CMyException& inst ) {
      return out <<  "CMyException[\n" <<
             "Error Code: " << inst.m_ErrorCode <<  "]";
    }
};

#pragma unmanaged
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS pExp ) {
   cout <<  "In my_trans_func.\n";
   throw CMyException( u, pExp );
}

#pragma managed
void managed_func() {
   try  {
      RaiseException( MYEXCEPTION_CODE, 0, 0, 0 );
   }
   catch ( CMyException x ) {}
   catch ( ... ) {
      printf_s("This is invoked since "
               "_set_se_translator is not "
               "supported when /clr is used\n" );
    }
}

#pragma unmanaged
void unmanaged_func() {
   try  {
      RaiseException( MYEXCEPTION_CODE,
                      0, 0, 0 );
   }
   catch ( CMyException x ) {
      printf("Caught an SEH exception with "
             "exception code: %x\n", x.m_ErrorCode );
    }
    catch ( ... ) {}
}

// #pragma managed
int main( int argc, char ** argv ) {
   _set_se_translator( my_trans_func );

   // It does not matter whether the translator function
   // is registered in managed or unmanaged code
   managed_func();
   unmanaged_func();
}
```

### <a name="output"></a>출력

```Output
This is invoked since _set_se_translator is not supported when /clr is used
In my_trans_func.
Caught an SEH exception with exception code: e0000101
```

## <a name="see-also"></a>참조

[예외 처리](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[MSVC의 예외 처리](../cpp/exception-handling-in-visual-cpp.md)
