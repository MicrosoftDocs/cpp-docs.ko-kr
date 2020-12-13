---
description: Isleadbyte, _isleadbyte_l에 대해 자세히 알아보세요.
title: isleadbyte, _isleadbyte_l
ms.date: 4/2/2020
api_name:
- _isleadbyte_l
- isleadbyte
- _o__isleadbyte_l
- _o_isleadbyte
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
- _istleadbyte
- _isleadbyte_l
- isleadbyte
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
ms.openlocfilehash: 544adda1b794db6a003e3ae7d51b15456574f875
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332657"
---
# <a name="isleadbyte-_isleadbyte_l"></a>isleadbyte, _isleadbyte_l

문자가 멀티바이트 문자의 선행 바이트인지 여부를 결정합니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>매개 변수

*c*<br/>
테스트할 정수입니다.

## <a name="return-value"></a>반환 값

**isleadbyte** 는 인수가 테스트 조건을 충족 하는 경우 0이 아닌 값을 반환 하 고 그렇지 않으면 0을 반환 합니다. "C" 로캘과 SBCS (싱글바이트 문자 집합) 로캘에서 **isleadbyte** 는 항상 0을 반환 합니다.

## <a name="remarks"></a>설명

**Isleadbyte** 매크로는 인수가 멀티 바이트 문자의 첫 번째 바이트인 경우 0이 아닌 값을 반환 합니다. **isleadbyte** 는-1 (**EOF**)에서 **UCHAR_MAX** (0xff) (포함) 사이의 모든 정수 인수에 대해 의미 있는 결과를 생성 합니다.

**Isleadbyte** 의 예상 인수 형식은입니다 **`int`** . 부호 있는 문자가 전달 되는 경우 컴파일러는 부호 확장을 통해 정수로 변환 하 여 예측할 수 없는 결과를 얻을 수 있습니다.

**_L** 접미사가 있는이 함수의 버전은 로캘 종속 동작에 현재 로캘 대신 전달 된 로캘을 사용 한다는 점을 제외 하 고는 동일 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|항상 false를 반환합니다.|**_isleadbyte**|항상 false를 반환합니다.|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[바이트 분류](../../c-runtime-library/byte-classification.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[_ismbb 루틴](../../c-runtime-library/ismbb-routines.md)<br/>
