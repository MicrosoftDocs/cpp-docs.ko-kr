---
description: '자세한 정보: 연결 지점 매크로'
title: 연결 지점 매크로
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
ms.openlocfilehash: bcb021abe128e15a598f485ab0c0a32a01f90327
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141130"
---
# <a name="connection-point-macros"></a>연결 지점 매크로

이러한 매크로는 연결 지점 맵과 항목을 정의 합니다.

|매크로|설명|
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|연결 지점 맵 항목의 시작을 표시 합니다.|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|연결 지점이 맵에 들어갑니다.|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) CONNECTION_POINT_ENTRY와 유사 하지만 iid에 대 한 포인터를 사용 합니다.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|연결 지점 맵 항목의 끝을 표시 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="begin_connection_point_map"></a><a name="begin_connection_point_map"></a> BEGIN_CONNECTION_POINT_MAP

연결 지점 맵 항목의 시작을 표시 합니다.

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>매개 변수

*x*<br/>
진행 연결 지점이 포함 된 클래스의 이름입니다.

### <a name="remarks"></a>설명

BEGIN_CONNECTION_POINT_MAP 매크로를 사용 하 여 연결 지점 맵을 시작 하 고, [CONNECTION_POINT_ENTRY](#connection_point_entry) 매크로를 사용 하 여 각 연결 지점에 대 한 항목을 추가 하 고, [END_CONNECTION_POINT_MAP](#end_connection_point_map) 매크로를 사용 하 여 맵을 완료 합니다.

ATL의 연결 점에 대 한 자세한 내용은 [연결 요소](../../atl/atl-connection-points.md)문서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

## <a name="connection_point_entry-and-connection_point_entry_p"></a><a name="connection_point_entry"></a> CONNECTION_POINT_ENTRY 및 CONNECTION_POINT_ENTRY_P

지정 된 인터페이스의 연결 지점을 연결 지점 맵에 입력 하 여 액세스할 수 있도록 합니다.

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 연결 지점 맵에 추가 되는 인터페이스의 GUID입니다.

*piid*<br/>
진행 Adde 중인 인터페이스의 GUID에 대 한 포인터입니다.

### <a name="remarks"></a>설명

맵의 연결 지점 항목은 [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)에서 사용 됩니다. 연결 지점 맵을 포함 하는 클래스는에서 상속 해야 합니다 `IConnectionPointContainerImpl` .

[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) 매크로를 사용 하 여 연결 지점 맵을 시작 하 고, CONNECTION_POINT_ENTRY 매크로를 사용 하 여 각 연결 지점에 대 한 항목을 추가 하 고, [END_CONNECTION_POINT_MAP](#end_connection_point_map) 매크로를 사용 하 여 맵을 완료 합니다.

ATL의 연결 점에 대 한 자세한 내용은 [연결 요소](../../atl/atl-connection-points.md)문서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

## <a name="end_connection_point_map"></a><a name="end_connection_point_map"></a> END_CONNECTION_POINT_MAP

연결 지점 맵 항목의 끝을 표시 합니다.

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>설명

[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) 매크로를 사용 하 여 연결 지점 맵을 시작 하 고, [CONNECTION_POINT_ENTRY](#connection_point_entry) 매크로를 사용 하 여 각 연결 지점에 대 한 항목을 추가 하 고, END_CONNECTION_POINT_MAP 매크로를 사용 하 여 맵을 완료 합니다.

ATL의 연결 점에 대 한 자세한 내용은 [연결 요소](../../atl/atl-connection-points.md)문서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)<br/>
[연결 지점 전역 함수](../../atl/reference/connection-point-global-functions.md)
