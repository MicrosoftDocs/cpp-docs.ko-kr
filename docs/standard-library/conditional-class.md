---
description: '자세히 알아보기: 조건부 클래스'
title: conditional 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: f8edbd7341598957ecbe8b0822a832973f0e06a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324973"
---
# <a name="conditional-class"></a>conditional 클래스

지정된 조건에 따라 두 가지 형식 중 하나를 선택합니다.

## <a name="syntax"></a>구문

```cpp
template <bool B, class T1, class T2>
struct conditional;

template <bool _Test, class _T1, class _T2>
using conditional_t = typename conditional<_Test, _T1, _T2>::type;
```

### <a name="parameters"></a>매개 변수

*B*\
선택된 형식을 확인하는 값입니다.

*들은*\
B가 true인 경우의 형식 결과입니다.

*T*\
B가 false인 경우의 형식 결과입니다.

## <a name="remarks"></a>설명

B가로 계산 되 면 템플릿 멤버 typedef가 `conditional<B, T1, T2>::type` *T1* 로 평가 되  **`true`** 고 *b* 가로 계산 되 면 *T2* 로 계산 **`false`** 됩니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
