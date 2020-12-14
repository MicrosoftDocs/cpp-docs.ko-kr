---
description: '자세한 정보: 연결 맵'
title: 연결 맵
ms.date: 11/04/2016
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: 61d2e7023ab97aa00952aee4786b34e60ba57af7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345253"
---
# <a name="connection-maps"></a>연결 맵

OLE 컨트롤은 다른 응용 프로그램에 인터페이스를 노출할 수 있습니다. 이러한 인터페이스는 컨테이너에서 해당 컨트롤에 대 한 액세스만 허용 합니다. OLE 컨트롤이 다른 OLE 개체의 외부 인터페이스에 액세스 하려는 경우에는 연결 지점을 설정 해야 합니다. 이 연결 지점을 사용 하면 이벤트 맵 또는 알림 함수와 같은 외부 디스패치 맵에 대 한 제어를 보낼 수 있습니다.

MFC 라이브러리는 연결 지점이 지원 되는 프로그래밍 모델을 제공 합니다. 이 모델에서 "연결 맵"은 OLE 컨트롤에 대 한 인터페이스 또는 연결 지점은 지정 하는 데 사용 됩니다. 연결 맵은 각 연결 지점에 대해 하나의 매크로를 포함 합니다. 연결 맵에 대 한 자세한 내용은 [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) 클래스를 참조 하세요.

일반적으로 컨트롤은 이벤트와 속성 알림에 대해 각각 하나씩 두 개의 연결 지점만 지원 합니다. 이러한 클래스는 기본 클래스에 의해 구현 `COleControl` 되며 컨트롤 작성기에서 추가 작업을 수행 하지 않아도 됩니다. 클래스에서 구현 하려는 추가 연결 지점은 수동으로 추가 해야 합니다. 연결 맵과 요소를 지원 하기 위해 MFC는 다음과 같은 매크로를 제공 합니다.

### <a name="connection-map-declaration-and-demarcation"></a>연결 맵 선언 및 경계

