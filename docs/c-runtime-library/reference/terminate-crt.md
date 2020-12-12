---
description: '자세한 정보: 종료 (CRT)'
title: terminate(CRT)
ms.date: 4/2/2020
api_name:
- terminate
- _o_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- terminate
helpviewer_keywords:
- terminate function
- exception handling, termination
ms.assetid: 90e67402-08e9-4b2a-962c-66a8afd3ccb4
ms.openlocfilehash: 8370c1f1aff54b5286ad4472b053275e3468a8d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326170"
---
# <a name="terminate-crt"></a>terminate(CRT)

**Set_terminate** 를 사용 하 여 [abort](abort.md) 또는 지정한 함수를 호출 합니다.

## <a name="syntax"></a>구문

```C
void terminate( void );
```

## <a name="remarks"></a>설명

**Terminate** 함수는 c + + 예외 처리와 함께 사용 되며 다음과 같은 경우에 호출 됩니다.

- throw된 C++ 예외에 대해 일치하는 catch 처리기를 찾을 수 없는 경우

- 스택 해제 중에 소멸자 함수가 예외를 throw한 경우

- 스택이 예외를 throw한 후에 손상된 경우

**종료** 호출은 기본적으로 [중단](abort.md) 됩니다. 사용자 고유의 종료 함수를 작성 하 고 함수 이름을 인수로 사용 하 여 **set_terminate** 를 호출 하 여이 기본값을 변경할 수 있습니다. **terminate** 는 **set_terminate** 에 대 한 인수로 지정 된 마지막 함수를 호출 합니다. 자세한 내용은 [처리되지 않은 C++ 예외](../../cpp/unhandled-cpp-exceptions.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**끝나야**|\<eh.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```cpp
// crt_terminate.cpp
// compile with: /EHsc
#include <eh.h>
#include <process.h>
#include <iostream>
using namespace std;

void term_func();

int main()
{
    int i = 10, j = 0, result;
    set_terminate( term_func );
    try
    {
        if( j == 0 )
            throw "Divide by zero!";
        else
            result = i/j;
    }
    catch( int )
    {
        cout << "Caught some integer exception.\n";
    }
    cout << "This should never print.\n";
}

void term_func()
{
    cout << "term_func() was called by terminate().\n";

    // ... cleanup tasks performed here

    // If this function does not exit, abort is called.

    exit(-1);
}
```

```Output
term_func() was called by terminate().
```

## <a name="see-also"></a>참고 항목

[예외 처리 루틴](../../c-runtime-library/exception-handling-routines.md)<br/>
[중단이](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[없는](unexpected-crt.md)<br/>
