---
description: '다음에 대 한 자세한 정보: __crtLCMapStringW'
title: __crtLCMapStringW
ms.date: 11/04/2016
api_name:
- __crtLCMapStringW
api_location:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __crtLCMapStringW
helpviewer_keywords:
- __crtLCMapStringW
ms.assetid: 45b4ac0e-438c-4fa3-b4d1-34195f4467d9
ms.openlocfilehash: 57b3f7e961de94d8a3dbd045a1fa1d74681cbfdc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246759"
---
# <a name="__crtlcmapstringw"></a>__crtLCMapStringW

지정된 로캘 종속 변환을 수행하여 하나의 문자열을 다른 문자열에 매핑합니다. 이 함수는 입력 문자열에 대한 정렬 키를 생성하는 데에도 사용될 수 있습니다.

## <a name="syntax"></a>구문

```cpp
int __crtLCMapStringW(
   LCID    Locale,
   DWORD   dwMapFlags,
   LPCWSTR lpSrcStr,
   int     cchSrc,
   LPWSTR  lpDestStr,
   int     cchDest)
```

#### <a name="parameters"></a>매개 변수

*로캘*<br/>
로캘 식별자입니다. 로캘은 문자열 매핑 또는 정렬 키 생성을 위한 컨텍스트를 제공합니다. 애플리케이션은 `MAKELCID` 매크로를 사용하여 로캘 식별자를 만들 수 있습니다.

*dwMapFlags*<br/>
문자열 매핑 또는 정렬 키 생성 시 사용할 변환 형식입니다.

*lpSrcStr*<br/>
함수가 정렬 키 생성을 위해 매핑하거나 사용하는 소스 문자열에 대한 포인터입니다. 이 매개 변수는 유니코드 문자열로 간주됩니다.

*cchSrc*<br/>
`lpSrcStr` 매개 변수가 가리키는 문자열의 크기(문자)입니다. 이 수는 null 종결자를 포함하거나 포함하지 않을 수 있습니다.

`cchSrc` 값이 -1이면 `lpSrcStr`이 가리키는 문자열이 null로 끝나도록 지정됩니다. 이 경우 이 함수가 해당 문자열 매핑 모드에서 사용 중이면 해당 함수는 문자열 길이 자체를 계산하고 `*lpDestStr`에 저장된 매핑된 문자열을 null로 끝냅니다.

*lpDestStr*<br/>
함수가 매핑된 문자열 또는 정렬 키를 저장하는 버퍼에 대한 긴 포인터입니다.

*cchDest*<br/>
`lpDestStr`이 가리키는 버퍼의 크기(문자)입니다.

## <a name="return-value"></a>반환 값

`cchDest` 의 값이 0이 아닌 경우 문자 수 또는 바이트이며, `LCMAP_SORTKEY` 가 지정된 경우 버퍼에 쓰여진 값은 성공을 나타냅니다. 이 수는 null 종결자에 대한 공간을 포함합니다.

`cchDest` 의 값이 0인 경우 버퍼의 크기(문자 또는 바이트)이며, `LCMAP_SORTKEY` 가 지정된 경우 변환된 문자열 또는 정렬 키를 받는 데 필요한 값은 성공을 나타냅니다. 이 크기는 null 종결자에 대한 공간을 포함합니다.

0은 실패를 나타냅니다. 확장 오류 정보를 가져오려면 `GetLastError` 함수를 호출하십시오.

## <a name="remarks"></a>설명

`cchSrc` 가 0보다 크고 `lpSrcStr` 이 null 종결 문자열인 경우 `__crtLCMapStringW` 는 `cchSrc` 를 문자열 길이로 설정합니다. 그러면 `__crtLCMapStringW` 가 지정된 매개 변수를 사용하여 `LCMapString` 함수의 와이드 문자(유니코드) 버전을 호출합니다. 이 함수의 반환 값 및 매개 변수에 대한 자세한 내용은 [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|__crtLCMapStringW|awint.h|
