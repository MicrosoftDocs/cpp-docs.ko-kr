---
title: isgraph, iswgraph, _isgraph_l, _iswgraph_l
ms.date: 11/04/2016
api_name:
- isgraph
- iswgraph
- _iswgraph_l
- _isgraph_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _isgraph_l
- _iswgraph_l
- _ismbcgraph_l
- Isgraph
- _istgraph_l
- _istgraph
- iswgraph
helpviewer_keywords:
- isgraph function
- _istgraph_l function
- istgraph function
- _isgraph_l function
- iswgraph function
- _iswgraph_l function
- _istgraph function
- _ismbcgraph_l function
ms.assetid: 531a5f34-4302-4d0a-8a4f-b7ea150ad941
ms.openlocfilehash: 88219ca6dc4218fc13f7d7c0b5f2ba399c07d501
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954871"
---
# <a name="isgraph-iswgraph-_isgraph_l-_iswgraph_l"></a>isgraph, iswgraph, _isgraph_l, _iswgraph_l

정수가 그래픽 문자를 나타내는지 여부를 확인합니다.

## <a name="syntax"></a>구문

```C
int isgraph(
   int c
);
int iswgraph(
   wint_t c
);
int _isgraph_l(
   int c,
   _locale_t locale
);
int _iswgraph_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*c*<br/>
테스트할 정수입니다.

## <a name="return-value"></a>반환 값

*C* 가 공백이 아닌 인쇄 가능한 문자의 특정 표현인 경우 이러한 각 루틴은 0이 아닌 값을 반환 합니다. *c* 가 공백이 아닌 인쇄 가능한 문자인 경우 **isgraph** 는 0이 아닌 값을 반환 합니다. *c* 가 와이드 문자 공간 이외의 인쇄 가능한 와이드 문자인 경우 **iswgraph** 는 0이 아닌 값을 반환 합니다. *C* 가 테스트 조건을 충족 하지 않는 경우 이러한 루틴은 각각 0을 반환 합니다.

**_L** 접미사가 있는 이러한 함수 버전은 로캘 종속 동작에 대해 현재 로캘 대신 전달 된 로캘을 사용 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

*C* 가 EOF가 아니거나 0에서 0xff 사이 (포함) 범위 내에 있는 경우 **isgraph** 및 **_isgraph_l** 의 동작이 정의 되지 않습니다. 디버그 CRT 라이브러리가 사용 되 고 *c* 가 이러한 값 중 하나가 아니면 함수는 어설션을 발생 시킵니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 루틴 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istgraph**|**isgraph**|[_ismbcgraph](ismbcgraph-functions.md)|**iswgraph**|
|**_istgraph_l**|**_isgraph_l**|[_ismbcgraph_l](ismbcgraph-functions.md)|**_iswgraph_l**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**isgraph**|\<ctype.h>|
|**iswgraph**|\<ctype.h> 또는 \<wchar.h>|
|**_isgraph_l**|\<ctype.h>|
|**_iswgraph_l**|\<ctype.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고자료

[문자 분류](../../c-runtime-library/character-classification.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[is, isw 루틴](../../c-runtime-library/is-isw-routines.md)<br/>
