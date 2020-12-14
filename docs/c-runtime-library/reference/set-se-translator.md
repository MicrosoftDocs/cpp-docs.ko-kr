---
description: '다음에 대 한 자세한 정보: _set_se_translator'
title: _set_se_translator
ms.date: 02/21/2018
api_name:
- _set_se_translator
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_se_translator
- set_se_translator
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
ms.openlocfilehash: 5ba0f0816b7876f24dfc010c83711e9ca652edad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211234"
---
# <a name="_set_se_translator"></a>_set_se_translator

Win32 예외 (C 구조적 예외)를 c + + 형식 예외로 변환 하도록 스레드별 콜백 함수를 설정 합니다.

## <a name="syntax"></a>구문

```cpp
_se_translator_function _set_se_translator(
    _se_translator_function seTransFunction
);
```

### <a name="parameters"></a>매개 변수

*seTransFunction*<br/>
작성하는 C 구조적 예외 변환기 함수에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

이전 함수를 나중에 복원할 수 있도록 **_set_se_translator** 에서 등록 한 이전 변환기 함수에 대 한 포인터를 반환 합니다. 이전 함수를 설정 하지 않은 경우 반환 값을 사용 하 여 기본 동작을 복원할 수 있습니다. 이 값은 일 수 있습니다 **`nullptr`** .

## <a name="remarks"></a>설명

**_Set_se_translator** 함수는 Win32 예외 (c 구조적 예외)를 c + + 형식 예외로 처리 하는 방법을 제공 합니다. 각 C 예외가 c + + 처리기에 의해 처리 되도록 허용 하려면 **`catch`** 먼저 특정 클래스 형식의 특성을 c 예외로 지정 하기 위해 사용 하거나 파생 시킬 수 있는 c 예외 래퍼 클래스를 정의 합니다. 이 클래스를 사용하려면 C 예외가 발생할 때마다 내부 예외 처리 메커니즘을 통해 호출되는 사용자 지정 C 예외 변환기 함수를 설치합니다. 변환기 함수 내에서 일치 하는 c + + 처리기에 의해 catch 될 수 있는 모든 형식의 예외를 throw 할 수 있습니다 **`catch`** .

**_Set_se_translator** 사용 하는 경우 [/eha](../../build/reference/eh-exception-handling-model.md) 를 사용 해야 합니다.

사용자 지정 변환 함수를 지정 하려면 변환 함수의 이름을 인수로 사용 하 여 **_set_se_translator** 를 호출 합니다. 작성 하는 변환기 함수는 블록이 있는 스택의 각 함수 호출에 대해 한 번씩 호출 됩니다 **`try`** . 기본 변환기 함수가 없습니다.

변환기 함수는 C++ 형식의 예외만 발생시켜야 합니다. throw 이외에도 어떤 작업을 수행하는 경우(예: 로그 파일에 쓰기) 변환기 함수가 호출되는 횟수가 플랫폼에 따라 다르므로 프로그램이 예상대로 작동하지 않을 수 있습니다.

다중 스레드 환경에서 변환기 함수는 각 스레드에 대해 개별적으로 유지 관리됩니다. 각 새 스레드는 자체 변환기 함수를 설치해야 합니다. 따라서 각 스레드는 자체 변환 처리를 담당합니다. **_set_se_translator** 은 한 스레드에만 적용 됩니다. 다른 DLL은 다른 변환 함수를 설치할 수 있습니다.

작성 하는 *seTransFunction* 함수는 네이티브 컴파일 함수 여야 합니다 (/clr을 사용 하 여 컴파일되지 않음). 부호 없는 정수 및 Win32 **_EXCEPTION_POINTERS** 구조체에 대 한 포인터를 인수로 사용 해야 합니다. 인수는 Win32 API **Getexceptioncode** 및 **getexceptioncode** 함수에 대 한 호출의 반환 값입니다.

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

