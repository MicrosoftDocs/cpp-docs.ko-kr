---
title: assert Macro, _assert, _wassert
description: Assert 매크로 및 함수가 C 런타임에 미치는 영향입니다.
ms.date: 11/04/2016
api_name:
- assert
- _assert
- _wassert
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- assert
- _assert
- _wassert
- assert/_wassert
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
ms.openlocfilehash: 071424f2201ceda43438fe1056801811fe444a01
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609079"
---
# <a name="assert-macro-_assert-_wassert"></a>assert Macro, _assert, _wassert

식을 계산 하 고 결과가 이면 **`false`** 진단 메시지를 출력 하 고 프로그램을 중단 합니다.

## <a name="syntax"></a>구문

```C
assert(
   expression
);
void _assert(
   char const* message,
   char const* filename,
   unsigned line
);
void _wassert(
   wchar_t const* message,
   wchar_t const* filename,
   unsigned line
);
```

### <a name="parameters"></a>매개 변수

*expression*<br/>
0이 아닌 값 ( **`true`** ) 또는 0 ()으로 계산 되는 스칼라 식 (포인터 식 포함) **`false`** 입니다.

*message*<br/>
표시할 메시지입니다.

*filename*<br/>
어설션이 실패한 소스 파일의 이름입니다.

*line*<br/>
실패한 어설션의 소스 파일에 있는 줄 번호입니다.

## <a name="remarks"></a>설명

일반적으로 `assert` 매크로는 프로그램을 개발하는 동안 논리 오류를 식별하는 데 사용됩니다. 프로그램이 제대로 작동 하지 않는 경우에만 계산 되도록 *식* 인수를 구현 하 여 예기치 않은 조건이 발생할 때 프로그램 실행을 중지 하는 데 사용 **`false`** 합니다. **Ndebug**매크로를 정의 하 여 컴파일 타임에 어설션 검사를 해제할 수 있습니다. &lt;assert.h&gt;를 포함하기 전에 `assert` 명령줄 옵션을 사용하여 소스 파일을 수정하지 않고 **assert** 매크로를 끌 수 있습니다. `assert` `#define NDEBUG` 을 포함 하기 전에 지시문을 사용 하 여 소스 코드에서 매크로를 해제할 수 있습니다 \<assert.h> .

`assert` *식이* **`false`** (0)로 계산 되 고 [`abort`](abort.md) 를 호출 하 여 프로그램 실행을 중지 하면 매크로가 진단 메시지를 출력 합니다. *식이* **`true`** (0이 아닌 값) 이면 아무 작업도 수행 되지 않습니다. 진단 메시지에는 실패한 식, 소스 파일의 이름 및 어설션이 실패한 줄의 번호가 포함됩니다.

진단 메시지는 와이드 문자 ()로 인쇄 됩니다 `wchar_t` . 따라서 식에 유니코드 문자가 있어도 예상 대로 작동 합니다.

진단 메시지의 대상은 루틴을 호출한 애플리케이션의 형식에 따라 달라집니다. 콘솔 응용 프로그램은 **stderr**을 통해 메시지를 받습니다. Windows 기반 응용 프로그램에서는 `assert` Windows [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) 함수를 호출 하 여 **중단**, **다시 시도**및 **무시**라는 세 가지 단추가 포함 된 메시지를 표시 하는 메시지 상자를 만듭니다. 사용자가 **중단**을 클릭하면 프로그램이 즉시 중단됩니다. 사용자가 **다시 시도**를 클릭하면 디버거가 호출되고 JIT(Just-In-Time) 디버깅을 사용하는 경우 사용자가 프로그램을 디버깅할 수 있습니다. 사용자가 **무시**를 클릭 하면 프로그램은 정상적으로 실행 됩니다. 오류 조건이 있을 때 **무시** 를 클릭 하면 호출 코드의 사전 조건이 충족 되지 않으므로 정의 되지 않은 동작이 발생할 수 있습니다.

앱 형식에 관계 없이 기본 출력 동작을 재정의 하려면를 호출 [`_set_error_mode`](set-error-mode.md) 하 여 출력-stderr 및 표시 대화 상자 동작 사이를 선택 합니다.

는 `assert` 메시지를 표시 한 후 [`abort`](abort.md)  **중단**, **다시 시도**및 **무시** 단추가 포함 된 대화 상자를 표시 하는를 호출 합니다. [`abort`](abort.md) 프로그램을 종료 하므로 **다시 시도** 및 **무시** 단추는 호출 후 프로그램 실행을 다시 시작 하지 않습니다 `assert` . `assert`대화 상자를 표시 하면 [`abort`](abort.md) 대화 상자가 표시 되지 않습니다. [`abort`](abort.md)대화 상자가 표시 되는 경우에만에서 `assert` 해당 출력을 stderr로 보낼 수 있습니다.

