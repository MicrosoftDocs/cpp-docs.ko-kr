---
description: '자세히 알아보기: TerminateMap 함수'
title: TerminateMap 함수
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 919759d0b4b7f67cf3aff83c3e83678860d0badc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135065"
---
# <a name="terminatemap-function"></a>TerminateMap 함수

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
inline bool TerminateMap(
   _In_ ModuleBase *module,
   _In_opt_z_ const wchar_t *serverName,
    bool forceTerminate) throw()
```

### <a name="parameters"></a>매개 변수

*모듈*<br/>
[모듈](module-class.md)입니다.

*serverName*<br/>
매개 변수 *모듈로* 지정 된 모듈에 있는 클래스 팩터리의 하위 집합 이름입니다.

*forceTerminate*<br/>
**`true`** 활성 상태에 관계 없이 클래스 팩터리를 종료 하려면 **`false`** 팩터리가 활성 상태인 경우 클래스 팩터리를 종료 하지 않으려면입니다.

## <a name="return-value"></a>반환 값

**`true`** 모든 클래스 팩터리가 종료 되었으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="remarks"></a>설명

지정 된 모듈에서 클래스 팩터리를 종료 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** module .h

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL::D etails 네임 스페이스](microsoft-wrl-details-namespace.md)
