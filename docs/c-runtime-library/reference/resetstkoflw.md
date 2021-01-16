---
description: '다음에 대 한 자세한 정보: _resetstkoflw'
title: _resetstkoflw
ms.date: 1/14/2021
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
- api-ms-win-crt-runtime-l1-1-0.dll
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
ms.openlocfilehash: 092eea34de10ff77a31b5be35fa84dc1eb887328
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98242971"
---
# `_resetstkoflw`

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

**`_resetstkoflw`** 함수는 스택 오버플로 상태에서 복구 하므로 심각한 예외 오류로 인해 프로그램이 실패 하는 대신 계속할 수 있습니다. 함수를 **`_resetstkoflw`** 호출 하지 않으면 이전 예외 다음에 가드 페이지가 없습니다. 다음 번에 스택 오버플로가 발생 하는 경우 예외가 전혀 발생 하지 않으며 프로세스가 경고 없이 종료 됩니다.

응용 프로그램의 스레드에서 예외가 발생 하는 경우 **`EXCEPTION_STACK_OVERFLOW`** 스레드의 스택이 손상 된 상태로 남아 있습니다. 이는 **`EXCEPTION_ACCESS_VIOLATION`** **`EXCEPTION_INT_DIVIDE_BY_ZERO`** 스택이 손상 되지 않은 또는와 같은 다른 예외와는 대조적입니다. 프로그램이 처음 로드될 때 스택은 임의로 작은 값으로 설정됩니다. 그런 다음 스택은 스레드의 요구 사항을 충족하도록 요구에 맞게 증가합니다. 이는 PAGE_GUARD가 있는 페이지를 현재 스택의 끝에 배치하여 구현됩니다. 자세한 내용은 [가드 페이지 만들기](/windows/win32/Memory/creating-guard-pages)를 참조하세요.

코드로 인해 스택 포인터가 이 페이지의 주소를 가리키는 경우 예외가 발생하고 시스템에서 다음 세 가지 작업이 수행됩니다.

- 스레드에서 데이터를 읽고 메모리에 쓸 수 있도록 가드 페이지의 PAGE_GUARD 보호를 제거합니다.

- 마지막 페이지에서 한 페이지 아래에 위치한 새 가드 페이지를 할당합니다.

- 예외를 발생시킨 명령을 다시 실행합니다.

이러한 방식으로 시스템은 자동으로 스레드에 대한 스택의 크기를 늘릴 수 있습니다. 프로세스의 각 스레드는 최대 스택 크기를 가집니다. 스택 크기는 컴파일 시간에 [ `/STACK` (스택 할당)](../../build/reference/stack-stack-allocations.md)또는 [`STACKSIZE`](../../build/reference/stacksize.md) `.def` 프로젝트에 대 한 파일의 문에 의해 설정 됩니다.

이 최대 스택 크기를 초과하면 시스템에서 다음 세 가지 작업을 수행합니다.

- 앞에서 설명한 대로 가드 페이지에 대한 PAGE_GUARD 보호를 제거합니다.

- 새 가드 페이지를 마지막 가드 페이지 아래에 할당하려고 합니다. 그러나 최대 스택 크기를 초과했기 때문에 이러한 작업이 실패합니다.

- 스레드가 예외 블록에서 처리할 수 있도록 예외를 발생시킵니다.

이 시점에서 스택은 더 이상 가드 페이지를 포함 하지 않습니다. 다음에 프로그램이 가드 페이지가 있어야 하는 끝 부분까지 계속 스택을 증가시킬 때 프로그램은 스택의 끝을 벗어나 쓰며 액세스 위반을 발생시킵니다.

**`_resetstkoflw`** 스택 오버플로 예외가 발생 한 후 복구가 수행 될 때마다 가드 페이지를 복원 하려면를 호출 합니다. 이 함수는 블록의 주 본문 내부 또는 블록 외부에서 호출할 수 있습니다 **`__except`** **`__except`** . 그러나 사용할 때 몇 가지 제한 사항이 있습니다. **`_resetstkoflw`** 에서 호출 해서는 안 됩니다.

- 필터 식

- 필터 함수

- 필터 함수에서 호출한 함수

- **`catch`** 블록입니다.

- **`__finally`** 블록입니다.

이러한 지점에서 스택이 아직 충분히 해제 되지 않았습니다.

스택 오버플로 예외는 c + + 예외가 아닌 구조적 예외로 생성 되므로 **`_resetstkoflw`** 일반 **`catch`** 블록에서 스택 오버플로 예외를 catch 하지 않기 때문에 유용 하지 않습니다. 그러나 [`_set_se_translator`](set-se-translator.md) 를 사용 하 여 c + + 예외를 throw 하는 구조적 예외 변환기를 구현 하는 경우 (두 번째 예제) 스택 오버플로 예외는 c + + catch 블록에 의해 처리 될 수 있는 c + + 예외를 발생 시킵니다.

**`_resetstkoflw`** 구조적 예외 변환기 함수에 의해 throw 된 예외 로부터 도달한 c + + catch 블록에서를 호출 하는 것은 안전 하지 않습니다. 이 경우 catch 블록 전에 소멸 가능한 개체에 대해 소멸자가 호출 된 경우에도 스택 공간은 해제 되지 않고 스택 포인터는 catch 블록 외부에서 다시 설정 되지 않습니다. 스택 공간이 해제 되 고 스택 포인터가 다시 설정 될 때까지이 함수를 호출 하면 안 됩니다. 따라서 catch 블록을 종료한 후에만 이 함수를 호출해야 합니다. 이전 스택 오버플로를 복구 하려고 하는 catch 블록에서 발생 하는 스택 오버플로가 복구할 수 없으며 catch 블록의 오버플로가 동일한 catch 블록에 의해 처리 되는 예외를 트리거하기 때문에 프로그램의 응답을 중지 시킬 수 있으므로 가능한 한 적은 스택 공간을 catch 블록에 사용 해야 합니다.

**`_resetstkoflw`** 블록 내에서와 같이 올바른 위치에서 사용 되는 경우에도가 실패할 수 있는 상황이 있습니다 **`__except`** . 스택을 해제 한 후에도 스택의 마지막 페이지에 쓰지 않고 실행 하기에 남은 스택 공간이 충분 하지 않은 경우 **`_resetstkoflw`** 는 **`_resetstkoflw`** 스택의 마지막 페이지를 가드 페이지로 다시 설정 하 고 실패를 나타내는 0을 반환 합니다. 이 함수의 안전한 사용에는 스택을 사용 해도 안전 하다 고 가정 하는 대신 반환 값을 확인 하는 것이 포함 되어야 합니다.

구조적 예외 처리는 **`STATUS_STACK_OVERFLOW`** 응용 프로그램이로 컴파일될 때 예외를 catch 하지 않습니다 **`/clr`** ( [ `/clr ` (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)참조).

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**`_resetstkoflw`**|\<malloc.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

**라이브러리:** 모든 버전의 [CRT 라이브러리 기능](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예

다음 예에서는 권장 되는 함수 사용법을 보여 줍니다 **`_resetstkoflw`** .

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
       // at this point, the stack isn't yet unwound.
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

### <a name="description"></a>Description

다음 예제에서는 **`_resetstkoflw`** 구조화 된 예외가 c + + 예외로 변환 되는 프로그램에서의 권장 사용 방법을 보여 줍니다.

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

[`_alloca`](alloca.md)<br/>
