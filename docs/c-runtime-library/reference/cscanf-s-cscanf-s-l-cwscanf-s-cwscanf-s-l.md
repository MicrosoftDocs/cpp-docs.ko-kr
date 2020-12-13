---
description: '자세한 정보: _cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l'
title: _cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l
ms.date: 11/04/2016
api_name:
- _cwscanf_s_l
- _cwscanf_s
- _cscanf_s
- _cscanf_s_l
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
- cscanf_s
- cscanf_s_l
- cwscanf_s
- _cwscanf_s
- _tcscanf_s
- _cscanf_s
- _cwscanf_s_l
- _cscanf_s_l
- cwscanf_s_l
- _tcscanf_s_l
- tcscanf_s
- tcscanf_s_l
helpviewer_keywords:
- cscanf_s function
- _cwscanf_s_l function
- tcscanf_s function
- console [C++], reading from
- _cscanf_s function
- data [C++], reading from the console
- cwscanf_s function
- _tcscanf_s_l function
- _cscanf_s_l function
- cscanf_s_l function
- cwscanf_s_l function
- reading data [C++], from the console
- _cwscanf_s function
- _tcscanf_s function
- tcscanf_s_l function
ms.assetid: 9ccab74d-916f-42a6-93d8-920525efdf4b
ms.openlocfilehash: e379d454b9acd9cda75eb41721f55f0818004858
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332936"
---
# <a name="_cscanf_s-_cscanf_s_l-_cwscanf_s-_cwscanf_s_l"></a>_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l

콘솔에서 형식이 지정된 데이터를 읽습니다. 더 안전한 버전의 [_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)에는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 향상된 보안 기능이 포함되어 있습니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int _cscanf_s(
   const char *format [,
   argument] ...
);
int _cscanf_s_l(
   const char *format,
   locale_t locale [,
   argument] ...
);
int _cwscanf_s(
   const wchar_t *format [,
   argument] ...
);
int _cwscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>매개 변수

*format*<br/>
형식 컨트롤 문자열입니다.

*argument*<br/>
선택적 매개 변수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

성공적으로 변환되고 할당된 필드 수입니다. 읽혀졌지만 할당되지 않은 필드는 반환 값에 포함되지 않습니다. 파일의 끝에서 읽으려고 시도 하는 경우 반환 값은 **EOF** 입니다. 키보드 입력이 운영 체제 명령줄 수준에서 리디렉션될 때 발생할 수 있습니다. 반환 값이 0이면 할당된 필드가 없음을 의미합니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. *Format* 이 null 포인터인 경우 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **EOF** 를 반환 하 고 **errno** 는 **EINVAL** 로 설정 됩니다.

## <a name="remarks"></a>설명

**_Cscanf_s** 함수는 콘솔에서 *인수로* 지정 된 위치로 데이터를 직접 읽습니다. [_getche](getch-getwch.md) 함수는 문자를 읽는 데 사용합니다. 각 선택적 매개 변수 *는 형식의 형식* 지정자에 해당 하는 형식의 변수에 대 한 포인터 여야 합니다. 이 형식은 입력 필드의 해석을 제어 하 고 [scanf_s](scanf-scanf-l-wscanf-wscanf-l.md) 함수에 대 한 *형식* 매개 변수와 동일한 형식 및 기능을 가집니다. **_Cscanf_s** 는 일반적으로 입력 문자를 에코 하지만 마지막 호출이 **_ungetch** 된 경우에는이를 수행 하지 않습니다.

**Scanf** 패밀리에 있는 다른 보안 버전의 함수와 마찬가지로 **_cscanf_s** 및 **_cswscanf_s** 에는 형식 필드 문자 **c**, **c**, **s**, **s** 및 **[** 에 대 한 크기 인수가 필요 합니다. 자세한 내용은 [scanf 너비 사양](../../c-runtime-library/scanf-width-specification.md)을 참조하세요.

> [!NOTE]
> Size 매개 변수는 size_t이 **`unsigned`** 아니라 형식 입니다.

**_L** 접미사가 있는 이러한 함수 버전은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 한다는 점을 제외 하 고는 동일 합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcscanf_s**|**_cscanf_s**|**_cscanf_s**|**_cwscanf_s**|
|**_tcscanf_s_l**|**_cscanf_s_l**|**_cscanf_s_l**|**_cwscanf_s_l**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_cscanf_s**, **_cscanf_s_l**|\<conio.h>|
|**_cwscanf_s**, **_cwscanf_s_l**|\<conio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_cscanf_s.c
// compile with: /c
/* This program prompts for a string
* and uses _cscanf_s to read in the response.
* Then _cscanf_s returns the number of items
* matched, and the program displays that number.
*/

#include <stdio.h>
#include <conio.h>

int main( void )
{
   int result, n[3];
   int i;

   result = _cscanf_s( "%i %i %i", &n[0], &n[1], &n[2] );
   _cprintf_s( "\r\nYou entered " );
   for( i=0; i<result; i++ )
      _cprintf_s( "%i ", n[i] );
   _cprintf_s( "\r\n" );
}
```

```Input
1 2 3
```

```Output
You entered 1 2 3
```

## <a name="see-also"></a>참고 항목

[콘솔 및 포트 i/o](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
