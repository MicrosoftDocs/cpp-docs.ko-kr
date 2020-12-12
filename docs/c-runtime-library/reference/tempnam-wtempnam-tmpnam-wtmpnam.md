---
description: _Tempnam, _wtempnam, tmpnam, _wtmpnam에 대해 자세히 알아보세요.
title: _tempnam, _wtempnam, tmpnam, _wtmpnam
ms.date: 11/04/2016
api_name:
- _wtempnam
- _wtmpnam
- tmpnam
- _tempnam
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wtempnam
- _wtmpnam
- wtmpnam
- tmpnam
- _wtempnam
- _tempnam
helpviewer_keywords:
- wtempnam function
- file names [C++], creating temporary
- _tempnam function
- ttmpnam function
- tmpnam function
- tempnam function
- wtmpnam function
- temporary files, creating
- file names [C++], temporary
- _ttmpnam function
- _wtmpnam function
- _wtempnam function
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
ms.openlocfilehash: ee127a7d3ee59ec697dc0032fefb04b84b839c4d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326198"
---
# <a name="_tempnam-_wtempnam-tmpnam-_wtmpnam"></a>_tempnam, _wtempnam, tmpnam, _wtmpnam

임시 파일을 만드는 데 사용할 수 있는 이름을 생성합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [tmpnam_s, _wtmpnam_s](tmpnam-s-wtmpnam-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
char *_tempnam(
   const char *dir,
   const char *prefix
);
wchar_t *_wtempnam(
   const wchar_t *dir,
   const wchar_t *prefix
);
char *tmpnam(
   char *str
);
wchar_t *_wtmpnam(
   wchar_t *str
);
```

### <a name="parameters"></a>매개 변수

*prefix*<br/>
**_Tempnam** 에서 반환 하는 이름에 미리 보류할 문자열입니다.

*dir*<br/>
TMP 환경 함수가 없는 경우 또는 TMP가 올바른 디렉터리가 아닌 경우 파일 이름에 사용되는 경로입니다.

*str*<br/>
생성된 이름이 저장되며 함수가 반환하는 이름과 동일하게 지정되는 포인터입니다. 이 매개 변수를 사용하면 생성되는 이름을 편리하게 저장할 수 있습니다.

## <a name="return-value"></a>반환 값

이러한 각 함수는 생성 된 이름에 대 한 포인터를 반환 하거나 오류가 발생 한 경우 **NULL** 을 반환 합니다. **TMP_MAX** 이상 시도 하면 오류가 발생할 수 있습니다 (stdio.h 참조). H)를 사용 하 여 **tmpnam** 을 호출 하는 경우 또는 **_tempnam** 사용 하는 경우 TMP 환경 변수 및 *dir* 매개 변수에 잘못 된 디렉터리 이름이 지정 되어 있습니다.

> [!NOTE]
> **Tmpnam** 및 **_wtmpnam** 에서 반환 되는 포인터는 내부 정적 버퍼를 가리킵니다. 이러한 포인터를 할당 해제하기 위해 [free](free.md)를 호출해서는 안 됩니다. **_tempnam** 및 **_wtempnam** 에 의해 할당 된 포인터에 대해 **free** 를 호출 해야 합니다.

## <a name="remarks"></a>설명

이러한 각 함수는 현재 없는 파일의 이름을 반환합니다. **tmpnam** 는 [Gettemppathw](/windows/win32/api/fileapi/nf-fileapi-gettemppathw)에서 반환 하는 지정 된 Windows 임시 디렉터리에서 고유한 이름을 반환 합니다. **\_ tempnam** 는 지정 된 디렉터리가 아닌 다른 디렉터리에 고유한 이름을 생성 합니다. \fname21과 같이 파일 이름 앞에 백슬래시가 붙고 경로 정보는 없는 경우 현재 작업 디렉터리에 대해 해당 이름이 유효함을 나타냅니다.

**Tmpnam** 의 경우이 생성 된 파일 이름을 *str* 에 저장할 수 있습니다. *Str* 이 **NULL** 이면 **tmpnam** 는 결과를 내부 정적 버퍼에 그대로 둡니다. 따라서 모든 후속 호출에서는 이 값을 제거합니다. **Tmpnam** 에서 생성 된 이름은 프로그램 생성 파일 이름으로 구성 되 고, **tmpnam** 에 대 한 첫 번째 호출 후 stdio.h에 **TMP_MAX** 때 base 32 (. 1-)에 있는 일련 번호의 파일 확장명입니다. H는 32767입니다.

**_tempnam** 는 다음 규칙에 따라 선택한 디렉터리에 대해 고유한 파일 이름을 생성 합니다.

- TMP 환경 변수가 정의되어 있으며 올바른 디렉터리 이름으로 설정되어 있으면 TMP가 지정한 디렉터리에 대해 고유한 파일 이름이 생성됩니다.

- TMP 환경 변수가 정의 되어 있지 않거나 존재 하지 않는 디렉터리의 이름으로 설정 된 경우 **_tempnam** 은 고유한 이름을 생성 하는 경로로 *dir* 매개 변수를 사용 합니다.

- TMP 환경 변수가 정의 되어 있지 않거나 존재 하지 않는 디렉터리의 이름으로 설정 된 경우 및 *dir* 이 **NULL** 이거나 존재 하지 않는 디렉터리 이름으로 설정 된 경우 **_tempnam** 는 현재 작업 디렉터리를 사용 하 여 고유한 이름을 생성 합니다. 현재 TMP와 *dir* 모두 존재 하지 않는 디렉터리의 이름을 지정 하는 경우 **_tempnam** 함수 호출이 실패 합니다.

**_Tempnam** 에서 반환 되는 이름은 *접두사* 와 일련 번호의 연결로,이를 결합 하 여 지정 된 디렉터리에 대 한 고유한 파일 이름을 만듭니다. **_tempnam** 는 확장명이 없는 파일 이름을 생성 합니다. **_tempnam** 는 [malloc](malloc.md) 를 사용 하 여 파일 이름에 공간을 할당 합니다. 프로그램은 더 이상 필요 하지 않을 때이 공간을 확보 해야 합니다.

**_tempnam** 및 **tmpnam** 는 멀티 바이트 문자열 인수를 자동으로 적절 하 게 처리 하 여 운영 체제에서 가져온 OEM 코드 페이지에 따라 멀티 바이트 문자 시퀀스를 인식 합니다. **_wtempnam** 은 **_tempnam** 의 와이드 문자 버전입니다. **_wtempnam** 의 인수 및 반환 값은 와이드 문자 문자열입니다. **_wtempnam** 및 **_tempnam** 는 **_wtempnam** 에서 멀티 바이트 문자열을 처리 하지 않는다는 점만 제외 하 고 동일 하 게 동작 합니다. **_wtmpnam** 는 **tmpnam** 의 와이드 문자 버전입니다. **_wtmpnam** 의 인수 및 반환 값은 와이드 문자 문자열입니다. **_wtmpnam** 는 멀티 바이트 문자열을 처리 하지 않는다는 점을 제외 하 고 **_wtmpnam** 및 **tmpnam** 는 동일 하 게 동작 합니다.

**_DEBUG** 및 **_CRTDBG_MAP_ALLOC** 정의 된 경우 **_tempnam** 및 **_wtempnam** 는 [_tempnam_dbg 및 _wtempnam_dbg](tempnam-dbg-wtempnam-dbg.md)호출로 바뀝니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam**|**tmpnam**|**tmpnam**|**_wtmpnam**|
|**_ttempnam**|**_tempnam**|**_tempnam**|**_wtempnam**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_tempnam**|\<stdio.h>|
|**_wtempnam**, **_wtmpnam**|\<stdio.h> 또는 \<wchar.h>|
|**tmpnam**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_tempnam.c
// compile with: /W3
// This program uses tmpnam to create a unique filename in the
// temporary directory, and _tempname to create a unique filename
// in C:\\tmp.

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
   char * name1 = NULL;
   char * name2 = NULL;
   char * name3 = NULL;

   // Create a temporary filename for the current working directory:
   if ((name1 = tmpnam(NULL)) != NULL) { // C4996
   // Note: tmpnam is deprecated; consider using tmpnam_s instead
      printf("%s is safe to use as a temporary file.\n", name1);
   } else {
      printf("Cannot create a unique filename\n");
   }

   // Create a temporary filename in temporary directory with the
   // prefix "stq". The actual destination directory may vary
   // depending on the state of the TMP environment variable and
   // the global variable P_tmpdir.

   if ((name2 = _tempnam("c:\\tmp", "stq")) != NULL) {
      printf("%s is safe to use as a temporary file.\n", name2);
   } else {
      printf("Cannot create a unique filename\n");
   }

   // When name2 is no longer needed:
   if (name2) {
      free(name2);
   }

   // Unset TMP environment variable, then create a temporary filename in C:\tmp.
   if (_putenv("TMP=") != 0) {
      printf("Could not remove TMP environment variable.\n");
   }

   // With TMP unset, we will use C:\tmp as the temporary directory.
   // Create a temporary filename in C:\tmp with prefix "stq".
   if ((name3 = _tempnam("c:\\tmp", "stq")) != NULL) {
      printf("%s is safe to use as a temporary file.\n", name3);
   }
   else {
      printf("Cannot create a unique filename\n");
   }

   // When name3 is no longer needed:
   if (name3) {
      free(name3);
   }

   return 0;
}
```

```Output
C:\Users\LocalUser\AppData\Local\Temp\sriw.0 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\stq2 is safe to use as a temporary file.
c:\tmp\stq3 is safe to use as a temporary file.
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile](tmpfile.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
