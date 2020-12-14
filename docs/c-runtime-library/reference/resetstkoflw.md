---
description: '다음에 대 한 자세한 정보: _resetstkoflw'
title: _resetstkoflw
ms.date: 4/2/2020
api_name:
- _resetstkoflw
- _o__resetstkoflw
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- resetstkoflw
- _resetstkoflw
helpviewer_keywords:
- resetstkoflw function
- stack overflow
- stack, recovering
- _resetstkoflw function
ms.assetid: 319529cd-4306-4d22-810b-2063f3ad9e14
ms.openlocfilehash: 02eb973c63bb372e43e57c413385b8e1b13d9f38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250350"
---
# <a name="_resetstkoflw"></a>_resetstkoflw

스택 오버플로에서 복구합니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int _resetstkoflw( void );
```

## <a name="return-value"></a>Return Value

함수가 성공하면 0이 아닌 값이고, 실패하면 0입니다.

## <a name="remarks"></a>설명

**_Resetstkoflw** 함수는 스택 오버플로 상태에서 복구 하 여 심각한 예외 오류로 인해 프로그램이 실패 하는 대신 계속할 수 있도록 합니다. **_Resetstkoflw** 함수를 호출 하지 않으면 이전 예외 다음에 가드 페이지가 없습니다. 다음번에 스택 오버플로가 발생하는 경우에는 예외가 전혀 발생하지 않으며 프로세스는 경고 없이 종료됩니다.

애플리케이션의 스레드에서 **EXCEPTION_STACK_OVERFLOW** 예외가 발생하는 경우 스레드의 스택이 손상된 상태로 남습니다. 이는 스택이 손상되지 않는 **EXCEPTION_ACCESS_VIOLATION** 또는 **EXCEPTION_INT_DIVIDE_BY_ZERO** 와 같은 다른 예외와 반대입니다. 프로그램이 처음 로드될 때 스택은 임의로 작은 값으로 설정됩니다. 그런 다음 스택은 스레드의 요구 사항을 충족하도록 요구에 맞게 증가합니다. 이는 PAGE_GUARD가 있는 페이지를 현재 스택의 끝에 배치하여 구현됩니다. 자세한 내용은 [가드 페이지 만들기](/windows/win32/Memory/creating-guard-pages)를 참조하세요.

코드로 인해 스택 포인터가 이 페이지의 주소를 가리키는 경우 예외가 발생하고 시스템에서 다음 세 가지 작업이 수행됩니다.

- 스레드에서 데이터를 읽고 메모리에 쓸 수 있도록 가드 페이지의 PAGE_GUARD 보호를 제거합니다.

- 마지막 페이지에서 한 페이지 아래에 위치한 새 가드 페이지를 할당합니다.

- 예외를 발생시킨 명령을 다시 실행합니다.

이러한 방식으로 시스템은 자동으로 스레드에 대한 스택의 크기를 늘릴 수 있습니다. 프로세스의 각 스레드는 최대 스택 크기를 가집니다. 스택 크기는 [/STACK(스택 할당)](../../build/reference/stack-stack-allocations.md) 또는 프로젝트에 대한 .def 파일에 있는 [STACKSIZE](../../build/reference/stacksize.md) 문에 의해 컴파일 시간에 설정됩니다.

이 최대 스택 크기를 초과하면 시스템에서 다음 세 가지 작업을 수행합니다.

- 앞에서 설명한 대로 가드 페이지에 대한 PAGE_GUARD 보호를 제거합니다.

- 새 가드 페이지를 마지막 가드 페이지 아래에 할당하려고 합니다. 그러나 최대 스택 크기를 초과했기 때문에 이러한 작업이 실패합니다.

- 스레드가 예외 블록에서 처리할 수 있도록 예외를 발생시킵니다.

여기서 스택은 더 이상 가드 페이지를 포함하지 않습니다. 다음에 프로그램이 가드 페이지가 있어야 하는 끝 부분까지 계속 스택을 증가시킬 때 프로그램은 스택의 끝을 벗어나 쓰며 액세스 위반을 발생시킵니다.

스택 오버플로 예외가 발생 한 후 복구가 수행 될 때마다 가드 페이지를 복원 하려면 **_resetstkoflw** 를 호출 합니다. 이 함수는 블록의 주 본문 내부 또는 블록 외부에서 호출할 수 있습니다 **`__except`** **`__except`** . 그러나 사용할 때 몇 가지 제한 사항이 있습니다. **_resetstkoflw** 는 다음에서 호출 하면 안 됩니다.

- 필터 식

- 필터 함수

- 필터 함수에서 호출한 함수

- **`catch`** 블록입니다.

- **`__finally`** 블록입니다.

이러한 지점에서 스택이 아직 충분하게 해제되지 않습니다.

스택 오버플로 예외는 c + + 예외가 아닌 구조적 예외로 생성 되므로 **_resetstkoflw** 는 **`catch`** 스택 오버플로 예외를 catch 하지 않기 때문에 일반 블록에서 유용 하지 않습니다. 그러나 [_set_se_translator](set-se-translator.md)가 C++ 예외를 throw하는 구조적 예외 변환기를 구현하는 데 사용되는 경우(두 번째 예제) 스택 오버플로 예외는 C++ catch 블록에 의해 처리될 수 있는 C++ 예외를 발생시킵니다.

구조적 예외 변환기 함수에 의해 throw된 예외로부터 도달한 C++ catch 블록에서 **_resetstkoflw** 를 호출하는 것은 안전하지 않습니다. 이 경우 catch 블럭 이전에 소멸적인 개체에 대한 소멸자가 호출되었어도 catch 블럭 외부까지 스택 공간이 비워지지 않고 스택 포인터가 다시 설정되지 않습니다. 이 함수는 스택 공간이 비워지고 스택 포인터가 다시 설정될 때까지 호출되지 않아야 합니다. 따라서 catch 블록을 종료한 후에만 이 함수를 호출해야 합니다. 이전 스택 오버플로에서 자체적으로 복구하려고 하는 catch 블록에서 수행되는 스택 오버플로가 복구할 수 없으며 catch 블록의 오버플로가 자체적으로 동일한 catch 블록에 의해 처리되는 예외를 트리거함에 따라 프로그램에서 응답을 중지하도록 할 수 있습니다.

블록 내에서와 같이 올바른 위치에서 사용 되는 경우에도 **_resetstkoflw** 실패할 수 있는 상황이 있습니다 **`__except`** . 스택을 해제한 이후에도 스택의 마지막 페이지에 쓰지 않고 **_resetstkoflw** 를 실행할 수 있는 남은 스택 공간이 계속 부족한 경우 **_resetstkoflw** 는 스택의 마지막 페이지를 가드 페이지로 다시 설정하고 실패를 나타내는 0을 반환합니다. 따라서 이 함수의 안전한 사용에는 스택을 사용하는 것이 안전하다는 가정 대신 반환 값을 확인하는 것이 포함되어야 합니다.

구조적 예외 처리는 응용 프로그램이 **/clr** 로 컴파일될 때 **STATUS_STACK_OVERFLOW** 예외를 catch 하지 않습니다 ( [/Clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)참조).

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_resetstkoflw**|\<malloc.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

**라이브러리:** 모든 버전의 [CRT 라이브러리 기능](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

다음 예에서는 **_resetstkoflw** 함수의 권장 사용법을 보여 줍니다.

```C
// crt_resetstkoflw.c
// Launch program with and without arguments to observe
// the difference made by calling _resetstkoflw.

