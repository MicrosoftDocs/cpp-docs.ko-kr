---
title: gets_s, _getws_s | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _getws_s
- gets_s
apilocation:
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
apitype: DLLExport
f1_keywords:
- _getws_s
- gets_s
dev_langs:
- C++
helpviewer_keywords:
- getws_s function
- _getws_s function
- lines, getting
- streams, getting lines
- buffers, avoiding overruns
- buffer overruns
- buffers, buffer overruns
- gets_s function
- standard input, reading from
ms.assetid: 5880c36f-122c-4061-a1a5-aeeced6fe58c
caps.latest.revision: 29
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efd4e458fa71fd6dcd93d47350c998a4a410cc65
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
---
# <a name="getss-getwss"></a>gets_s, _getws_s

줄을 가져옵니다는 **stdin** 스트림 합니다. 이러한 버전의 [gets, _getws](../../c-runtime-library/gets-getws.md)에는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 강화된 보안 기능이 포함되어 있습니다.

## <a name="syntax"></a>구문

```C
char *gets_s(
   char *buffer,
   size_t sizeInCharacters
);
wchar_t *_getws_s(
   wchar_t *buffer,
   size_t sizeInCharacters
);
```

```cpp
template <size_t size>
char *gets_s( char (&buffer)[size] ); // C++ only

template <size_t size>
wchar_t *_getws_s( wchar_t (&buffer)[size] ); // C++ only
```

### <a name="parameters"></a>매개 변수

*buffer*<br/>
입력 문자열에 대한 저장소 위치입니다.

*sizeInCharacters*<br/>
버퍼의 크기입니다.

## <a name="return-value"></a>반환 값

반환 *버퍼* 성공 하는 경우. A **NULL** 포인터는 오류 또는 파일 끝 조건을 나타냅니다. 어떤 것이 발생했는지 확인하려면 [ferror](ferror.md) 또는 [feof](feof.md)를 사용합니다.

## <a name="remarks"></a>설명

**gets_s** 함수는 표준 입력 스트림에서 한 줄 읽고 **stdin** 저장 *버퍼*합니다. 줄은 첫 번째 줄 바꿈 문자('\n')까지 모든 문자로 구성됩니다. **gets_s** 줄을 반환 하기 전에 줄 바꿈 문자를 null 문자 ('\0')로 대체 합니다. 반면,는 **fgets_s** 함수는 줄 바꿈 문자를 유지 합니다.

Null 문자 맨 앞에 저장은 읽은 첫 번째 문자는 파일의 끝 문자 이면 *버퍼* 및 **NULL** 반환 됩니다.

**_getws_s** 의 와이드 문자 버전이 **gets_s**; 해당 인수 및 반환 값은 와이드 문자 문자열입니다.

경우 *버퍼* 은 **NULL** 또는 *sizeInCharacters* 가 0 보다 작은 또는 버퍼가 너무 작아서 입력된 줄와 null 종결자를 포함 하는 경우 이러한 함수 호출 에 설명 된 대로 잘못 된 매개 변수 처리기는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)합니다. 실행을 계속 허용 된 경우 이러한 함수가 반환 **NULL** errno로 설정 하 고 **ERANGE**합니다.

C++에서는 템플릿 오버로드로 인해 이러한 함수를 사용하는 것이 보다 간단해 집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으며(크기 인수를 지정할 필요가 없어짐), 기존의 비보안 함수를 보다 최신의 보안 대응 함수로 자동으로 바꿀 수 있습니다. 자세한 내용은 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)을 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_getts_s**|**gets_s**|**gets_s**|**_getws_s**|

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**gets_s**|\<stdio.h>|
|**_getws_s**|\<stdio.h> 또는 \<wchar.h>|

콘솔 유니버설 Windows 플랫폼 (UWP) 응용 프로그램에서 지원 되지 않습니다. 콘솔을 사용 하는 연결 된 표준 스트림 핸들 **stdin**, **stdout**, 및 **stderr**, C 런타임 함수 UWP 앱에서 사용할 수 있는 전에 리디렉션되어야 . 호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_gets_s.c
// This program retrieves a string from the stdin and
// prints the same string to the console.

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets_s( line, 20 );
   printf( "The line entered was: %s\n", line );
}
```

```Input
Hello there!
```

```Output
The line entered was: Hello there!
```

## <a name="see-also"></a>참고자료

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[fgets, fgetws](fgets-fgetws.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
