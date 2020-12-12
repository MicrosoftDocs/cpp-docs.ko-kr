---
description: '자세히 알아보기: isblank, iswblank, _isblank_l, _iswblank_l'
title: isblank, iswblank, _isblank_l, _iswblank_l
ms.date: 4/2/2020
api_name:
- isblank
- _isblank_l
- iswblank
- _iswblank_l
- _o_isblank
- _o_iswblank
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _iswblank_l
- isblank
- _istblank_l
- _istblank
- _isblank_l
- iswblank
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
ms.openlocfilehash: a2731468cda3a2d3bf059133f116b22fa2b019f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321115"
---
# <a name="isblank-iswblank-_isblank_l-_iswblank_l"></a>isblank, iswblank, _isblank_l, _iswblank_l

정수가 공백 문자를 나타내는지 여부를 확인합니다.

## <a name="syntax"></a>구문

```C
int isblank(
   int c
);
int iswblank(
   wint_t c
);
int _isblank_l(
   int c,
   _locale_t locale
);
int _iswblank_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*c*<br/>
테스트할 정수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

*C* 가 공백 또는 가로 탭 문자의 특정 표현인 경우 이러한 각 루틴은 0이 아닌 값을 반환 하 고, 텍스트 줄 내에서 단어를 구분 하는 데 사용 되는 로캘별 문자 집합 중 하나입니다. **isblank** 는 *c* 가 공백 문자 (0x20) 또는 가로 탭 문자 (0x09) 인 경우 0이 아닌 값을 반환 합니다. **Isblank** 함수의 테스트 조건 결과는 로캘의 **LC_CTYPE** 범주 설정에 따라 달라 집니다. 자세한 내용은 [setlocale, _wsetlocale](setlocale-wsetlocale.md)를 참조 하세요. **_L** 접미사가 없는 이러한 함수 버전은 로캘 종속 동작에 현재 로캘을 사용 합니다. **_l** 접미사가 있는 버전은 전달 된 로캘을 대신 사용 한다는 점을 제외 하 고는 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

*c* 가 표준 공백 또는 가로 탭 문자에 해당 하는 와이드 문자인 경우 **iswblank** 는 0이 아닌 값을 반환 합니다.

*C* 가 EOF가 아니거나 0에서 0xff 사이 (포함) 범위 내에 있는 경우 **isblank** 및 **_isblank_l** 의 동작이 정의 되지 않습니다. 디버그 CRT 라이브러리가 사용 되 고 *c* 가 이러한 값 중 하나가 아니면 함수는 어설션을 발생 시킵니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istblank**|**isblank**|[_ismbcblank](ismbcgraph-functions.md)|**iswblank**|
|**_istblank_l**|**_isblank_l**|[_ismbcblank_l](ismbcgraph-functions.md)|**_iswblank_l**|

## <a name="remarks"></a>설명

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**isblank**|\<ctype.h>|
|**iswblank**|\<ctype.h> 또는 \<wchar.h>|
|**_isblank_l**|\<ctype.h>|
|**_iswblank_l**|\<ctype.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[문자 분류](../../c-runtime-library/character-classification.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[is, isw 루틴](../../c-runtime-library/is-isw-routines.md)<br/>