#include <malloc.h>
#include <stdio.h>
#include <windows.h>

void recursive(int recurse)
{
   _alloca(2000);
   if (recurse)
      recursive(recurse);
}

// Filter for the stack overflow exception.
// This function traps the stack overflow exception, but passes
// all other exceptions through.
int stack_overflow_exception_filter(int exception_code)
{
   if (exception_code == EXCEPTION_STACK_OVERFLOW)
   {
       // Do not call _resetstkoflw here, because
       // at this point, the stack is not yet unwound.
       // Instead, signal that the handler (the __except block)
       // is to be executed.
       return EXCEPTION_EXECUTE_HANDLER;
   }
   else
       return EXCEPTION_CONTINUE_SEARCH;
}

int main(int ac)
{
   int i = 0;
   int recurse = 1, result = 0;

   for (i = 0 ; i < 10 ; i++)
   {
      printf("loop #%d\n", i + 1);
      __try
      {
         recursive(recurse);

      }

      __except(stack_overflow_exception_filter(GetExceptionCode()))
      {
         // Here, it is safe to reset the stack.

         if (ac >= 2)
         {
            puts("resetting stack overflow");
            result = _resetstkoflw();
         }
      }

      // Terminate if _resetstkoflw failed (returned 0)
      if (!result)
         return 3;
   }

   return 0;
}
```

프로그램 인수가 없는 샘플 출력:

```Output
loop #1
```

프로그램이 반복을 실행하지 않고 응답하지 않습니다.

프로그램 인수 있음

```Output
loop #1
resetting stack overflow
loop #2
resetting stack overflow
loop #3
resetting stack overflow
loop #4
resetting stack overflow
loop #5
resetting stack overflow
loop #6
resetting stack overflow
loop #7
resetting stack overflow
loop #8
resetting stack overflow
loop #9
resetting stack overflow
loop #10
resetting stack overflow
```

### <a name="description"></a>설명

다음 예제에서는 구조화 된 예외가 c + + 예외로 변환 되는 프로그램의 권장 **_resetstkoflw** 사용을 보여 줍니다.

### <a name="code"></a>코드

```cpp
// crt_resetstkoflw2.cpp
// compile with: /EHa
// _set_se_translator requires the use of /EHa
#include <malloc.h>
#include <stdio.h>
#include <windows.h>
#include <eh.h>

