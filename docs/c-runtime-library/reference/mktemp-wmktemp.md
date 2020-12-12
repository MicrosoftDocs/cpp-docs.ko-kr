---
description: '자세히 알아보기: _mktemp, _wmktemp'
title: _mktemp, _wmktemp
ms.date: 4/2/2020
api_name:
- _wmktemp
- _mktemp
- _o__mktemp
- _o__wmktemp
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
- _tmktemp
- wmktemp
- tmktemp
- _wmktemp
- _mktemp
helpviewer_keywords:
- _wmktemp function
- _mktemp function
- files [C++], temporary
- tmktemp function
- _tmktemp function
- wmktemp function
- mktemp function
- temporary files [C++]
ms.assetid: 055eb539-a8c2-4a7d-be54-f5b6d1eb5c85
ms.openlocfilehash: 06f75f8fd46bdd7ece42c292fd8ab6272ad39250
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114172"
---
# <a name="_mktemp-_wmktemp"></a>_mktemp, _wmktemp

고유한 파일 이름을 만듭니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [_mktemp_s, _wmktemp_s](mktemp-s-wmktemp-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
char *_mktemp(
   char *nameTemplate
);
wchar_t *_wmktemp(
   wchar_t *nameTemplate
);
template <size_t size>
char *_mktemp(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
wchar_t *_wmktemp(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>매개 변수

*nameTemplate*<br/>
파일 이름 패턴입니다.

## <a name="return-value"></a>반환 값

이러한 각 함수는 수정 된 nameTemplate에 대 한 포인터를 반환 합니다. *NameTemplate* 이 잘못 구성 되었거나 지정 된 nameTemplate에서 더 이상 고유한 이름을 만들 수 없는 경우이 함수는 **NULL** 을 반환 합니다.

## <a name="remarks"></a>설명

**_Mktemp** 함수는 *nameTemplate* 인수를 수정 하 여 고유한 파일 이름을 만듭니다. **_mktemp** 은 자동으로 멀티 바이트 문자열 인수를 적절 하 게 처리 하 고, 런타임 시스템에서 현재 사용 중인 멀티 바이트 코드 페이지에 따라 멀티 바이트 문자 시퀀스를 인식 합니다. **_wmktemp** 은 **_mktemp** 의 와이드 문자 버전입니다. **_wmktemp** 의 인수 및 반환 값은 와이드 문자 문자열입니다. **_wmktemp** 에서 멀티 바이트 문자열을 처리 하지 않는 경우를 제외 하 고 **_wmktemp** 및 **_mktemp** 는 동일 하 게 동작 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

*NameTemplate* 인수에는 *기본* XXXXXX 형식이 있습니다. 여기서 *base* 는 사용자가 제공 하는 새 파일 이름의 일부이 고 각 X는 **_mktemp** 에서 제공 하는 문자에 대 한 자리 표시자입니다. *NameTemplate* 의 각 자리 표시자 문자는 대문자 X 여야 합니다  . _mktemp *밑* 을 유지 하 고 첫 번째 후행 X를 영문자로 바꿉니다. **_mktemp** 는 다음 후행 X를 5 자리 값으로 바꿉니다. 이 값은 호출 프로세스 또는 다중 스레드 프로그램의 호출 스레드를 식별 하는 고유 번호입니다.

**_Mktemp** 에 대 한 각 호출은 *nameTemplate* 을 수정 합니다. 동일한 *nameTemplate* 인수를 사용 하는 동일한 프로세스 또는 스레드에서의 각 후속 호출에서 **_mktemp** 는 이전 호출에서 **_mktemp** 에서 반환 된 이름과 일치 하는 파일 이름을 확인 합니다. 지정 된 이름에 대 한 파일이 존재 하지 않는 경우 **_mktemp** 는 해당 이름을 반환 합니다. 이전에 반환 된 모든 이름에 대 한 파일이 존재 하는 경우 **_mktemp** 이전에 반환 된 이름에서 사용한 영문자를 ' a ' ~ ' z '부터 순서 대로 사용 가능한 다음 소문자로 대체 하 여 새 이름을 만듭니다. 예를 들어 *base* 가 다음과 같은 경우:

> **fn**

**_mktemp** 에서 제공 하는 5 자리 값은 12345이 고, 반환 되는 첫 번째 이름은입니다.

> **fna12345**

이 이름을 사용 하 여 FNA12345 파일을 만들 때이 파일이 여전히 존재 하는 경우 *nameTemplate* 에 대해 동일한 *기본* 을 사용 하는 동일한 프로세스 또는 스레드의 호출에서 반환 된 다음 이름은 다음과 같습니다.

> **fnb12345**

FNA12345가 존재하지 않는 경우 반환된 다음 이름은 다시 아래와 같습니다.

> **fna12345**

**_mktemp** 는 *base* 및 *nameTemplate* 값의 지정 된 조합에 대해 최대 26 개의 고유한 파일 이름을 만들 수 있습니다. 따라서 FNZ12345는이 예제에 사용 된 *base* 및 *nameTemplate* 값에 대해 만들 수 **_mktemp** 마지막으로 고유한 파일 이름입니다.

오류가 발생 하면 **errno** 가 설정 됩니다. *NameTemplate* 의 형식이 잘못 된 경우 (예: 6 X 미만) **errno** 가 **EINVAL** 로 설정 됩니다. 사용할 수 있는 파일 이름 26 개 모두 이미 존재 하기 때문에 **_mktemp** 에서 고유한 이름을 만들 수 없는 경우 **_mktemp** 를 빈 문자열로 설정 하 고 **eexist** 를 반환 합니다.

C++에서 이러한 함수는 보다 최신의 보안 대응 함수를 호출하는 템플릿 오버로드를 갖고 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_mktemp**|\<io.h>|
|**_wmktemp**|\<io.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_mktemp.c
// compile with: /W3
/* The program uses _mktemp to create
* unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>
#include <errno.h>

char *template = "fnXXXXXX";
char *result;
char names[27][9];

int main( void )
{
   int i;
   FILE *fp;

   for( i = 0; i < 27; i++ )
   {
      strcpy_s( names[i], sizeof( names[i] ), template );
      /* Attempt to find a unique filename: */
      result = _mktemp( names[i] );  // C4996
      // Note: _mktemp is deprecated; consider using _mktemp_s instead
      if( result == NULL )
      {
         printf( "Problem creating the template\n" );
         if (errno == EINVAL)
         {
             printf( "Bad parameter\n");
         }
         else if (errno == EEXIST)
         {
             printf( "Out of unique filenames\n");
         }
      }
      else
      {
         fopen_s( &fp, result, "w" );
         if( fp != NULL )
            printf( "Unique filename is %s\n", result );
         else
            printf( "Cannot open %s\n", result );
         fclose( fp );
      }
   }
}
```

```Output
Unique filename is fna03912
Unique filename is fnb03912
Unique filename is fnc03912
Unique filename is fnd03912
Unique filename is fne03912
Unique filename is fnf03912
Unique filename is fng03912
Unique filename is fnh03912
Unique filename is fni03912
Unique filename is fnj03912
Unique filename is fnk03912
Unique filename is fnl03912
Unique filename is fnm03912
Unique filename is fnn03912
Unique filename is fno03912
Unique filename is fnp03912
Unique filename is fnq03912
Unique filename is fnr03912
Unique filename is fns03912
Unique filename is fnt03912
Unique filename is fnu03912
Unique filename is fnv03912
Unique filename is fnw03912
Unique filename is fnx03912
Unique filename is fny03912
Unique filename is fnz03912
Problem creating the template.
Out of unique filenames.
```

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile](tmpfile.md)<br/>
