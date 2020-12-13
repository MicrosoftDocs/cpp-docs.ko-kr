---
description: '자세히 알아보기: CancelTransitionPolicy 열거형'
title: CancelTransitionPolicy 열거형
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
helpviewer_keywords:
- CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
ms.openlocfilehash: 8de995ed492f8f1260534b08b818b77d889d95fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344538"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy 열거형

비동기 작업의 상태를 완료 또는 오류로 전환 하려는 시도가 클라이언트에서 요청한 취소 됨 상태와 관련 하 여 동작 하는 방식을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
enum CancelTransitionPolicy;
```

## <a name="members"></a>멤버

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`RemainCanceled`|비동기 작업이 현재 클라이언트에서 요청 된 취소 된 상태 이면이는 완료 된 터미널 또는 오류 상태로 전환 하는 것과는 반대로 취소 된 상태를 유지 함을 나타냅니다.|
|`TransitionFromCanceled`|비동기 작업이 현재 클라이언트에서 요청한 취소 된 상태 이면이 플래그를 활용 하는 호출에 의해 결정 된 대로 상태가 취소 됨 상태에서 완료 됨 또는 오류의 터미널 상태로 전환 되어야 함을 나타냅니다.|

## <a name="requirements"></a>요구 사항

**헤더:** async. h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL 네임 스페이스](microsoft-wrl-namespace.md)
