---
description: '자세히 알아보기: _cgets, _cgetws'
title: _cgets, _cgetws
ms.date: 4/2/2020
api_name:
- _cgetws
- _cgets
- _o__cgets
- _o__cgetws
api_location:
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-conio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- cgetws
- _cgetws
- _cgets
helpviewer_keywords:
- _cgetws function
- strings [C++], getting from console
- console, getting strings from
- _cgets function
- cgetws function
- cgets function
ms.assetid: 4d5e134a-58c3-4f62-befd-5d235b0212f4
ms.openlocfilehash: ac712c7ee51c3f06dfe1dd4e881630768a7e6b20
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221685"
---
# <a name="_cgets-_cgetws"></a>_cgets, _cgetws

콘솔에서 문자열을 가져옵니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)를 참조하세요.

> [!IMPORTANT]
> 이러한 함수는 사용되지 않습니다. Visual Studio 2015부터 CRT에서 사용할 수 없습니다. 이러한 함수의 안전한 버전인 _cgets_s 및 _cgetws_s는 계속 사용할 수 있습니다. 이러한 대체 함수에 대한 자세한 내용은 [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)를 참조하세요.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```
char *_cgets(
   char *buffer
);
wchar_t *_cgetws(
   wchar_t *buffer
);
template <size_t size>
char *_cgets(
   char (&buffer)[size]
); // C++ only
template <size_t size>
wchar_t *_cgetws(
   wchar_t (&buffer)[size]
); // C++ only
```

#### <a name="parameters"></a>매개 변수

*버퍼*<br/>
데이터의 스토리지 위치입니다.

## <a name="return-value"></a>반환 값

`_cgets` 및 `_cgetws` 는 `buffer[2]`에서 문자열의 시작에 대한 포인터를 반환합니다. `buffer`이 **NULL** 인 경우 이러한 함수는 [매개 변수 유효성 검사](../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기를 호출합니다. 계속해서 실행하도록 허용된 경우, 이러한 함수는 **NULL** 을 반환하고 `errno`를 `EINVAL`로 설정합니다.

## <a name="remarks"></a>설명

이러한 함수는 콘솔에서 문자열을 읽고 문자열과 해당 길이를 `buffer`가 가리키는 위치에 저장합니다. `buffer` 매개 변수는 문자 배열에 대한 포인터여야 합니다. 배열의 첫 번째 요소인 `buffer[0]`에는 읽을 문자열의 최대 길이(문자)가 포함되어야 합니다. 배열에 문자열, 종료 null 문자('\0') 및 추가 2바이트를 저장하는 데 충분한 요소가 포함되어야 합니다. 함수는 CR-LF(캐리지 리턴-줄 바꿈) 조합이나 지정된 개수의 문자를 읽을 때까지 문자를 읽습니다. `buffer[2]`부터 시작하여 문자열이 저장됩니다. 함수는 CR-LF를 읽을 경우 null 문자('\0')를 저장합니다. 그런 다음 문자열의 실제 길이를 두 번째 배열 요소인 `buffer[1]`에 저장합니다.

콘솔 창에 있는 동안 `_cgets` 또는 `_cgetws` 를 호출한 경우 모든 편집 키가 활성 상태이기 때문에 F3 키를 누르면 마지막으로 입력한 항목이 반복됩니다.

C++에서 이러한 함수는 보다 최신의 보안 대응 함수를 호출하는 템플릿 오버로드를 갖고 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../c-runtime-library/secure-template-overloads.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_cgetts`|`_cgets`|`_cgets`|`_cgetws`|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|`_cgets`|\<conio.h>|
|`_cgetws`|\<conio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```c
// crt_cgets.c
// compile with: /c /W3
// This program creates a buffer and initializes
// the first byte to the size of the buffer. Next, the
// program accepts an input string using _cgets and displays
// the size and text of that string.

#include <conio.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
   char buffer[83] = { 80 };  // Maximum characters in 1st byte
   char *result;

   printf( "Input line of text, followed by carriage return:\n");

   // Input a line of text:
   result = _cgets( buffer ); // C4996
   // Note: _cgets is deprecated; consider using _cgets_s
   if (!result)
   {
      printf( "An error occurred reading from the console:"
              " error code %d\n", errno);
   }
   else
   {
      printf( "\nLine length = %d\nText = %s\n",
              buffer[1], result );
   }
}
```

```Output

      A line of input.Input line of text, followed by carriage return:
Line Length = 16
Text = A line of input.
```

## <a name="see-also"></a>참고 항목

[콘솔 및 포트 i/o](../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)
