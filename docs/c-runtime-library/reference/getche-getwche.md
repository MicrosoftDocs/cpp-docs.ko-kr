---
title: _getche, _getwche | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _getwche
- _getche
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- getwche
- _getche
- _getwche
dev_langs:
- C++
helpviewer_keywords:
- characters, getting from console
- _getwche function
- getche function
- console, reading from
- getwche function
- _getche function
ms.assetid: eac978a8-c43a-4130-938f-54f12e2a0fda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bfd791eb0ac022cfd13de74ca902ef45565ac16
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42571406"
---
# <a name="getche-getwche"></a>_getche, _getwche

에코를 사용하여 콘솔에서 문자를 가져옵니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int _getche( void );
wint_t _getwche( void );
```

## <a name="return-value"></a>반환 값

읽은 문자를 반환합니다. 반환되는 오류가 없습니다.

## <a name="remarks"></a>설명

합니다 **_getche** 하 고 **_getwche** 함수 echo, 문자가 콘솔에 표시 되는 의미를 사용 하 여 콘솔에서 단일 문자를 읽습니다. 이 중 어느 것도, CTRL + C를 읽을 수 없습니다. 화살표 키 또는 기능 키를 읽을 때, 각 함수는 두 번 호출되어야 합니다. 0 또는 0xE0를 첫 번째 호출에서 반환하고 실제 키 코드를 두 번째 호출에서 반환합니다.

이러한 함수는 호출 스레드를 잠그므로 스레드로부터 안전합니다. 잠기지 않는 버전의 경우 [_getche_nolock, _getwche_nolock](getche-nolock-getwche-nolock.md)을 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 루틴 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_getche**|**_getche**|**_getch**|**_getwche**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_getche**|\<conio.h>|
|**_getwche**|\<conio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예

```C
// crt_getche.c
// compile with: /c
// This program reads characters from
// the keyboard until it receives a 'Y' or 'y'.

#include <conio.h>
#include <ctype.h>

int main( void )
{
   int ch;

   _cputs( "Type 'Y' when finished typing keys: " );
   do
   {
      ch = _getche();
      ch = toupper( ch );
   } while( ch != 'Y' );

   _putch( ch );
   _putch( '\r' );    // Carriage return
   _putch( '\n' );    // Line feed
}
```

```Input
abcdefy
```

```Output
Type 'Y' when finished typing keys: abcdefyY
```

## <a name="see-also"></a>참고자료

[콘솔 및 포트 I/O](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cgets, _cgetws](../../c-runtime-library/cgets-cgetws.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[_ungetch, _ungetwch, _ungetch_nolock, _ungetwch_nolock](ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)<br/>
