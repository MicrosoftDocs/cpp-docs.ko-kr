---
description: '자세히 알아보기: _findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64'
title: _findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64
ms.date: 4/2/2020
api_name:
- _findnext
- _findnext32
- _findnext32i64
- _findnext64
- _findnext64i32
- _findnexti64
- _wfindnext
- _wfindnext32
- _wfindnext32i64
- _wfindnext64
- _wfindnext64i32
- _wfindnexti64
- _o__findnext32
- _o__findnext32i64
- _o__findnext64
- _o__findnext64i32
- _o__wfindnext32
- _o__wfindnext32i64
- _o__wfindnext64
- _o__wfindnext64i32
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
- findnext
- _wfindnext32i64
- _tfindnext64i32
- findnext32
- findnext32i64
- wfindnext64i32
- _wfindnext
- tfindnext64
- findnexti64
- _findnexti64
- _tfindnexti64
- _findnext64i32
- tfindnexti64
- tfindnext32
- _wfindnext64i32
- findnext64i32
- _findnext
- _tfindnext32i64
- _wfindnext64
- wfindnext
- wfindnext32
- tfindnext32i64
- _findnext64
- _tfindnext64
- _wfindnext32
- findnext64
- _findnext32i64
- tfindnext
- wfindnexti64
- tfindnext64i32
- _tfindnext32
- wfindnext32i64
- wfindnext64
- _wfindnexti64
- _tfindnext
- _findnext32
helpviewer_keywords:
- _wfindnexti64 function
- _tfindnext32 function
- wfindnexti64 function
- _wfindnext32i64 function
- findnext32i64 function
- tfindnext64i32 function
- _tfindnext64i32 function
- _findnext function
- findnext64i32 function
- _tfindnext function
- findnext32 function
- tfindnext32 function
- _findnext32 function
- _tfindnext32i64 function
- _wfindnext function
- tfindnext function
- _findnext64 function
- findnext64 function
- _findnext64i32 function
- wfindnext32i64 function
- findnext function
- wfindnext32 function
- _wfindnext64i32 function
- findnexti64 function
- _wfindnext64 function
- _findnext32i64 function
- _findnexti64 function
- _tfindnext64 function
- wfindnext64i32 function
- tfindnexti64 function
- wfindnext64 function
- wfindnext function
- tfindnext64 function
- _wfindnext32 function
- tfindnext32i64 function
- _tfindnexti64 function
ms.assetid: 75d97188-5add-4698-a46c-4c492378f0f8
ms.openlocfilehash: 5513f3932b78d450ecce81947e0095efb8df1d9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263129"
---
# <a name="_findnext-_findnext32-_findnext32i64-_findnext64-_findnext64i32-_findnexti64-_wfindnext-_wfindnext32-_wfindnext32i64-_wfindnext64-_wfindnext64i32-_wfindnexti64"></a>_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64

[_Findfirst](findfirst-functions.md)에 대 한 이전 호출의 *filespec* 인수와 일치 하는 다음 이름 (있는 경우)을 찾은 다음 *fileinfo* 구조체 내용을 그에 따라 변경 합니다.

## <a name="syntax"></a>구문

```C
int _findnext(
   intptr_t handle,
   struct _finddata_t *fileinfo
);
int _findnext32(
   intptr_t handle,
   struct _finddata32_t *fileinfo
);
int _findnext64(
   intptr_t handle,
   struct __finddata64_t *fileinfo
);
int _findnexti64(
   intptr_t handle,
   struct __finddatai64_t *fileinfo
);
int _findnext32i64(
   intptr_t handle,
   struct _finddata32i64_t *fileinfo
);
int _findnext64i32(
   intptr_t handle,
   struct _finddata64i32_t *fileinfo
);
int _wfindnext(
   intptr_t handle,
   struct _wfinddata_t *fileinfo
);
int _wfindnext32(
   intptr_t handle,
   struct _wfinddata32_t *fileinfo
);
int _wfindnext64(
   intptr_t handle,
   struct _wfinddata64_t *fileinfo
);
int _wfindnexti64(
   intptr_t handle,
   struct _wfinddatai64_t *fileinfo
);
int _wfindnext32i64(
   intptr_t handle,
   struct _wfinddatai64_t *fileinfo
);
int _wfindnext64i32(
   intptr_t handle,
   struct _wfinddata64i32_t *fileinfo
);
```

### <a name="parameters"></a>매개 변수

*처리*<br/>
**_Findfirst** 에 대 한 이전 호출에서 반환 된 검색 핸들입니다.

*fileinfo*<br/>
파일 정보 버퍼입니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환합니다. 그렇지 않으면-1을 반환 하 고 **errno** 를 오류 특성을 나타내는 값으로 설정 합니다. 다음 표에 가능한 오류 코드가 나와 있습니다.

|errno 값|조건|
|-|-|
| **EINVAL** | 잘못 된 매개 변수: *fileinfo* 가 **NULL** 입니다. 또는 운영 체제에서 예기치 않은 오류를 반환했습니다. |
| **ENOENT (** | 일치하는 추가 파일을 찾을 수 없습니다. |
| **ENOMEM** | 메모리가 부족 하거나 파일 이름의 길이가 **MAX_PATH** 을 (를) 초과 했습니다. |

잘못된 매개 변수가 전달되면 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)의 설명대로 잘못된 매개 변수 처리기를 호출합니다.

