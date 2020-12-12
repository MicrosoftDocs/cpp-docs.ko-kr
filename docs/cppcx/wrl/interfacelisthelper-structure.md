---
description: '자세히 알아보기: InterfaceListHelper Structure'
title: InterfaceListHelper 구조체
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
ms.openlocfilehash: ca9e13e66acb6f27fba76a7653388305c57146dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249804"
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper 구조체

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <
    typename T0,
    typename T1 = Nil,
    typename T2 = Nil,
    typename T3 = Nil,
    typename T4 = Nil,
    typename T5 = Nil,
    typename T6 = Nil,
    typename T7 = Nil,
    typename T8 = Nil,
    typename T9 = Nil
>
struct InterfaceListHelper;

template <typename T0>
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;
```

### <a name="parameters"></a>매개 변수

*T0*<br/>
필요한 템플릿 매개 변수 0입니다.

*T1*<br/>
기본적으로 지정 되지 않은 템플릿 매개 변수 1입니다.

*T2*<br/>
기본적으로 지정 되지 않은 템플릿 매개 변수 2입니다. 세 번째 템플릿 매개 변수입니다.

*T3*<br/>
기본적으로 지정 되지 않은 템플릿 매개 변수 3입니다.

*T4*<br/>
기본적으로 지정 되지 않은 템플릿 매개 변수 4입니다.

*T5*<br/>
기본적으로 지정 되지 않은 템플릿 매개 변수 5입니다.

*T6*<br/>
기본적으로 지정 되지 않은 템플릿 매개 변수 6입니다.

*T7*<br/>
기본적으로 지정 되지 않은 템플릿 매개 변수 7입니다.

*T8*<br/>
기본적으로 지정 되지 않은 템플릿 매개 변수 8입니다.

*T9*<br/>
기본적으로 지정 되지 않은 템플릿 매개 변수 9입니다.

## <a name="remarks"></a>설명

지정 된 `InterfaceList` 템플릿 매개 변수 인수를 재귀적으로 적용 하 여 형식을 빌드합니다.

**InterfaceListHelper** 템플릿에서는 템플릿 매개 변수 *T0* 를 사용 하 여 구조체의 첫 번째 데이터 멤버를 정의한 `InterfaceList` 다음, 나머지 템플릿 매개 변수에 **InterfaceListHelper** 템플릿을 재귀적으로 적용 합니다. 남아 있는 템플릿 매개 변수가 없으면 **InterfaceListHelper** 이 중지 됩니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`TypeT`|[인터페이스 목록] 형식의 동의어입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`InterfaceListHelper`

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL::D etails 네임 스페이스](microsoft-wrl-details-namespace.md)