|Name|설명|
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|추가 연결 지점을 구현 하는 포함 클래스를 선언 합니다 (클래스 선언에 사용 되어야 함).|
|[END_CONNECTION_PART](#end_connection_part)|연결 지점의 선언을 끝냅니다 (클래스 선언에서 사용 되어야 함).|
|[CONNECTION_IID](#connection_iid)|컨트롤의 연결 지점에 대 한 인터페이스 ID를 지정 합니다.|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|클래스에서 연결 맵이 사용 됨을 선언 합니다 (클래스 선언에서 사용 되어야 함).|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|연결 맵의 정의를 시작 합니다 (클래스 구현에서 사용 되어야 함).|
|[END_CONNECTION_MAP](#end_connection_map)|연결 맵의 정의를 끝냅니다 (클래스 구현에서 사용 되어야 함).|
|[CONNECTION_PART](#connection_part)|컨트롤의 연결 맵에서 연결 지점을 지정 합니다.|

다음 함수는 연결을 사용 하 여 연결을 설정 하 고 연결을 끊을 때 싱크를 지원 합니다.

### <a name="initializationtermination-of-connection-points"></a>연결 지점의 초기화/종료

|Name|설명|
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|원본과 싱크 간에 연결을 설정 합니다.|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|소스와 싱크 간의 연결을 끊습니다.|

## <a name="begin_connection_part"></a><a name="begin_connection_part"></a> BEGIN_CONNECTION_PART

BEGIN_CONNECTION_PART 매크로를 사용 하 여 이벤트 및 속성 알림 연결 지점이 아닌 추가 연결 지점의 정의를 시작 합니다.

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
연결 지점이 있는 컨트롤 클래스의 이름을 지정 합니다.

*localClass*<br/>
연결 지점을 구현하는 로컬 클래스의 이름을 지정합니다.

### <a name="remarks"></a>설명

클래스의 멤버 함수를 정의 하는 선언 (.h) 파일에서 BEGIN_CONNECTION_PART 매크로를 사용 하 여 연결 지점을 시작한 다음, CONNECTION_IID 매크로 및 구현할 다른 모든 멤버 함수를 추가 하 고 END_CONNECTION_PART 매크로를 사용 하 여 연결 지점 맵을 완료 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="end_connection_part"></a><a name="end_connection_part"></a> END_CONNECTION_PART

연결 지점의 선언을 종료합니다.

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>매개 변수

*localClass*<br/>
연결 지점을 구현하는 로컬 클래스의 이름을 지정합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="connection_iid"></a><a name="connection_iid"></a> CONNECTION_IID

BEGIN_CONNECTION_PART와 END_CONNECTION_PART 매크로 사이를 사용 하 여 OLE 컨트롤에서 지 원하는 연결 지점의 인터페이스 ID를 정의 합니다.

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
연결 지점에서 호출 하는 인터페이스의 인터페이스 ID입니다.

### <a name="remarks"></a>설명

*Iid* 인수는 연결 지점이 연결 된 싱크에 대해 호출할 인터페이스를 식별 하는 데 사용 되는 인터페이스 ID입니다. 예를 들어:

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

인터페이스를 호출 하는 연결 지점을 지정 합니다 `ISinkInterface` .

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="declare_connection_map"></a><a name="declare_connection_map"></a> DECLARE_CONNECTION_MAP

`COleControl`프로그램의 각 파생 클래스는 연결 맵을 제공 하 여 컨트롤에서 지 원하는 추가 연결 요소를 지정할 수 있습니다.

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>설명

컨트롤에서 추가 요소를 지 원하는 경우 클래스 선언 끝에 DECLARE_CONNECTION_MAP 매크로를 사용 합니다. 그런 다음 클래스의 멤버 함수를 정의 하는 .cpp 파일에서 BEGIN_CONNECTION_MAP 매크로를 사용 하 여 각 컨트롤의 연결 점에 대 한 매크로를 CONNECTION_PART 하 고 END_CONNECTION_MAP 매크로를 사용 하 여 연결 맵의 끝을 선언 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="begin_connection_map"></a><a name="begin_connection_map"></a> BEGIN_CONNECTION_MAP

프로그램에서 각 `COleControl` 파생 클래스는 컨트롤을 지원하는 연결 포인트를 지정하기 위해 연결 맵을 제공할 수 있습니다.

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
이 연결을 매핑할 컨트롤 클래스의 이름을 지정합니다.

*theBase*<br/>
*Theclass* 의 기본 클래스 이름을 지정 합니다.

### <a name="remarks"></a>설명

구현 (. CPP) 파일을 사용 하 여 클래스의 멤버 함수를 정의 하 고 BEGIN_CONNECTION_MAP 매크로를 사용 하 여 연결 맵을 시작한 다음 [CONNECTION_PART](#connection_part) 매크로를 사용 하 여 각 연결 지점의 매크로 항목을 추가 합니다. 마지막으로 [END_CONNECTION_MAP](#end_connection_map) 매크로를 사용 하 여 연결 맵을 완료 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="end_connection_map"></a><a name="end_connection_map"></a> END_CONNECTION_MAP

연결 맵의 정의를 끝냅니다.

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="connection_part"></a><a name="connection_part"></a> CONNECTION_PART

OLE 컨트롤에 대 한 연결 지점을 특정 인터페이스 ID에 매핑합니다.

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
연결 지점이 있는 컨트롤 클래스의 이름을 지정 합니다.

*iid*<br/>
연결 지점에서 호출 하는 인터페이스의 인터페이스 ID입니다.

*localClass*<br/>
연결 지점을 구현하는 로컬 클래스의 이름을 지정합니다.

### <a name="remarks"></a>설명

예를 들어:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

인터페이스를 호출 하는 연결 지점을 사용 하 여 연결 맵을 구현 `IID_ISinkInterface` 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="afxconnectionadvise"></a><a name="afxconnectionadvise"></a> AfxConnectionAdvise

*PUnkSrc* 에 의해 지정 된 소스와 *pUnkSink* 에 의해 지정 된 싱크로 연결을 설정 하려면이 함수를 호출 합니다.

```
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD FAR* pdwCookie);
```

### <a name="parameters"></a>매개 변수

*pUnkSrc*<br/>
인터페이스를 호출 하는 개체에 대 한 포인터입니다.

*pUnkSink*<br/>
인터페이스를 구현 하는 개체에 대 한 포인터입니다.

*iid*<br/>
연결의 인터페이스 ID입니다.

*bRefCount*<br/>
TRUE로 설정 하면 연결을 만들 때 *pUnkSink* 의 참조 수가 증가 하는 것을 나타냅니다. FALSE는 참조 횟수를 증가 시킬 수 없음을 나타냅니다.

*pdwCookie*<br/>
연결 식별자가 반환 되는 DWORD에 대 한 포인터입니다. 연결을 끊을 때이 값을 *Dwcookie* 매개 변수로 전달 해야 합니다 `AfxConnectionUnadvise` .

### <a name="return-value"></a>반환 값

연결이 설정 된 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afxctl

## <a name="afxconnectionunadvise"></a><a name="afxconnectionunadvise"></a> AfxConnectionUnadvise

*PUnkSrc* 에 의해 지정 된 소스와 *pUnkSink* 에 의해 지정 된 싱크로 연결의 연결을 끊으려면이 함수를 호출 합니다.

```
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD dwCookie);
```

### <a name="parameters"></a>매개 변수

*pUnkSrc*<br/>
인터페이스를 호출 하는 개체에 대 한 포인터입니다.

*pUnkSink*<br/>
인터페이스를 구현 하는 개체에 대 한 포인터입니다.

*iid*<br/>
연결 지점 인터페이스의 인터페이스 ID입니다.

*bRefCount*<br/>
TRUE로 설정 하면 연결을 끊을 때 *pUnkSink* 참조 수가 감소 됩니다. FALSE는 참조 횟수를 감소할 수 없음을 나타냅니다.

*dwCookie*<br/>
에서 반환 하는 연결 식별자 `AfxConnectionAdvise` 입니다.

### <a name="return-value"></a>반환 값

연결이 끊어져 있는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afxctl

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