**_Set_se_translator** 의 경우 CRT에 동적으로 연결 하는 경우에도 영향을 미칩니다. 프로세스의 다른 DLL은 **_set_se_translator** 를 호출 하 고 처리기를 자체 처리기로 대체할 수 있습니다.

관리 코드 (/clr을 사용 하 여 컴파일된 코드) 또는 혼합 네이티브 및 관리 코드에서 **_set_se_translator** 사용 하는 경우 변환기는 네이티브 코드 에서만 생성 된 예외에 영향을 줍니다. 관리 코드에서 생성된 관리 예외(예: `System::Exception`을 발생시키는 경우)는 변환기 함수를 통해 라우팅되지 않습니다. Win32 함수를 사용 하 여 관리 코드에서 발생 하는 예외 또는 0으로 나누기 예외와 같은 시스템 예외에의 한 **RaiseException** 변환기를 통해 라우팅됩니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_set_se_translator**|\<eh.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example-catch-__try-exception-error"></a>예: Catch __try 예외 오류

이 샘플은 호출을 래핑하여 구조화 된 예외 변환기를 설정 하 고 RAII 클래스에서 이전 항목을 복원 `Scoped_SE_Translator` 합니다. 이 클래스를 사용 하 여 범위 고유의 번역기를 단일 선언으로 도입할 수 있습니다. 클래스 소멸자는 컨트롤이 범위를 벗어날 때 원래 변환기를 복원 합니다.

```cpp
// crt_settrans.cpp
// compile with: cl /W4 /EHa crt_settrans.cpp
#include <stdio.h>
#include <windows.h>
#include <eh.h>
#include <exception>

class SE_Exception : public std::exception
{
private:
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
};

void SEFunc()
{
    __try
    {
        printf( "In __try, about to force exception\n" );
        int x = 5;
        int y = 0;
        int *p = &y;
        *p = x / *p;
    }
    __finally
    {
        printf( "In __finally\n" );
    }
}

void trans_func( unsigned int u, EXCEPTION_POINTERS* )
{
    throw SE_Exception( u );
}

int main()
{
    Scoped_SE_Translator scoped_se_translator{ trans_func };
    try
    {
        SEFunc();
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught a __try exception, error %8.8x.\n", e.getSeNumber() );
    }
}
```

```Output
In __try, about to force exception
In __finally
Caught a __try exception, error c0000094.
```

## <a name="example-catch-se_exception-error"></a>예: Catch SE_Exception 오류

**_Set_se_translator** 에서 제공 하는 기능을 관리 코드에서 사용할 수는 없지만 네이티브 코드가를 사용 하 여 표시 되는 한 **/clr** 스위치를 사용 하 여 컴파일하는 경우에도 네이티브 코드에서이 매핑을 사용할 수 있습니다 `#pragma unmanaged` . 매핑될 관리 코드에서 구조적 예외가 throw 되는 경우 예외를 생성 하 고 처리 하는 코드를로 표시 해야 합니다 `#pragma unmanaged` . 다음 코드에서는 가능한 사용법을 보여 줍니다. 자세한 내용은 [Pragma 지시문 및 __Pragma 키워드](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)를 참조하세요.

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <stdio.h>
#include <exception>

int thrower_func( int i ) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class SE_Exception : public std::exception
{
private:
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
};

#pragma unmanaged
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS )
{
    throw SE_Exception( u );
}

void DoTest()
{
    try
    {
        thrower_func( 10 );
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught SE_Exception, error %8.8x\n", e.getSeNumber() );
    }
    catch(...)
    {
        printf( "Caught unexpected SEH exception.\n" );
    }
}
#pragma managed

int main() {
    Scoped_SE_Translator scoped_se_translator{ my_trans_func };

    DoTest();
}
```

```Output
Caught SE_Exception, error c0000094
```

## <a name="see-also"></a>참고 항목

[예외 처리 루틴](../../c-runtime-library/exception-handling-routines.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[끝나야](terminate-crt.md)<br/>
[없는](unexpected-crt.md)<br/>
