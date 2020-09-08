---
title: sct.inp, _inp, inpw, _inpw, _inpd
description: Microsoft CRT (C 런타임 라이브러리)의 사용 되지 않거나 제거 된 sct.inp, _inp, inpw, _inpw 및 _inpd 함수에 대해 설명 합니다.
ms.date: 12/09/2019
api_name:
- inp
- inpw
- _inp
- _inpw
- _inpd
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- inp
- inpw
- _inp
- _inpw
- _inpd
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
ms.openlocfilehash: aafcd633b2ee04c9ced1520d4ecd1520475d0fea
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556478"
---
# <a name="inp-_inp-inpw-_inpw-_inpd"></a>sct.inp, _inp, inpw, _inpw, _inpd

포트, 바이트 ( `inp` ,) `_inp` , 단어 ( `inpw` , `_inpw` ) 또는 2 배 워드 ()를 입력 `_inpd` 합니다.

> [!IMPORTANT]
> 이러한 함수는 사용되지 않습니다. Visual Studio 2015부터 CRT에서 사용할 수 없습니다.
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```cpp
int _inp(
   unsigned short port
);
unsigned short _inpw(
   unsigned short port
);
unsigned long _inpd(
   unsigned short port
);
```

### <a name="parameters"></a>매개 변수

*포트인*\
I/O 포트 번호입니다.

## <a name="return-value"></a>반환 값

함수가 `port`에서 바이트, 워드 또는 2배 워드를 반환합니다. 오류가 반환 되지 않습니다.

## <a name="remarks"></a>설명

`_inp`, `_inpw`및 `_inpd` 함수는 바이트, 워드 및 2배 워드를 각각 지정된 된 입력 포트로부터 읽습니다. 입력 값은 0 - 65,535 범위의 부호 없는 정수(Short)입니다.

이러한 함수는 I/O 포트에서 직접 읽기 때문에 사용자 코드에서 사용할 수 없습니다.

및 `inp` `inpw` 이름은 이전 버전의 및 함수에 사용 되지 않는 이름입니다 `_inp` `_inpw` . 자세한 내용은 [POSIX 함수 이름](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)을 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|`_inp`|\<conio.h>|
|`_inpw`|\<conio.h>|
|`_inpd`|\<conio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../c-runtime-library/crt-library-features.md)입니다.

## <a name="see-also"></a>참고 항목

[콘솔 및 포트 i/o](../c-runtime-library/console-and-port-i-o.md)\
[outp, outp, _outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)
