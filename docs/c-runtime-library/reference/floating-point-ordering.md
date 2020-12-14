---
description: '자세히 알아보기: isgreater, isgreaterequal, isgreater, islessequal, islessgreater, isgreater'
title: isgreater, isgreaterequal, isless, islessequal, islessgreater, isunordered
ms.date: 01/31/2019
f1_keywords:
- isgreater
- math/isgreater
- isgreaterequal
- math/isgreaterequal
- isless
- math/isless
- islessequal
- math/islessequal
- islessgreater
- math/islessgreater
- isunordered
- math/isunordered
helpviewer_keywords:
- isgreater function
- isgreaterequal function
- isless function
- islessequal function
- islessgreater function
- isunordered function
ms.openlocfilehash: 90e01de2caeb5a73b1b48a0c78678d975cdca6e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262973"
---
# <a name="isgreater-isgreaterequal-isless-islessequal-islessgreater-isunordered"></a>isgreater, isgreaterequal, isless, islessequal, islessgreater, isunordered

두 부동 소수점 값 간의 순서 관계를 결정 합니다.

## <a name="syntax"></a>구문

```C
int isgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isgreaterequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isless(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isunordered(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */
```

```C++
template <class FloatingType1, class FloatingType2>
inline bool isgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isgreaterequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isless(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isunordered(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>매개 변수

*x*, *y*<br/>
비교할 부동 소수점 값입니다.

## <a name="return-value"></a>반환 값

모든 비교에서 동일한 부호 비교는 동일 하 게 무한대. 음의 무한대는 유한 값 또는 양의 무한대 보다 낮습니다. 양의 무한대는 유한 값 또는 음의 무한대 보다 큽니다. 0은 부호에 관계 없이 동일 합니다. Nan는 다른 NaN을 포함 하 여 값 보다 작거나, 같거나, 커야 합니다.

인수가 NaN이 아니면 정렬 매크로 **isgreater**, **isgreater** 및  **islessequal** 가 0이 아닌 값을 반환 합니다 .이 값은 *x* 와 *y* 사이의 지정 된 정렬 관계가 true 인 경우에는 0이 아닌 값을 반환 합니다. 이러한 매크로는 두 인수 중 하나 또는 모두 Nan 이거나 정렬 관계가 false 인 경우 0을 반환 합니다. 함수 forms는 동일한 방식으로 동작 하지만 또는를 반환 합니다 **`true`** **`false`** .

**Islessgreater** 매크로는 *x* 와 *y* 가 nan이 아니고 *x* 가 *y* 보다 작거나 같은 경우 0이 아닌 값을 반환 합니다. 두 인수 중 하나 또는 둘 다 Nan 경우 0을 반환 하 고, 값이 같으면 0을 반환 합니다. 함수 폼은 동일한 방식으로 동작 하지만 또는를 반환 합니다 **`true`** **`false`** .

*X*, *y* 중 하나 또는 둘 다가 nan 경우 **isunordered** 지정 되지 않은 매크로는 0이 아닌 값을 반환 합니다. 그렇지 않으면 0을 반환합니다. 함수 폼은 동일한 방식으로 동작 하지만 또는를 반환 합니다 **`true`** **`false`** .

## <a name="remarks"></a>설명

이러한 비교 작업은 C로 컴파일될 때 매크로로 구현 되 고 c + +로 컴파일될 때 인라인 템플릿 함수로 구현 됩니다.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더(C)|필수 헤더(C++)|
|--------------|---------------------------|-------------------------------|
| **isgreater**, **isgreaterequal**, **isgreater**,<br/>**islessequal**, **islessgreater**, **isunordered** | \<math.h> | \<math.h> 또는 \<cmath> |

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