class Exception { };

class StackOverflowException : Exception { };

// Because the overflow is deliberate, disable the warning that
// this function will cause a stack overflow.
#pragma warning (disable: 4717)
void CauseStackOverflow (int i)
{
    // Overflow the stack by allocating a large stack-based array
    // in a recursive function.
    int a[10000];
    printf("%d ", i);
    CauseStackOverflow (i + 1);
}

void __cdecl SEHTranslator (unsigned int code, _EXCEPTION_POINTERS*)
{
    // For stack overflow exceptions, throw our own C++
    // exception object.
    // For all other exceptions, throw a generic exception object.
    // Use minimal stack space in this function.
    // Do not call _resetstkoflw in this function.

    if (code == EXCEPTION_STACK_OVERFLOW)
        throw StackOverflowException ( );
    else
        throw Exception( );
}

int main ( )
{
    bool stack_reset = false;
    bool result = false;

    // Set up a function to handle all structured exceptions,
    // including stack overflow exceptions.
    _set_se_translator (SEHTranslator);

    try
    {
        CauseStackOverflow (0);
    }
    catch (StackOverflowException except)
    {
        // Use minimal stack space here.
        // Do not call _resetstkoflw here.
        printf("\nStack overflow!\n");
        stack_reset = true;
    }
    catch (Exception except)
    {
        // Do not call _resetstkoflw here.
        printf("\nUnknown Exception!\n");
    }
    if (stack_reset)
    {
        result = _resetstkoflw();
        // If stack reset failed, terminate the application.
        if (result == 0)
            exit(1);
    }

    void* pv = _alloca(100000);
    printf("Recovered from stack overflow and allocated 100,000 bytes"
           " using _alloca.");

    return 0;
}
```

```Output
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
Stack overflow!
Recovered from stack overflow and allocated 100,000 bytes using _alloca.
```

## <a name="see-also"></a>참조

[_alloca](alloca.md)<br/>
