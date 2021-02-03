---
description: '자세한 내용은 _bstr_t:: operator!를 확인 하세요.'
title: '_bstr_t:: operator!'
ms.date: 02/02/2021
f1_keywords:
- _bstr_t::operator!
helpviewer_keywords:
- '! operator'
- operator!, bstr
- operator !, bstr
ms.openlocfilehash: 712aeafd26fda6c8291a54a9b897d31fa77ac02e
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522601"
---
# `_bstr_t::operator !`

**Microsoft 전용**

캡슐화 된이 NULL 문자열 인지 여부를 확인 합니다 `BSTR` .

## <a name="syntax"></a>구문

```cpp
bool operator!( ) const throw( );
```

## <a name="return-value"></a>Return Value

**`true`** 캡슐화 된 `BSTR` 가 NULL 문자열이 **`false`** 아닌 경우를 반환 합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[`_bstr_t` 클래스](../cpp/bstr-t-class.md)
