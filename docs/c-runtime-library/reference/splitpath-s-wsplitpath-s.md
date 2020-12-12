---
description: '자세히 알아보기: _splitpath_s, _wsplitpath_s'
title: _splitpath_s, _wsplitpath_s
ms.date: 4/2/2020
api_name:
- _wsplitpath_s
- _splitpath_s
- _o__splitpath_s
- _o__wsplitpath_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wsplitpath_s
- splitpath_s
- _splitpath_s
- wsplitpath_s
helpviewer_keywords:
- splitpath_s function
- pathnames
- _splitpath_s function
- _wsplitpath_s function
- path names
- wsplitpath_s function
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
ms.openlocfilehash: f14ea8a31d241abae3a214067cae1e4d34e97861
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292346"
---
# <a name="_splitpath_s-_wsplitpath_s"></a>_splitpath_s, _wsplitpath_s

경로 이름을 구성 요소로 분해합니다. 이러한 함수는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 강화된 보안 기능이 있는 [_splitpath, _wsplitpath](splitpath-wsplitpath.md)의 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t _splitpath_s(
   const char * path,
   char * drive,
   size_t driveNumberOfElements,
   char * dir,
   size_t dirNumberOfElements,
   char * fname,
   size_t nameNumberOfElements,
   char * ext,
   size_t extNumberOfElements
);
errno_t _wsplitpath_s(
   const wchar_t * path,
   wchar_t * drive,
   size_t driveNumberOfElements,
   wchar_t *dir,
   size_t dirNumberOfElements,
   wchar_t * fname,
   size_t nameNumberOfElements,
   wchar_t * ext,
   size_t extNumberOfElements
);
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _splitpath_s(
   const char *path,
   char (&drive)[drivesize],
   char (&dir)[dirsize],
   char (&fname)[fnamesize],
   char (&ext)[extsize]
); // C++ only
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _wsplitpath_s(
   const wchar_t *path,
   wchar_t (&drive)[drivesize],
   wchar_t (&dir)[dirsize],
   wchar_t (&fname)[fnamesize],
   wchar_t (&ext)[extsize]
); // C++ only
```

### <a name="parameters"></a>매개 변수

*path*<br/>
전체 경로입니다.

*드라이브나*<br/>
드라이브 문자를 입력 한 다음 콜론 (**:**)을 입력 합니다. 드라이브 문자가 필요 하지 않은 경우이 매개 변수에 **NULL** 을 전달할 수 있습니다.

*driveNumberOfElements*<br/>
*드라이브* 버퍼의 크기 (싱글바이트 또는 와이드 문자)입니다. *드라이브가* **NULL** 이면이 값은 0 이어야 합니다.

*dir*<br/>
후행 슬래시를 포함한 디렉터리 경로입니다. 슬래시 ( **/** ), 백슬래시 ( **\\** ) 또는 둘 다를 사용할 수 있습니다. 디렉터리 경로가 필요 하지 않은 경우이 매개 변수에 **NULL** 을 전달할 수 있습니다.

*dirNumberOfElements*<br/>
단일 바이트 또는 와이드 문자에 있는 *dir* 버퍼의 크기입니다. *Dir* 이 **NULL** 이면이 값은 0 이어야 합니다.

*fname*<br/>
확장명이 없는 기본 파일 이름입니다. 파일 이름이 필요 하지 않은 경우이 매개 변수에 **NULL** 을 전달할 수 있습니다.

*nameNumberOfElements*<br/>
단일 바이트 또는 와이드 문자에서 *fname* 버퍼의 크기입니다. *Fname* 이 **NULL** 이면이 값은 0 이어야 합니다.

*확장*<br/>
파일 이름 확장명으로, 선행 마침표 (**.**)를 포함 합니다. 파일 이름 확장명이 필요 하지 않은 경우이 매개 변수에 **NULL** 을 전달할 수 있습니다.

*extNumberOfElements*<br/>
단일 바이트 또는 와이드 문자 단위의 *ext* 버퍼 크기입니다. *Ext* 가 **NULL** 이면이 값은 0 이어야 합니다.

## <a name="return-value"></a>반환 값

성공 시 0이고, 실패 시 오류 코드입니다.

### <a name="error-conditions"></a>오류 조건

|조건|반환 값|
|---------------|------------------|
|*경로가* **NULL** 입니다.|**EINVAL**|
|*드라이브가* **NULL** 이 고 *driveNumberOfElements* 가 0이 아닌 경우|**EINVAL**|
|*드라이브가* **NULL** 이 아니고 *driveNumberOfElements* 가 0입니다.|**EINVAL**|
|*dir* 은 **NULL** 이 고, *dirnumberofelements* 는 0이 아닙니다.|**EINVAL**|
|*dir* 이 **NULL** 이 아닌 경우 *dirnumberofelements* 는 0입니다.|**EINVAL**|
|*fname* is **NULL**, *namenumberofelements* 가 0이 아닌 경우|**EINVAL**|
|*fname* 이 **NULL** 이 아닌 경우 *namenumberofelements* 는 0입니다.|**EINVAL**|
|*ext* 가 **NULL**, *extnumberofelements* 가 0이 아닙니다.|**EINVAL**|
|*ext* 가 **NULL** 이 아닌 경우 *extnumberofelements* 는 0입니다.|**EINVAL**|

이러한 조건 중 하나라도 발생하는 경우, [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **errno** 를 **EINVAL** 로 설정 하 고 **EINVAL** 를 반환 합니다.

버퍼가 너무 짧아 결과를 저장할 수 없는 경우 이러한 함수는 모든 버퍼를 빈 문자열로 지우고 **errno** 를 **ERANGE** 로 설정 하 고 **ERANGE** 를 반환 합니다.

## <a name="remarks"></a>설명

**_Splitpath_s** 함수는 경로를 4 개의 구성 요소로 나눕니다. **_splitpath_s** 는 멀티 바이트 문자열 인수를 자동으로 적절 하 게 처리 하 여 현재 사용 중인 멀티 바이트 코드 페이지에 따라 멀티 바이트 문자 시퀀스를 인식 합니다. **_wsplitpath_s** 은 **_splitpath_s** 의 와이드 문자 버전입니다. **_wsplitpath_s** 인수는 와이드 문자 문자열입니다. 그 외의 경우에는 이들 함수가 동일하게 동작합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

전체 경로의 각 구성 요소는 별도의 버퍼에 저장 됩니다. 매니페스트 상수 **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME** 및 **_MAX_EXT** (stdlib.h에 정의 되어 있습니다. H) 각 파일 구성 요소에 허용 되는 최대 크기를 지정 합니다. 해당 매니페스트 상수보다 큰 파일 구성 요소가 있으면 힙이 손상됩니다.

다음 표에는 매니페스트 상수의 값이 나와 있습니다.

|Name|값|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

전체 경로에 구성 요소 (예: 파일 이름)가 포함 되어 있지 않으면 **_splitpath_s** 는 해당 버퍼에 빈 문자열을 할당 합니다.

C++에서는 템플릿 오버로드를 통해 이러한 함수를 사용하는 것이 더욱 간단해집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으므로 크기 인수를 지정할 필요가 없습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

이러한 함수의 디버그 라이브러리 버전은 먼저 0xFE를 사용 하 여 버퍼를 채웁니다. 이 동작을 사용하지 않으려면 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)를 사용하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_splitpath_s**|\<stdlib.h>|
|**_wsplitpath_s**|\<stdlib.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
