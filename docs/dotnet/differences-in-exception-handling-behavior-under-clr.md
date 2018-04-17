---
title: 예외 처리와 CLR에서 동작의에서 차이점 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- EXCEPTION_CONTINUE_EXECUTION macro
- set_se_translator function
ms.assetid: 2e7e8daf-d019-44b0-a51c-62d7aaa89104
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 56bacf88b2c633704b46c6d0de3bb313767b7b2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="differences-in-exception-handling-behavior-under-clr"></a>/CLR을 지정하는 경우 예외 처리 동작의 차이점
[관리 되는 예외 사용의 기본 개념과](../dotnet/basic-concepts-in-using-managed-exceptions.md) 관리 되는 응용 프로그램에서 예외 처리에 대해 설명 합니다. 이 항목에서는 몇 가지 제한 사항이 및 예외 처리의 표준 동작과에서 차이점을 자세히 설명 되어 있습니다. 자세한 내용은 참조 [_set_se_translator 함수](../c-runtime-library/reference/set-se-translator.md)합니다.  
  
##  <a name="vcconjumpingoutofafinallyblock"></a>밖으로의 점프는 Finally 블록  
 점프는 _ _에서 네이티브 C/c + + 코드에서**마지막** 경고를 생성 하지만, 구조적된 예외 처리 (SEH)를 사용 하 여 블록은 사용할 수 있습니다.  아래 [/clr](../build/reference/clr-common-language-runtime-compilation.md)의 점프는 **마지막** 블록에는 오류 발생:  
  
```  
// clr_exception_handling_4.cpp  
// compile with: /clr  
int main() {  
   try {}  
   finally {  
      return 0;   // also fails with goto, break, continue  
    }  
}   // C3276  
```  
  
##  <a name="vcconraisingexceptionswithinanexceptionfilter"></a>예외 필터 내에서 예외 발생  
 처리 하는 동안 예외가 발생 하는 경우는 [예외 필터](../cpp/writing-an-exception-filter.md) 관리 코드 내에서 예외를 포착 하 0을 반환 하는 필터 처럼 처리 합니다.  
  
 이 동작은 동작의 중첩 된 예외를 발생 하는 네이티브 코드는 **ExceptionRecord** 필드에 **EXCEPTION_RECORD** 구조 (반환한 [ GetExceptionInformation](http://msdn.microsoft.com/library/windows/desktop/ms679357))을 설정 및 **ExceptionFlags** 필드 0x10 비트를 설정 합니다. 다음 예제에서는 동작의이 차이 보여 줍니다.  
  
```  
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
  
```  
Caught a nested exception  
We should execute this handler if compiled to native  
```  
  
##  <a name="vccondisassociatedrethrows"></a>끊어진 다시 Throw  
 **/clr** (끊어진된 rethrow 라고도 함) catch 처리기 외부에서 예외가 다시 throw 하는 것을 지원 하지 않습니다. 이러한 종류의 예외가 처리 되는 표준 c + + rethrow로 합니다. 끊어진된 rethrow 활성 관리 되는 예외가 있으면 발생 하는 경우는 c + + 예외로 예외 래핑되고 다시 throw 합니다. 이 유형의 예외 형식의 예외를 낼 수 있습니다 [System::SEHException](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.sehexception.aspx)합니다.  
  
 다음 예제에서는 c + + 예외 다시 throw 하는 관리 되는 예외를 보여 줍니다.  
  
```  
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
  
```  
caught an SEH Exception  
```  
  
##  <a name="vcconexceptionfiltersandexception_continue_execution"></a>예외 필터 및 EXCEPTION_CONTINUE_EXECUTION  
 필터를 반환 하는 경우 `EXCEPTION_CONTINUE_EXECUTION` 관리 되는 응용 프로그램에서 처리 됩니다 필터가 반환 하는 경우 `EXCEPTION_CONTINUE_SEARCH`합니다. 이러한 상수에 대 한 자세한 내용은 참조 하십시오. [시도-문을 제외 하 고](../cpp/try-except-statement.md)합니다.  
  
 다음 예제에서는 이러한 차이 보여 줍니다.  
  
```  
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
  
```  
Counter=-3  
```  
  
##  <a name="vcconthe_set_se_translatorfunction"></a>_Set_se_translator 함수  
 변환기 함수를 호출 하 여 설정 `_set_se_translator`, 비관리 코드에서 catches만 영향을 줍니다. 다음 예제에서는 이러한 제한:  
  
```  
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
  
```  
This is invoked since _set_se_translator is not supported when /clr is used  
In my_trans_func.  
Caught an SEH exception with exception code: e0000101  
```  
  
## <a name="see-also"></a>참고 항목  
 [예외 처리](../windows/exception-handling-cpp-component-extensions.md)   
 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)   
 [예외 처리](../cpp/exception-handling-in-visual-cpp.md)