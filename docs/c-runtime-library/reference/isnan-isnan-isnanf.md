---
description: '자세한 정보: isnan, _isnan, _isnanf'
title: isnan, _isnan, _isnanf
ms.date: 01/31/2019
api_name:
- _isnan
- _isnanf
- isnan
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
ms.openlocfilehash: 819b53740c6717f0ba8d18376a38c91c80ee03c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211247"
---
# <a name="isnan-_isnan-_isnanf"></a>isnan, _isnan, _isnanf

부동 소수점 값이 NAN(숫자가 아님)인지를 테스트합니다.

## <a name="syntax"></a>구문

```C
int isnan(
   /* floating-point */ x
); /* C-only macro */

int _isnan(
   double x
);

int _isnanf(
   float x
); /* x64 only */

template <class T>
bool isnan(
   T x
) throw(); /* C++ only */
```

### <a name="parameters"></a>매개 변수

*x*<br/>
테스트할 부동 소수점 값입니다.

## <a name="return-value"></a>반환 값

C에서 **isnan** 매크로와 **_isnan** 및 **_ISNANF** 함수는 *x* 인수가 NAN 인 경우 0이 아닌 값을 반환 합니다. 그렇지 않으면 0을 반환 합니다.

C + +에서 **isnan** 템플릿 함수는 **`true`** *x* 인수가 NaN 이면를 반환 하 고 그렇지 않으면를 반환 **`false`** 합니다.

## <a name="remarks"></a>설명

NaN 값은 다른 NaN 값과 동일 하 게 비교 되지 않으므로 이러한 함수 또는 매크로 중 하나를 사용 하 여 검색 해야 합니다. NaN은 부동 소수점 연산 결과를 지정 된 형식에 대 한 IEEE-754 부동 소수점 형식으로 표현할 수 없는 경우에 생성 됩니다. 출력에 NaN이 표시 되는 방법에 대 한 자세한 내용은 [printf](printf-printf-l-wprintf-wprintf-l.md)를 참조 하세요.

C + +로 컴파일될 때 **isnan** 매크로가 정의 되어 있지 않고 **isnan** 템플릿 함수가 정의 됩니다. 매크로와 동일한 방식으로 동작 하지만 정수 대신 형식의 값을 반환 합니다 **`bool`** .

**_Isnan** 및 **_Isnanf** 함수는 Microsoft 전용입니다. **_Isnanf** 함수는 x 64 용으로 컴파일된 경우에만 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더(C)|필수 헤더(C++)|
|-------------|---------------------------|-------------------------------|
|**isnan**, **_isnanf**|\<math.h>|\<math.h> 또는 \<cmath>|
|**_isnan**|\<float.h>|\<float.h> 또는 \<cfloat>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
