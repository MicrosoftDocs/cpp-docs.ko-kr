---
description: '자세히 알아보기: EnableIf 구조체'
title: EnableIf 구조체
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::EnableIf
helpviewer_keywords:
- EnableIf structure
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
ms.openlocfilehash: 098dd5fdc7e37a7754d7124eba3e146575c127be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272853"
---
# <a name="enableif-structure"></a>EnableIf 구조체

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <bool b, typename T = void>
struct EnableIf;

template <typename T>
struct EnableIf<true, T>;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
형식입니다.

*b*<br/>
부울 식입니다.

## <a name="remarks"></a>설명

첫 번째 템플릿 매개 변수가로 평가 될 경우 두 번째 템플릿 매개 변수로 지정 된 형식의 데이터 멤버를 정의 합니다 **`true`** .

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`type`|템플릿 매개 변수 *b* 가로 계산 **`true`** 되는 경우 부분 특수화는 데이터 멤버를 형식으로 정의 합니다 `type` `T` .|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`EnableIf`

## <a name="requirements"></a>요구 사항

**헤더:** internal. h

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL::D etails 네임 스페이스](microsoft-wrl-details-namespace.md)
