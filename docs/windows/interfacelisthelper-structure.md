---
title: InterfaceListHelper 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
dev_langs:
- C++
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 87516cf45a39602bea462b8e94f17d3ef64ad0eb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431621"
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

template <
   typename T0
>
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;
```

### <a name="parameters"></a>매개 변수

*T0*<br/>
템플릿 매개 변수 0 필요 합니다.

*T1*<br/>
템플릿 매개 변수 1에는 기본적으로 지정 되지 않았습니다.

*T2*<br/>
템플릿 매개 변수 2는 기본적으로 지정 되지 않았습니다. 세 번째 템플릿 매개 변수입니다.

*T3*<br/>
템플릿 매개 변수 3, 기본적으로 지정 되지 않았습니다.

*T4*<br/>
템플릿 매개 변수 4, 기본적으로 지정 되지 않았습니다.

*T5*<br/>
템플릿 매개 변수 5는 기본적으로 지정 되지 않았습니다.

*T6*<br/>
템플릿 매개 변수 6, 기본적으로 지정 되지 않았습니다.

*T7*<br/>
템플릿 매개 변수 7, 기본적으로 지정 되지 않았습니다.

*T8*<br/>
템플릿 매개 변수 8, 기본적으로 지정 되지 않았습니다.

*T9*<br/>
템플릿 매개 변수 9, 기본적으로 지정 되지 않았습니다.

## <a name="remarks"></a>설명

빌드는 `InterfaceList` 재귀적으로 지정 된 템플릿 매개 변수 인수를 적용 하 여 형식입니다.

**InterfaceListHelper** 템플릿은 템플릿 매개 변수를 사용 하 여 *T0* 의 첫 번째 데이터 멤버를 정의 하는 `InterfaceList` 구조 및 재귀적으로 적용 되는  **InterfaceListHelper** 나머지 모든 템플릿 매개 변수는 템플릿. **InterfaceListHelper** 나머지 템플릿 매개 변수가 없는 경우 중지 합니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|이름|설명|
|----------|-----------------|
|`TypeT`|InterfaceList 형식에 대 한 동의어입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층

`InterfaceListHelper`

## <a name="requirements"></a>요구 사항

**헤더:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>참고 항목

[Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)