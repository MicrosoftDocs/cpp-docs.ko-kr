---
description: '자세히 알아보기: _findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64'
title: _findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64
ms.date: 4/2/2020
api_name:
- _findfirst
- _wfindfirst
- _findfirst32
- _wfindfirst32
- _findfirst32i64
- _wfindfirst32i64
- _findfirst64
- _wfindfirst64
- _findfirst64i32
- _wfindfirst64i32
- _findfirsti64
- _wfindfirsti64
- _o__findfirst32
- _o__findfirst32i64
- _o__findfirst64
- _o__findfirst64i32
- _o__wfindfirst32
- _o__wfindfirst32i64
- _o__wfindfirst64
- _o__wfindfirst64i32
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
- findfirst32i64
- wfindfirst32i64
- tfindfirst64
- _findfirst64i32
- _wfindfirst32i64
- _wfindfirsti64
- wfindfirst
- _tfindfirsti64
- findfirst32
- _tfindfirst32
- _findfirsti64
- findfirst
- wfindfirst64
- wfindfirst32
- tfindfirst32
- _wfindfirst64i32
- findfirst64i32
- tfindfirst64i32
- _wfindfirst
- findfirsti64
- _findfirst32i64
- wfindfirst64i32
- _wfindfirst32
- _findfirst32
- _tfindfirst32i64
- tfindfirst
- _tfindfirst64i32
- findfirst64
- _tfindfirst
- _findfirst64
- _tfindfirst64
- tfindfirst32i64
- _findfirst
- _wfindfirst64
helpviewer_keywords:
- _tfindfirst64 function
- _wfindfirst64i32 function
- _wfindfirst32i64 function
- wfindfirst32 function
- _findfirst function
- wfindfirst64 function
- _wfindfirst function
- _findfirst64i32 function
- wfindfirst function
- _findfirst64 function
- tfindfirst32 function
- _tfindfirst64i32 function
- findfirst function
- findfirst32i64 function
- tfindfirst64 function
- _tfindfirst32 function
- tfindfirst32i64 function
- tfindfirst64i32 function
- _wfindfirsti64 function
- _findfirst32i64 function
- findfirst32 function
- findfirsti64 function
- findfirst64i32 function
- tfindfirsti64 function
- tfindfirst function
- _wfindfirst32 function
- wfindfirsti64 function
- _tfindfirsti64 function
- _tfindfirst function
- _tfindfirst32i64 function
- findfirst64 function
- _findfirst32 function
- _findfirsti64 function
- wfindfirst32i64 function
- wfindfirst64i32 function
- _wfindfirst64 function
ms.assetid: 9bb46d1a-b946-47de-845a-a0b109a33ead
ms.openlocfilehash: dce0c283a6177940019f1d358bd6cfa500c04306
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263142"
---
# <a name="_findfirst-_findfirst32-_findfirst32i64-_findfirst64-_findfirst64i32-_findfirsti64-_wfindfirst-_wfindfirst32-_wfindfirst32i64-_wfindfirst64-_wfindfirst64i32-_wfindfirsti64"></a>_findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64

*Filespec* 인수에 지정 된 파일과 일치 하는 파일 이름의 첫 번째 인스턴스에 대 한 정보를 제공 합니다.

## <a name="syntax"></a>구문

