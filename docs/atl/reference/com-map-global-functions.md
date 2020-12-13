---
description: '자세한 정보: COM 맵 전역 함수'
title: COM 맵 전역 함수
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: ee502a68a0a3b21849d2fabdadcc9ecbbcc1602d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141338"
---
# <a name="com-map-global-functions"></a>COM 맵 전역 함수

이러한 함수는 COM 맵 구현을 지원 `IUnknown` 합니다.

|함수|설명|
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|집계할 수 없는 개체의에 대 한 대리자입니다 `IUnknown` .|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|인터페이스를 비교 하기 위한 효율적인 코드를 생성 `IUnknown` 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="atlinternalqueryinterface"></a><a name="atlinternalqueryinterface"></a> 없음 Internalqueryinterface

요청된 인터페이스에 대한 포인터를 검색합니다.

```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>매개 변수

*pThis*<br/>
진행 에 노출 된 인터페이스의 COM 맵을 포함 하는 개체에 대 한 포인터입니다 `QueryInterface` .

*pEntries*<br/>
진행 `_ATL_INTMAP_ENTRY` 사용 가능한 인터페이스의 맵에 액세스 하는 구조체의 배열입니다.

*iid*<br/>
진행 요청 되는 인터페이스의 GUID입니다.

*ppvObject*<br/>
제한이 *Iid* 에 지정 된 인터페이스 포인터에 대 한 포인터 이거나, 인터페이스를 찾을 수 없는 경우 NULL입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

`AtlInternalQueryInterface`에서는 COM 맵 테이블의 인터페이스만 처리됩니다. 개체가 집계 된 경우는 `AtlInternalQueryInterface` 알 수 없는 외부에 위임 하지 않습니다. 매크로 [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) 또는 해당 변형 중 하나를 사용 하 여 COM 맵 테이블에 인터페이스를 입력할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

## <a name="inlineisequaliunknown"></a><a name="inlineisequaliunknown"></a> InlineIsEqualIUnknown

에 대 한 특수 테스트 사례에 대해이 함수를 호출 `IUnknown` 합니다.

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>매개 변수

*rguid1*<br/>
진행 비교할 GUID `IID_IUnknown` 입니다.

## <a name="see-also"></a>참조

[함수](../../atl/reference/atl-functions.md)<br/>
[COM 맵 매크로](../../atl/reference/com-map-macros.md)
