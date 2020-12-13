---
description: '자세한 정보: isinf'
title: isinf
ms.date: 01/31/2019
f1_keywords:
- isinf
- math/isinf
helpviewer_keywords:
- isinf function
ms.openlocfilehash: f174855ddbb8cc43fd7338d4254c0f03bf53967d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332645"
---
# <a name="isinf"></a>isinf

부동 소수점 값이 무한대 인지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```C
int isinf(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isinf(
   FloatingType x
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>매개 변수

*x*<br/>
테스트할 부동 소수점 값입니다.

## <a name="return-value"></a>반환 값

**isinf** 는 **`true`** 인수 *x* 가 양의 무한대 또는 음의 무한대 인 경우 0이 아닌 값 (c + + 코드의 경우)을 반환 합니다. **isinf** 는 인수가 유한 또는 NAN 인 경우 0을 반환 합니다 ( **`false`** c + + 코드의 경우). Normal 및 subnormal 부동 소수점 값은 모두 한정 된 것으로 간주 됩니다.

## <a name="remarks"></a>설명

**isinf** 는 c로 컴파일될 때 매크로 이며 c + +로 컴파일된 인라인 템플릿 함수입니다.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더(C)|필수 헤더(C++)|
|--------------|---------------------------|-------------------------------|
|**isinf**|\<math.h>|\<math.h> 또는 \<cmath>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
