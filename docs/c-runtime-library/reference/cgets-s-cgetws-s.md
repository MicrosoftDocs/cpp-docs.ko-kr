---
description: '자세히 알아보기: _cgets_s, _cgetws_s'
title: _cgets_s, _cgetws_s
ms.date: 4/2/2020
api_name:
- _cgetws_s
- _cgets_s
- _o__cgets_s
- _o__cgetws_s
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
- api-ms-win-crt-conio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cgets_s
- cgets_s
- cgetws_s
- _cgetws_s
helpviewer_keywords:
- strings [C++], getting from console
- console, getting strings from
- _cgets_s function
- cget_s function
- _cgetws_s function
- cgetws_s function
ms.assetid: 38b74897-afe6-4dd9-a43f-36a3c0d72c5c
ms.openlocfilehash: 827f3c8b155f58fe13396f5dc0c66e8999b5f942
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275089"
---
# <a name="_cgets_s-_cgetws_s"></a>_cgets_s, _cgetws_s

콘솔에서 문자열을 가져옵니다. 이러한 버전의 [_cgets 및 _cgetws](../../c-runtime-library/cgets-cgetws.md)에는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 향상된 보안 기능이 포함되어 있습니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
errno_t _cgets_s(
   char *buffer,
   size_t numberOfElements,
   size_t *pSizeRead
);
errno_t _cgetws_s(
   wchar_t *buffer
   size_t numberOfElements,
   size_t *pSizeRead
);
template <size_t size>
errno_t _cgets_s(
   char (&buffer)[size],
   size_t *pSizeRead
); // C++ only
template <size_t size>
errno_t _cgetws_s(
   wchar_t (&buffer)[size],
   size_t *pSizeRead
); // C++ only
```

### <a name="parameters"></a>매개 변수

*버퍼*<br/>
데이터의 스토리지 위치입니다.

*이면 numberofelements 이벤트가*<br/>
단일 바이트 또는 와이드 문자 단위의 버퍼 크기이며, 읽을 수 있는 최대 문자 수이기도 합니다.

*pSizeRead*<br/>
실제로 읽은 문자 수입니다.

## <a name="return-value"></a>반환 값

성공할 경우 반환 값은 0이고, 그렇지 않고 오류가 발생할 경우 오류 코드를 반환합니다.

### <a name="error-conditions"></a>오류 조건

|*버퍼*|*이면 numberofelements 이벤트가*|*pSizeRead*|반환 값|*버퍼* 의 내용|
|--------------|------------------------|-----------------|------------|--------------------------|
|**NULL**|any|any|**EINVAL**|해당 없음|
|**NULL** 이 아님|0|any|**EINVAL**|수정 안 됨|
|**NULL** 이 아님|any|**NULL**|**EINVAL**|빈 문자열|

## <a name="remarks"></a>설명

**_cgets_s** 및 **_cgetws_s** 콘솔에서 문자열을 읽고 null 종결자를 사용 하 여 문자열을 *버퍼* 에 복사 합니다. **_cgetws_s** 은 함수의 와이드 문자 버전입니다. 문자 크기를 제외 하 고 이러한 두 함수의 동작은 동일 합니다. 읽을 문자열의 최대 크기는 *Numberofelements* 매개 변수로 전달 됩니다. 이 크기는 종료 null에 대한 추가 문자를 포함해야 합니다. 읽은 실제 문자 수는 *pSizeRead* 에 배치 됩니다.

작업 중이나 매개 변수의 유효성을 검사할 때 오류가 발생하면 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속 해 서 실행 하도록 허용 된 경우 **errno** 가 **EINVAL** 로 설정 되 고 **EINVAL** 이 반환 됩니다.

C++에서는 템플릿 오버로드를 통해 이러한 함수를 사용하는 것이 보다 간단해집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으므로 크기 인수를 지정할 필요가 없어지고 보안 수준이 낮은 기존 함수를 보안 수준이 높은 최신 함수로 자동으로 바꿀 수 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

이러한 함수의 디버그 라이브러리 버전은 먼저 0xFE를 사용 하 여 버퍼를 채웁니다. 이 동작을 사용하지 않으려면 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)를 사용하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cgetts_s**|**_cgets_s**|**_cgets_s**|**_cgetws_s**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_cgets_s**|\<conio.h>|
|**_cgetws_s**|\<conio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[콘솔 및 포트 i/o](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