```C
intptr_t _findfirst(
   const char *filespec,
   struct _finddata_t *fileinfo
);
intptr_t _findfirst32(
   const char *filespec,
   struct _finddata32_t *fileinfo
);
intptr_t _findfirst64(
   const char *filespec,
   struct _finddata64_t *fileinfo
);
intptr_t _findfirsti64(
   const char *filespec,
   struct _finddatai64_t *fileinfo
);
intptr_t _findfirst32i64(
   const char *filespec,
   struct _finddata32i64_t *fileinfo
);
intptr_t _findfirst64i32(
   const char *filespec,
   struct _finddata64i32_t *fileinfo
);
intptr_t _wfindfirst(
   const wchar_t *filespec,
   struct _wfinddata_t *fileinfo
);
intptr_t _wfindfirst32(
   const wchar_t *filespec,
   struct _wfinddata32_t *fileinfo
);
intptr_t _wfindfirst64(
   const wchar_t *filespec,
   struct _wfinddata64_t *fileinfo
);
intptr_t _wfindfirsti64(
   const wchar_t *filespec,
   struct _wfinddatai64_t *fileinfo
);
intptr_t _wfindfirst32i64(
   const wchar_t *filespec,
   struct _wfinddata32i64_t *fileinfo
);
intptr_t _wfindfirst64i32(
   const wchar_t *filespec,
   struct _wfinddata64i32_t *fileinfo
);
```

### <a name="parameters"></a>매개 변수

*filespec*<br/>
대상 파일 사양입니다(와일드카드 문자를 포함할 수 있음).

*fileinfo*<br/>
파일 정보 버퍼입니다.

## <a name="return-value"></a>반환 값

성공 하면 **_findfirst** 는 [_findnext](findnext-functions.md) 에 대 한 후속 호출에서 사용할 수 있는 파일 또는 파일 그룹을 식별 하는 고유한 검색 핸들을 반환 *하 고* [_findclose](findclose.md)합니다. 그렇지 않으면 **_findfirst** -1을 반환 하 고 **errno** 을 다음 값 중 하나로 설정 합니다.

| errno 값 | 조건 |
|-|-|
| **EINVAL** | 매개 변수가 잘못 되었습니다. *filespec* 또는 *fileinfo* 가 **NULL** 입니다. 또는 운영 체제에서 예기치 않은 오류를 반환했습니다. |
| **ENOENT (** | 일치시킬 수 없는 파일 사양입니다. |
| **ENOMEM** | 메모리가 부족합니다. |
| **EINVAL** | 파일 이름 사양이 잘못 되었거나 지정 된 파일 이름이 **MAX_PATH** 보다 큽니다. |

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

잘못된 매개 변수가 전달되면 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)의 설명대로 잘못된 매개 변수 처리기를 호출합니다.

## <a name="remarks"></a>설명

**_Findfirst** 또는 [_findnext](findnext-functions.md) 함수 (또는 모든 변형)를 완료 한 후에는 [_findclose](findclose.md) 를 호출 해야 합니다. 그러면 애플리케이션에서 이러한 함수에 사용된 리소스가 해제됩니다.

**W** 접두사가 있는 이러한 함수의 변형은 와이드 문자 버전입니다. 그렇지 않으면 해당 하는 싱글바이트 함수와 동일 합니다.

이러한 함수의 변형은 32비트 또는 64비트 시간 형식과 32비트 또는 64비트 파일 크기를 지원합니다. 첫 번째 숫자 접미사 (**32** 또는 **64**)는 시간 형식의 크기를 나타냅니다. 두 번째 접미사는 **i32** 또는 **i64** 이 고, 파일 크기가 32 비트 또는 64 비트 정수로 표시 되는지 여부를 나타냅니다. 어떤 버전이 32비트 및 64비트 시간 형식과 파일 크기를 지원하는지에 대한 자세한 내용은 다음 표를 참조하세요. **I32** 또는 **i64** 접미사는 시간 형식의 크기와 같으면 생략 됩니다. 따라서 **_findfirst64** 는 64 비트 파일 길이를 지원 하 고 **_findfirst32** 32 비트 파일 길이만 지원 합니다.

이러한 함수는 *fileinfo* 매개 변수에 대해 다양 한 형식의 **_finddata_t** 구조를 사용 합니다. 구조체에 대한 자세한 내용은 [파일 이름 검색 함수](../../c-runtime-library/filename-search-functions.md)를 참조하세요.

