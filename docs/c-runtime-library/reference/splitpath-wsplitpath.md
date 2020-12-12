---
description: '자세히 알아보기: _splitpath, _wsplitpath'
title: _splitpath, _wsplitpath
ms.date: 4/2/2020
api_name:
- _wsplitpath
- _splitpath
- _o__splitpath
- _o__wsplitpath
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wsplitpath
- _splitpath
- splitpath
- _wsplitpath
- _tsplitpath
helpviewer_keywords:
- _splitpath function
- pathnames
- wsplitpath function
- splitpath function
- _wsplitpath function
- tsplitpath function
- path names
- _tsplitpath function
ms.assetid: 32bd76b5-1385-4ee8-a64c-abcb541cd2e4
ms.openlocfilehash: d270cf15c00c42f350dafe0cd45dddbb2f6594c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292314"
---
# <a name="_splitpath-_wsplitpath"></a>_splitpath, _wsplitpath

경로 이름을 구성 요소로 분해합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
void _splitpath(
   const char *path,
   char *drive,
   char *dir,
   char *fname,
   char *ext
);
void _wsplitpath(
   const wchar_t *path,
   wchar_t *drive,
   wchar_t *dir,
   wchar_t *fname,
   wchar_t *ext
);
```

### <a name="parameters"></a>매개 변수

*path*<br/>
전체 경로입니다.

*드라이브나*<br/>
드라이브 문자를 입력 한 다음 콜론 (**:**)을 입력 합니다. 드라이브 문자가 필요 하지 않은 경우이 매개 변수에 **NULL** 을 전달할 수 있습니다.

*dir*<br/>
후행 슬래시를 포함한 디렉터리 경로입니다. 슬래시 ( **/** ), 백슬래시 ( **\\** ) 또는 둘 다를 사용할 수 있습니다. 디렉터리 경로가 필요 하지 않은 경우이 매개 변수에 **NULL** 을 전달할 수 있습니다.

*fname*<br/>
기본 파일 이름(확장명 없음)입니다. 파일 이름이 필요 하지 않은 경우이 매개 변수에 **NULL** 을 전달할 수 있습니다.

*확장*<br/>
파일 이름 확장명으로, 선행 마침표 (**.**)를 포함 합니다. 파일 이름 확장명이 필요 하지 않은 경우이 매개 변수에 **NULL** 을 전달할 수 있습니다.

## <a name="remarks"></a>설명

**_Splitpath** 함수는 경로를 4 개의 구성 요소로 나눕니다. **_splitpath** 는 멀티 바이트 문자열 인수를 자동으로 적절 하 게 처리 하 여 현재 사용 중인 멀티 바이트 코드 페이지에 따라 멀티 바이트 문자 시퀀스를 인식 합니다. **_wsplitpath** 은 **_splitpath** 의 와이드 문자 버전입니다. **_wsplitpath** 인수는 와이드 문자 문자열입니다. 그 외의 경우에는 이들 함수가 동일하게 작동합니다.

**보안 정보** 이러한 함수는 버퍼 오버런 문제로 인해 발생하는 잠재적인 위협을 일으킵니다. 버퍼 오버런 문제는 자주 사용되는 시스템 공격 방법으로, 불필요한 권한 상승을 초래합니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [_splitpath_s, _wsplitpath_s을](splitpath-s-wsplitpath-s.md)참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

전체 경로의 각 구성 요소는 별도의 버퍼에 저장 됩니다. 매니페스트 상수 **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME** 및 **_MAX_EXT** (stdlib.h에 정의 되어 있습니다. H) 각 파일 구성 요소의 최대 크기를 지정 합니다. 해당 매니페스트 상수보다 큰 파일 구성 요소가 있으면 힙이 손상됩니다.

버퍼 오버런 가능성을 방지하려면 각 버퍼가 해당하는 매니페스트 상수만큼 커야 합니다.

다음 표에는 매니페스트 상수의 값이 나와 있습니다.

|Name|값|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

전체 경로에 구성 요소 (예: 파일 이름)가 포함 되어 있지 않으면 **_splitpath** 는 해당 버퍼에 빈 문자열을 할당 합니다.

필요 하지 않은 *경로* 이외의 매개 변수에 대 한 **_splitpath** 에 **NULL** 을 전달할 수 있습니다.

*Path* 가 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 는 **EINVAL** 로 설정 되 고 함수는 **EINVAL** 를 반환 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<stdlib.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[_makepath](makepath-wmakepath.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