위의 동작의 결과로, `assert` 디버그 모드에서 호출 후에 대화 상자가 항상 표시 됩니다. 각 단추의 동작은 아래 표에 나와 있습니다.

|오류 모드|Stderr로 출력 (콘솔/_OUT_TO_STDERR)|표시 대화 상자 (Windows/_OUT_TO_MSGBOX)|
|----------|----------------|------------------|
|중단|종료 코드 3으로 즉시 종료|종료 코드 3으로 즉시 종료|
|재시도|에서 디버거를 중단 합니다. `abort`|에서 디버거를 중단 합니다. `assert`|
|무시|종료 완료 `abort`|Assert가 발생 하지 않은 것 처럼 프로그램을 계속 합니다 (호출 코드의 사전 조건이 충족 되지 않아 정의 되지 않은 동작이 발생할 수 있음).|

CRT 디버깅에 대한 자세한 내용은 [CRT 디버깅 기술](/visualstudio/debugger/crt-debugging-techniques)을 참조하세요.

`_assert` 및 `_wassert` 함수는 내부 CRT 함수입니다. 이를 통해 어설션을 지원하기 위해 개체 파일에 필요한 코드를 최소화할 수 있습니다. 이러한 함수는 직접 호출 하지 않는 것이 좋습니다.

`assert` **Ndebug** 가 정의 되지 않은 경우 매크로는 C 런타임 라이브러리의 릴리스 및 디버그 버전에서 모두 사용할 수 있습니다. **Ndebug** 가 정의 되 면 매크로를 사용할 수 있지만 인수를 계산 하지 않고 아무런 영향을 주지 않습니다. 사용 하도록 설정 되 면 `assert` 매크로가 `_wassert` 구현을 위해를 호출 합니다. 기타 어셜션 매크로 [_ASSERT](assert-asserte-assert-expr-macros.md), [_ASSERTE](assert-asserte-assert-expr-macros.md) 및 [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md)도 사용할 수 있지만 어설션 매크로는 [_DEBUG](../../c-runtime-library/debug.md) 매크로가 정의되고 어설션 매크로가 C 런타임 라이브러리의 디버그 버전과 연결된 코드에 있을 때만 어설션 매크로에 전달되는 식을 계산합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|`assert`, `_wassert`|\<assert.h>|

`_assert`헤더 파일에서는 함수 시그니처를 사용할 수 없습니다. 함수 시그니처는 `_wassert` **ndebug** 매크로가 정의 되지 않은 경우에만 사용할 수 있습니다.

## <a name="example"></a>예제

이 프로그램에서 **analyze_string** 함수는 매크로를 사용 하 여 `assert` 문자열 및 길이와 관련 된 여러 조건을 테스트 합니다. 조건 중 하나라도 실패하면 프로그램이 실패의 원인을 나타내는 메시지를 출력합니다.

```C
// crt_assert.c
// compile by using: cl /W4 crt_assert.c
#include <stdio.h>
#include <assert.h>
#include <string.h>

void analyze_string( char *string );   // Prototype

int main( void )
{
   char  test1[] = "abc", *test2 = NULL, test3[] = "";

   printf ( "Analyzing string '%s'\n", test1 ); fflush( stdout );
   analyze_string( test1 );
   printf ( "Analyzing string '%s'\n", test2 ); fflush( stdout );
   analyze_string( test2 );
   printf ( "Analyzing string '%s'\n", test3 ); fflush( stdout );
   analyze_string( test3 );
}

// Tests a string to see if it is NULL,
// empty, or longer than 0 characters.
void analyze_string( char * string )
{
   assert( string != NULL );        // Cannot be NULL
   assert( *string != '\0' );       // Cannot be empty
   assert( strlen( string ) > 2 );  // Length must exceed 2
}
```

프로그램에서 다음 출력이 생성됩니다.

```Output
Analyzing string 'abc'
Analyzing string '(null)'
Assertion failed: string != NULL, file crt_assert.c, line 25
```

어설션 실패 후에는 운영 체제 및 런타임 라이브러리의 버전에 따라 다음과 비슷한 메시지가 표시 될 수 있습니다.

```Output
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.
```

디버거가 설치되어 있으면 **디버그** 단추를 선택하여 디버거를 시작하거나, **프로그램을 닫아** 종료합니다.

## <a name="see-also"></a>참고 항목

[오류 처리](../../c-runtime-library/error-handling-crt.md)<br/>
[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)<br/>
[중단이](abort.md)<br/>
[올리려면](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR 매크로](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