64비트 시간 형식을 사용하는 변형을 통해 3000년 12월 31일 23:59:59(UTC)까지 파일 생성 날짜를 표현할 수 있습니다. 32비트 시간 형식을 사용하는 변형은 2038년 1월 18일 23:59:59(UTC)까지의 날짜만 나타냅니다. 1970년 1월 1일 자정은 이러한 모든 함수에 대한 날짜 범위의 하한입니다.

시간 크기를 명시적으로 지정 하는 버전을 사용 해야 하는 특별 한 이유가 없다면 **_findfirst** 또는 **_wfindfirst** 를 사용 하 고, 3gb 보다 큰 파일 크기를 지원 해야 하는 경우에는 **_findfirsti64** 또는 **_wfindfirsti64** 를 사용 합니다. 이러한 함수는 모두 64비트 시간 형식을 사용합니다. 이전 버전에서는 이러한 함수에서 32비트 시간 형식을 사용했습니다. 응용 프로그램에 대 한 주요 변경 사항이 면 이전 동작으로 되돌리는 **_USE_32BIT_TIME_T** 를 정의할 수 있습니다. **_USE_32BIT_TIME_T** 정의 된 경우 **_findfirst**, **_finfirsti64** 및 해당 유니코드 버전은 32 비트 시간을 사용 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="time-type-and-file-length-type-variations-of-_findfirst"></a>_findfirst의 시간 형식 및 파일 길이 형식 변형

|함수|정의 **_USE_32BIT_TIME_T** ?|시간 형식|파일 길이 형식|
|---------------|----------------------------------|---------------|----------------------|
|**_findfirst**, **_wfindfirst**|정의되지 않음|64비트|32비트|
|**_findfirst**, **_wfindfirst**|정의됨|32비트|32비트|
|**_findfirst32**, **_wfindfirst32**|매크로 정의의 영향을 받지 않음|32비트|32비트|
|**_findfirst64**, **_wfindfirst64**|매크로 정의의 영향을 받지 않음|64비트|64비트|
|**_findfirsti64**, **_wfindfirsti64**|정의되지 않음|64비트|64비트|
|**_findfirsti64**, **_wfindfirsti64**|정의됨|32비트|64비트|
|**_findfirst32i64**, **_wfindfirst32i64**|매크로 정의의 영향을 받지 않음|32비트|64비트|
|**_findfirst64i32**, **_wfindfirst64i32**|매크로 정의의 영향을 받지 않음|64비트|32비트|

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindfirst**|**_findfirst**|**_findfirst**|**_wfindfirst**|
|**_tfindfirst32**|**_findfirst32**|**_findfirst32**|**_wfindfirst32**|
|**_tfindfirst64**|**_findfirst64**|**_findfirst64**|**_wfindfirst64**|
|**_tfindfirsti64**|**_findfirsti64**|**_findfirsti64**|**_wfindfirsti64**|
|**_tfindfirst32i64**|**_findfirst32i64**|**_findfirst32i64**|**_wfindfirst32i64**|
|**_tfindfirst64i32**|**_findfirst64i32**|**_findfirst64i32**|**_wfindfirst64i32**|

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**_findfirst**|\<io.h>|
|**_findfirst32**|\<io.h>|
|**_findfirst64**|\<io.h>|
|**_findfirsti64**|\<io.h>|
|**_findfirst32i64**|\<io.h>|
|**_findfirst64i32**|\<io.h>|
|**_wfindfirst**|\<io.h> 또는 \<wchar.h>|
|**_wfindfirst32**|\<io.h> 또는 \<wchar.h>|
|**_wfindfirst64**|\<io.h> 또는 \<wchar.h>|
|**_wfindfirsti64**|\<io.h> 또는 \<wchar.h>|
|**_wfindfirst32i64**|\<io.h> 또는 \<wchar.h>|
|**_wfindfirst64i32**|\<io.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[시스템 호출](../../c-runtime-library/system-calls.md)<br/>
[파일 이름 검색 함수](../../c-runtime-library/filename-search-functions.md)<br/>