## <a name="remarks"></a>설명

**_Findfirst** 또는 **_findnext** 함수 (또는 모든 변형)를 사용 하 여 완료 한 후 [_findclose](findclose.md) 를 호출 해야 합니다. 그러면 애플리케이션에서 이러한 함수에 사용된 리소스가 해제됩니다.

**W** 접두사가 있는 이러한 함수의 변형은 와이드 문자 버전입니다. 그렇지 않으면 해당 하는 싱글바이트 함수와 동일 합니다.

이러한 함수의 변형은 32비트 또는 64비트 시간 형식과 32비트 또는 64비트 파일 크기를 지원합니다. 첫 번째 숫자 접미사 (**32** 또는 **64**)는 사용 된 시간 형식의 크기를 나타냅니다. 두 번째 접미사는 **i32** 또는 **i64** 중 하나 이며, 파일 크기가 32 비트 또는 64 비트 정수로 표시 되는지를 나타냅니다. 어떤 버전이 32비트 및 64비트 시간 형식과 파일 크기를 지원하는지에 대한 자세한 내용은 다음 표를 참조하세요. 64비트 시간 형식을 사용하는 변형을 통해 3000년 12월 31일 23:59:59(UTC)까지 파일 생성 날짜를 표현할 수 있습니다. 반면, 32비트 시간 형식을 사용하는 변형은 2038년 1월 18일 23:59:59(UTC)까지의 날짜만 나타냅니다. 1970년 1월 1일 자정은 이러한 모든 함수에 대한 날짜 범위의 하한입니다.

시간 크기를 명시적으로 지정 하는 버전을 사용 해야 하는 특별 한 이유가 없다면 **_findnext** 또는 **_wfindnext** 를 사용 하 고, 3gb 보다 큰 파일 크기를 지원 해야 하는 경우에는 **_findnexti64** 또는 **_wfindnexti64** 를 사용 합니다. 이러한 함수는 모두 64비트 시간 형식을 사용합니다. 이전 버전에서는 이러한 함수에서 32비트 시간 형식을 사용했습니다. 응용 프로그램에 대 한 주요 변경 내용이 있는 경우 이전 동작을 얻기 위해 **_USE_32BIT_TIME_T** 를 정의할 수 있습니다. **_USE_32BIT_TIME_T** 정의 된 경우 **_findnext**, **_finnexti64** 및 해당 유니코드 버전은 32 비트 시간을 사용 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="time-type-and-file-length-type-variations-of-_findnext"></a>_findnext의 시간 형식 및 파일 길이 형식 변형

|함수|정의 **_USE_32BIT_TIME_T** ?|시간 형식|파일 길이 형식|
|---------------|----------------------------------|---------------|----------------------|
|**_findnext**, **_wfindnext**|정의되지 않음|64비트|32비트|
|**_findnext**, **_wfindnext**|정의됨|32비트|32비트|
|**_findnext32**, **_wfindnext32**|매크로 정의의 영향을 받지 않음|32비트|32비트|
|**_findnext64**, **_wfindnext64**|매크로 정의의 영향을 받지 않음|64비트|64비트|
|**_findnexti64**, **_wfindnexti64**|정의되지 않음|64비트|64비트|
|**_findnexti64**, **_wfindnexti64**|정의됨|32비트|64비트|
|**_findnext32i64**, **_wfindnext32i64**|매크로 정의의 영향을 받지 않음|32비트|64비트|
|**_findnext64i32**, **_wfindnext64i32**|매크로 정의의 영향을 받지 않음|64비트|32비트|

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindnext**|**_findnext**|**_findnext**|**_wfindnext**|
|**_tfindnext32**|**_findnext32**|**_findnext32**|**_wfindnext32**|
|**_tfindnext64**|**_findnext64**|**_findnext64**|**_wfindnext64**|
|**_tfindnexti64**|**_findnexti64**|**_findnexti64**|**_wfindnexti64**|
|**_tfindnext32i64**|**_findnext32i64**|**_findnext32i64**|**_wfindnext32i64**|
|**_tfindnext64i32**|**_findnext64i32**|**_findnext64i32**|**_wfindnext64i32**|

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**_findnext**|\<io.h>|
|**_findnext32**|\<io.h>|
|**_findnext64**|\<io.h>|
|**_findnexti64**|\<io.h>|
|**_findnext32i64**|\<io.h>|
|**_findnext64i32**|\<io.h>|
|**_wfindnext**|\<io.h> 또는 \<wchar.h>|
|**_wfindnext32**|\<io.h> 또는 \<wchar.h>|
|**_wfindnext64**|\<io.h> 또는 \<wchar.h>|
|**_wfindnexti64**|\<io.h> 또는 \<wchar.h>|
|**_wfindnext32i64**|\<io.h> 또는 \<wchar.h>|
|**_wfindnext64i32**|\<io.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="see-also"></a>참고 항목

[시스템 호출](../../c-runtime-library/system-calls.md)<br/>
[파일 이름 검색 함수](../../c-runtime-library/filename-search-functions.md)<br/>
