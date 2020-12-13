---
description: '다음에 대 한 자세한 정보: _setmbcp'
title: _setmbcp
ms.date: 4/2/2020
api_name:
- _setmbcp
- _o__setmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _setmbcp
- setmbcp
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
ms.openlocfilehash: fe69360de2e6e0ebdea8c700ab398d56e669f022
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342220"
---
# <a name="_setmbcp"></a>_setmbcp

새 멀티바이트 코드 페이지를 설정합니다.

## <a name="syntax"></a>구문

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>매개 변수

*codepage*<br/>
로캘 독립적인 멀티바이트 루틴에 대한 새 코드 페이지 설정입니다.

## <a name="return-value"></a>반환 값

코드 페이지가 올바르게 설정되면 0을 반환합니다. *코드 페이지에 대해 잘못* 된 코드 페이지 값이 제공 된 경우는-1을 반환 하 고 코드 페이지 설정은 변경 되지 않습니다. 메모리 할당 오류가 발생 하는 경우 **errno** 을 **EINVAL** 로 설정 합니다.

## <a name="remarks"></a>설명

**_Setmbcp** 함수는 새 멀티 바이트 코드 페이지를 지정 합니다. 기본적으로 런타임 시스템은 멀티바이트 코드 페이지를 시스템 기본 ANSI 코드 페이지로 자동 설정합니다. 멀티바이트 코드 페이지 설정은 로캘에 종속되지 않는 모든 멀티바이트 루틴에 적용됩니다. 그러나 **_setmbcp** 에 현재 로캘에 대해 정의 된 코드 페이지를 사용 하도록 지시할 수 있습니다 (다음 매니페스트 상수 및 관련 동작 결과 목록 참조). 멀티바이트 코드 페이지가 아닌 로캘 코드 페이지를 사용하는 멀티바이트 루틴의 목록은 [멀티바이트 문자 시퀀스 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)을 참조하세요.

*Codepage* 인수는 다음 값 중 하나로 설정할 수 있습니다.

- **_MB_CP_ANSI** 프로그램 시작 시 운영 체제에서 가져온 ANSI 코드 페이지를 사용 합니다.

- **_MB_CP_LOCALE** [Setlocale](setlocale-wsetlocale.md)에 대 한 이전 호출에서 가져온 현재 로캘의 코드 페이지를 사용 합니다.

- **_MB_CP_OEM** 프로그램 시작 시 운영 체제에서 가져온 OEM 코드 페이지를 사용 합니다.

- **_MB_CP_SBCS** 싱글바이트 코드 페이지를 사용 합니다. 코드 페이지가 **_MB_CP_SBCS** 로 설정 된 경우 [_ismbblead](ismbblead-ismbblead-l.md) 와 같은 루틴은 항상 false를 반환 합니다.

- **_MB_CP_UTF8** U t f-8을 사용 합니다.  코드 페이지가 **_MB_CP_UTF8** 로 설정 된 경우 [_ismbblead](ismbblead-ismbblead-l.md) 와 같은 루틴은 항상 false를 반환 합니다.

- 다른 모든 유효한 코드 페이지 값은 값이 ANSI, OEM 또는 기타 운영 체제 지원 코드 페이지 (지원 되지 않는 u t f-7 제외) 인지 여부에 관계 없이 모든 유효한 코드 페이지 값입니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
