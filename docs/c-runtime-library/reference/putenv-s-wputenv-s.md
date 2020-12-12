---
description: '자세히 알아보기: _putenv_s, _wputenv_s'
title: _putenv_s, _wputenv_s
ms.date: 4/2/2020
api_name:
- _wputenv_s
- _putenv_s
- _o__putenv_s
- _o__wputenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
ms.openlocfilehash: bba9d595d716f3a8e5e9c41326a0258b10e8abf8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246294"
---
# <a name="_putenv_s-_wputenv_s"></a>_putenv_s, _wputenv_s

환경 변수를 생성, 수정 또는 제거합니다. 이러한 버전의 [_putenv, _wputenv](putenv-wputenv.md)에는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 향상된 보안 기능이 포함되어 있습니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
errno_t _putenv_s(
   const char *varname,
   const char *value_string
);
errno_t _wputenv_s(
   const wchar_t *varname,
   const wchar_t *value_string
);
```

### <a name="parameters"></a>매개 변수

*varname*<br/>
환경 변수 이름입니다.

*value_string*<br/>
환경 변수를 설정할 값입니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환하고, 그렇지 않으면 오류 코드를 반환합니다.

### <a name="error-conditions"></a>오류 조건

|*varname*|*value_string*|반환 값|
|------------|-------------|------------------|
|**NULL**|any|**EINVAL**|
|any|**NULL**|**EINVAL**|

오류 조건 중 하나가 발생할 경우 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기를 호출합니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **EINVAL** 를 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

## <a name="remarks"></a>설명

**_Putenv_s** 함수는 새 환경 변수를 추가 하거나 기존 환경 변수의 값을 수정 합니다. 환경 변수는 프로세스가 실행되는 환경을 정의합니다(예: 프로그램에 연결할 라이브러리의 기본 검색 경로). **_wputenv_s** 은 **_putenv_s** 의 와이드 문자 버전입니다. **_wputenv_s** 에 대 한 *envstring* 인수는 와이드 문자 문자열입니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*varname* 은 추가 또는 수정할 환경 변수의 이름이 고 *value_string* 은 변수의 값입니다. *Varname* 이 이미 환경의 일부 이면 해당 값이 *value_string* 로 바뀝니다. 그렇지 않으면 새 *varname* 변수 및 해당 *value_string* 환경에 추가 됩니다. *Value_string* 에 대해 빈 문자열 ("")을 지정 하 여 환경에서 변수를 제거할 수 있습니다.

**_putenv_s** 및 **_wputenv_s** 는 현재 프로세스에 로컬인 환경에만 영향을 줍니다. 명령 수준 환경을 수정 하는 데 사용할 수 없습니다. 이러한 함수는 운영 체제가 프로세스에 대해 만드는 환경 "세그먼트"가 아니라 런타임 라이브러리에 액세스할 수 있는 데이터 구조에서만 작동합니다. 현재 프로세스가 종료되면 환경이 호출 프로세스의 수준(대부분의 경우 운영 체제 수준)으로 되돌아갑니다. 그러나 수정 된 환경은 **_spawn**, **_exec** 또는 **시스템** 에 의해 만들어진 모든 새 프로세스에 전달 될 수 있으며, 이러한 새 프로세스는 **_putenv_s** 및 **_wputenv_s** 에 의해 추가 되는 모든 새 항목을 가져옵니다.

환경 항목을 직접 변경 하지 마십시오. 대신 **_putenv_s** 또는 **_wputenv_s** 를 사용 하 여 변경 합니다. 특히 **_environ []** 전역 배열의 요소를 직접 해제 하면 잘못 된 메모리가 처리 될 수 있습니다.

**getenv** 및 **_putenv_s** 전역 변수 **_environ** 를 사용 하 여 환경 테이블에 액세스 합니다. **_wgetenv** 및 **_wputenv_s** **_wenviron** 를 사용 합니다. **_putenv_s** 및 **_wputenv_s** 은 **_environ** 및 **_wenviron** 값을 변경할 수 있으므로 **main** 에 대 한 *envp* 인수 및 **wmain** 에 대 한 **_wenvp** 인수를 무효화할 수 있습니다. 따라서 **_environ** 또는 **_wenviron** 를 사용 하 여 환경 정보에 액세스 하는 것이 더 안전 합니다. **_Putenv_s** 및 전역 변수에 대 한 **_wputenv_s** 관계에 대 한 자세한 내용은 [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md)를 참조 하세요.

> [!NOTE]
> **_Putenv_s** 및 **_getenv_s** 함수 패밀리는 스레드로부터 안전 하지 않습니다. **_putenv_s** 문자열을 수정 하는 동안 **_getenv_s** 는 문자열 포인터를 반환할 수 있으므로 임의 오류가 발생 합니다. 이러한 함수에 대한 호출은 동기화해야 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

**_Putenv_s** 를 사용 하는 방법을 보여 주는 예제는 [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
