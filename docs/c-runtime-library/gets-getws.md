---
description: '자세한 정보: 가져오기, _getws'
title: gets, _getws
ms.date: 4/2/2020
api_name:
- _getws
- gets
- _o__getws
- _o_gets
api_location:
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getts
- gets
- _getws
helpviewer_keywords:
- getws function
- getts function
- _getws function
- lines, getting
- streams, getting lines
- _getts function
- gets function
- standard input, reading from
ms.assetid: 1ec2dd4b-f801-48ea-97c2-892590f16024
ms.openlocfilehash: cb2bf89bfcec8e10e05fa479cd7c9d78d9c6d80e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181724"
---
# <a name="gets-_getws"></a>gets, _getws

`stdin` 스트림에서 줄을 가져옵니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)를 참조하세요.

> [!IMPORTANT]
> 이러한 함수는 사용되지 않습니다. Visual Studio 2015부터 CRT에서 사용할 수 없습니다. 이러한 함수의 안전한 버전인 gets_s 및 _getws_s는 계속 사용할 수 있습니다. 이러한 대체 함수에 대한 자세한 내용은 [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)를 참조하세요.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```
char *gets(
   char *buffer
);
wchar_t *_getws(
   wchar_t *buffer
);
template <size_t size>
char *gets(
   char (&buffer)[size]
); // C++ only
template <size_t size>
wchar_t *_getws(
   wchar_t (&buffer)[size]
); // C++ only
```

#### <a name="parameters"></a>매개 변수

*버퍼*<br/>
입력 문자열에 대한 스토리지 위치입니다.

## <a name="return-value"></a>반환 값

성공하면 해당 인수를 반환합니다. **NULL** 포인터는 오류 또는 파일 끝 조건을 나타냅니다. 어떤 것이 발생했는지 확인하려면 [ferror](../c-runtime-library/reference/ferror.md) 또는 [feof](../c-runtime-library/reference/feof.md) 를 사용하십시오. `buffer`이 **NULL** 인 경우 이러한 함수는 [매개 변수 유효성 검사](../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기를 호출합니다. 계속해서 실행하도록 허용된 경우 이러한 함수는 **NULL** 을 반환하고 errno를 `EINVAL`로 설정합니다.

## <a name="remarks"></a>설명

`gets` 함수는 표준 입력 스트림 `stdin`에서 줄을 읽고 `buffer`에 저장합니다. 줄은 첫 번째 줄 바꿈 문자('\n')까지 모든 문자로 구성됩니다. `gets` 는 줄을 반환하기 전에 줄 바꿈 문자를 null 문자('\0')로 대체합니다. 반대로 `fgets` 함수는 줄 바꿈 문자를 유지합니다. `_getws` 는 `gets`의 와이드 문자 버전입니다. 해당 인수 및 반환 값은 와이드 문자열입니다.

> [!IMPORTANT]
> gets에서 읽은 문자 수에 대한 제한이 없으므로 신뢰할 수 없는 입력에서 쉽게 버퍼 오버런이 발생할 수 있습니다. 대신 `fgets`를 사용하세요.

C++에서 이러한 함수는 보다 최신의 보안 대응 함수를 호출하는 템플릿 오버로드를 갖고 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../c-runtime-library/secure-template-overloads.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_getts`|`gets`|`gets`|`_getws`|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|`gets`|\<stdio.h>|
|`_getws`|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```c
// crt_gets.c
// compile with: /WX /W3

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets( line );  // C4996
   // Danger: No way to limit input to 20 chars.
   // Consider using gets_s instead.
   printf( "The line entered was: %s\n", line );
}
```

20자보다 긴 입력에서 줄 버퍼를 오버런하면 대부분 프로그램에서 충돌이 유발될 수 있습니다.

```Output

Hello there!The line entered was: Hello there!
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../c-runtime-library/stream-i-o.md)<br/>
[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)<br/>
[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)<br/>
[puts, _putws](../c-runtime-library/reference/puts-putws.md)
