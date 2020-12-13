---
description: '자세히 알아보기: isnormal'
title: isnormal
ms.date: 01/31/2019
f1_keywords:
- isnormal
- math/isnormal
helpviewer_keywords:
- isnormal function
ms.openlocfilehash: 3afae5196a7a6b2b149028ad347f95baa27b1544
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337756"
---
# <a name="isnormal"></a>isnormal

부동 소수점 값이 일반 값 인지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```C
int isnormal(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isnormal(
   FloatingType x
) throw(); /* C++-only function template */
```

### <a name="parameters"></a>매개 변수

*x*<br/>
테스트할 부동 소수점 값입니다.

## <a name="return-value"></a>반환 값

**isnormal** 은 0이 아닌 값 ( **`true`** c + + 코드의 경우  )을 반환 합니다. 그렇지 않은 경우 **isnormal** 은 0 ( **`false`** c + + 코드의 경우)을 반환 합니다.

## <a name="remarks"></a>설명

**isnormal** 은 c로 컴파일되는 매크로 이며 c + +로 컴파일될 때 인라인 함수 템플릿을 말합니다.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더(C)|필수 헤더(C++)|
|--------------|---------------------------|-------------------------------|
|**isnormal**|\<math.h>|\<math.h> 또는 \<cmath>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
