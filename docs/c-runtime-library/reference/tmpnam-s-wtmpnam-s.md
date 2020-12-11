---
description: '자세히 알아보기: tmpnam_s, _wtmpnam_s'
title: tmpnam_s, _wtmpnam_s
ms.date: 4/2/2020
api_name:
- tmpnam_s
- _wtmpnam_s
- _o__wtmpnam_s
- _o_tmpnam_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
ms.openlocfilehash: fefaa0ca54ecd1a4ae0a61f10ab502cf5310648a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155789"
---
# <a name="tmpnam_s-_wtmpnam_s"></a>tmpnam_s, _wtmpnam_s

임시 파일을 만드는 데 사용할 수 있는 이름을 생성합니다. 이러한 함수는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 강화된 보안 기능이 있는 [tmpnam 및 _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)의 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t tmpnam_s(
   char * str,
   size_t sizeInChars
);
errno_t _wtmpnam_s(
   wchar_t *str,
   size_t sizeInChars
);
template <size_t size>
errno_t tmpnam_s(
   char (&str)[size]
); // C++ only
template <size_t size>
errno_t _wtmpnam_s(
   wchar_t (&str)[size]
); // C++ only
```

### <a name="parameters"></a>매개 변수

*str*<br/>
생성된 이름이 저장되는 포인터입니다.

*sizeInChars*<br/>
버퍼의 크기(문자)입니다.

## <a name="return-value"></a>반환 값

이 두 함수는 정상적으로 실행되면 0을 반환하고 오류 시에는 오류 번호를 반환합니다.

### <a name="error-conditions"></a>오류 조건

| *str* | *sizeInChars* | **반환 값** | *Str* **의 내용** |
|--|--|--|--|
| **NULL** | any | **EINVAL** | 수정 안 됨 |
| not **NULL** (유효한 메모리를 가리킴) | 너무 짧음 | **ERANGE** | 수정 안 됨 |

*Str* 이 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **errno** 를 **EINVAL** 로 설정 하 고 **EINVAL** 를 반환 합니다.

## <a name="remarks"></a>설명

이러한 각 함수는 현재 없는 파일의 이름을 반환합니다. **tmpnam_s** 는 [Gettemppathw](/windows/win32/api/fileapi/nf-fileapi-gettemppathw)에서 반환 하는 지정 된 Windows 임시 디렉터리에서 고유한 이름을 반환 합니다. \fname21과 같이 파일 이름 앞에 백슬래시가 붙고 경로 정보는 없는 경우 현재 작업 디렉터리에 대해 해당 이름이 유효함을 나타냅니다.

**Tmpnam_s** 의 경우이 생성 된 파일 이름을 *str* 에 저장할 수 있습니다. **Tmpnam_s** 에서 반환 되는 문자열의 최대 길이는 stdio.h에 정의 된 **L_tmpnam_s** 입니다. *Str* 이 **NULL** 인 경우 **tmpnam_s** 은 결과를 내부 정적 버퍼에 그대로 둡니다. 따라서 모든 후속 호출에서는 이 값을 제거합니다. **Tmpnam_s** 에서 생성 되는 이름은 프로그램에서 생성 된 파일 이름으로 구성 되 고, **tmpnam_s** 에 대 한 첫 번째 호출 후에는 stdio.h에서 **TMP_MAX_S** 때 base 32 (. 1-. 1vvvvvu)에 있는 일련 번호의 파일 확장명이 됩니다. H는 **INT_MAX**)입니다.

**tmpnam_s** 은 자동으로 멀티 바이트 문자열 인수를 적절 하 게 처리 하 여 운영 체제에서 가져온 OEM 코드 페이지에 따라 멀티 바이트 문자 시퀀스를 인식 합니다. **_wtmpnam_s** 은 **tmpnam_s** 의 와이드 문자 버전입니다. **_wtmpnam_s** 의 인수 및 반환 값은 와이드 문자 문자열입니다. **_wtmpnam_s** 및 **tmpnam_s** 는 **_wtmpnam_s** 에서 멀티 바이트 문자열을 처리 하지 않는다는 점만 제외 하 고 동일 하 게 동작 합니다.

C++에서는 템플릿 오버로드를 통해 이러한 함수를 사용하는 것이 더욱 간단해집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으므로 크기 인수를 지정할 필요가 없습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam_s**|**tmpnam_s**|**tmpnam_s**|**_wtmpnam_s**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**tmpnam_s**|\<stdio.h>|
|**_wtmpnam_s**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_tmpnam_s.c
// This program uses tmpnam_s to create a unique filename in the
// current working directory.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char name1[L_tmpnam_s];
   errno_t err;
   int i;

   for (i = 0; i < 15; i++)
   {
      err = tmpnam_s( name1, L_tmpnam_s );
      if (err)
      {
         printf("Error occurred creating unique filename.\n");
         exit(1);
      }
      else
      {
         printf( "%s is safe to use as a temporary file.\n", name1 );
      }
   }
}
```

```Output
C:\Users\LocalUser\AppData\Local\Temp\u19q8.0 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.1 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.2 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.3 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.4 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.5 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.6 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.7 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.8 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.9 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.a is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.b is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.c is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.d is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.e is safe to use as a temporary file.
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
