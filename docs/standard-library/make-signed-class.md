---
description: Make_signed 클래스에 대해 자세히 알아보세요.
title: make_signed 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_signed
helpviewer_keywords:
- make_signed class
- make_signed
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
ms.openlocfilehash: 2f11fe3223e6193613772d2c4abbf0182215a17d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277559"
---
# <a name="make_signed-class"></a>make_signed 클래스

형식을 만들거나 형식의 크기보다 크거나 같은 부호가 있는 가장 작은 형식을 만듭니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct make_signed;

template <class T>
using make_signed_t = typename make_signed<T>::type;
```

### <a name="parameters"></a>매개 변수

*트*\
수정할 형식입니다.

## <a name="remarks"></a>설명

형식 한정자의 인스턴스는가 true 인 경우 *T* 인 수정 된 형식을 보유 `is_signed<T>` 합니다. 그렇지 않은 경우 가장 작은 부호 없는 형식 `UT`이며, 여기서 `sizeof (T) <= sizeof (UT)`입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
