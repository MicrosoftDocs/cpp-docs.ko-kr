---
description: '자세히 알아보기: CConnectionPoint 클래스'
title: CConnectionPoint 클래스
ms.date: 11/04/2016
f1_keywords:
- CConnectionPoint
- AFXDISP/CConnectionPoint
- AFXDISP/CConnectionPoint::CConnectionPoint
- AFXDISP/CConnectionPoint::GetConnections
- AFXDISP/CConnectionPoint::GetContainer
- AFXDISP/CConnectionPoint::GetIID
- AFXDISP/CConnectionPoint::GetMaxConnections
- AFXDISP/CConnectionPoint::GetNextConnection
- AFXDISP/CConnectionPoint::GetStartPosition
- AFXDISP/CConnectionPoint::OnAdvise
- AFXDISP/CConnectionPoint::QuerySinkInterface
helpviewer_keywords:
- CConnectionPoint [MFC], CConnectionPoint
- CConnectionPoint [MFC], GetConnections
- CConnectionPoint [MFC], GetContainer
- CConnectionPoint [MFC], GetIID
- CConnectionPoint [MFC], GetMaxConnections
- CConnectionPoint [MFC], GetNextConnection
- CConnectionPoint [MFC], GetStartPosition
- CConnectionPoint [MFC], OnAdvise
- CConnectionPoint [MFC], QuerySinkInterface
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
ms.openlocfilehash: 62525428d8f9bf5303f379140837d75e53cbb387
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227847"
---
# <a name="cconnectionpoint-class"></a>CConnectionPoint 클래스

"연결점"이라고 하는 다른 OLE 개체와 통신하는 데 사용하는 특별한 형식의 인터페이스를 정의합니다.

## <a name="syntax"></a>구문

```
class CConnectionPoint : public CCmdTarget
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|`CConnectionPoint` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CConnectionPoint:: GetConnections](#getconnections)|연결 맵의 모든 연결점을 검색 합니다.|
|[CConnectionPoint:: GetContainer](#getcontainer)|연결 맵을 소유 하는 컨트롤의 컨테이너를 검색 합니다.|
|[CConnectionPoint:: GetIID](#getiid)|연결 지점의 인터페이스 ID를 검색 합니다.|
|[CConnectionPoint:: GetMaxConnections](#getmaxconnections)|컨트롤에서 지 원하는 최대 연결 지점의 수를 검색 합니다.|
|[CConnectionPoint::GetNextConnection](#getnextconnection)|*Pos* 에서 connection 요소에 대 한 포인터를 검색 합니다.|
|[CConnectionPoint:: GetStartPosition](#getstartposition)|호출에 전달 될 수 있는 위치 값을 반환 하 여 지도 반복을 시작 `GetNextConnection` 합니다.|
|[CConnectionPoint:: OnAdvise](#onadvise)|연결을 설정 하거나 중단할 때 프레임 워크에서 호출 됩니다.|
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|요청 된 싱크 인터페이스에 대 한 포인터를 검색 합니다.|

## <a name="remarks"></a>설명

OLE 컨트롤의 기능을 구현 하 고 노출 하는 데 사용 되는 일반적인 OLE 인터페이스와 달리 연결 지점은 이벤트 발생 및 변경 알림과 같은 다른 개체에 대 한 작업을 시작할 수 있는 송신 인터페이스를 구현 합니다.

연결은 "원본" 이라는 인터페이스를 호출 하는 개체와 인터페이스를 구현 하는 개체 ("싱크") 라는 두 부분으로 구성 됩니다. 원본에서 연결 지점을 노출 하 여 싱크는 자신에 대 한 연결을 설정할 수 있습니다. 원본 개체는 연결 지점 메커니즘을 통해 멤버 함수 집합의 싱크 구현에 대 한 포인터를 가져옵니다. 예를 들어 싱크에 의해 구현 되는 이벤트를 발생 시키려면 소스가 싱크의 구현에 적절 한 메서드를 호출할 수 있습니다.

기본적으로 `COleControl` 파생 클래스는 이벤트와 속성 변경 알림에 대 한 두 개의 연결점을 구현 합니다. 이러한 연결은 이벤트를 발생 시키고 속성 값이 변경 될 때 싱크 (예: 컨트롤의 컨테이너)에 알리기 위해 각각 사용 됩니다. 추가 연결 지점은 구현 하기 위해 OLE 컨트롤에 대 한 지원도 제공 합니다. 컨트롤 클래스에서 구현 되는 각 추가 연결 지점에 대해 연결 지점을 구현 하는 "연결 부분"을 선언 해야 합니다. 하나 이상의 연결 지점은 구현 하는 경우 컨트롤 클래스에서 단일 "연결 맵"도 선언 해야 합니다.

다음 예제에서는 두 가지 코드 조각으로 구성 된 간단한 연결 맵과 OLE 컨트롤에 대 한 하나의 연결 지점을 보여 줍니다 `Sample` . 첫 번째 부분은 연결 맵과 점을 선언 하 고 두 번째는이 맵과 점을 구현 합니다. 첫 번째 조각은 컨트롤 클래스의 선언에서 섹션 아래에 삽입 됩니다 **`protected`** .

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

BEGIN_CONNECTION_PART 및 END_CONNECTION_PART 매크로는 `XSampleConnPt` `CConnectionPoint` 이 특정 연결 지점을 구현 하는 포함 클래스 (에서 파생 됨)를 선언 합니다. `CConnectionPoint`멤버 함수를 재정의 하거나 고유한 멤버 함수를 추가 하려면 이러한 두 매크로 사이에 멤버 함수를 선언 합니다. 예를 들어 CONNECTION_IID 매크로는 `CConnectionPoint::GetIID` 두 매크로 사이에 배치 될 때 멤버 함수를 재정의 합니다.

두 번째 코드 조각이 구현 파일 ()에 삽입 됩니다. CPP)를 제어 합니다. 이 코드는 추가 연결 지점을 포함 하는 연결 맵을 구현 합니다 `SampleConnPt` .

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

이러한 코드 조각이 삽입 되 면 샘플 OLE 컨트롤은 인터페이스의 연결 지점을 노출 합니다 `ISampleSink` .

일반적으로 연결 지점은 동일한 인터페이스에 연결 된 여러 싱크에 브로드캐스트할 수 있는 "멀티 캐스팅"을 지원 합니다. 다음 코드 조각에서는 연결 지점에서 각 싱크를 반복 하 여 멀티 캐스팅을 수행 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

이 예에서는를 호출 하 여 연결 지점에서 현재 연결 집합을 검색 `SampleConnPt` `CConnectionPoint::GetConnections` 합니다. 그런 다음 `ISampleSink::SinkFunc` 모든 활성 연결에 대 한 연결 및 호출을 반복 합니다.

사용에 대 한 자세한 내용은 `CConnectionPoint` [연결 요소](../../mfc/connection-points.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="cconnectionpointcconnectionpoint"></a><a name="cconnectionpoint"></a> CConnectionPoint::CConnectionPoint

`CConnectionPoint` 개체를 생성합니다.

```
CConnectionPoint();
```

## <a name="cconnectionpointgetconnections"></a><a name="getconnections"></a> CConnectionPoint:: GetConnections

연결 지점에 대 한 모든 활성 연결을 검색 하려면이 함수를 호출 합니다.

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>반환 값

활성 연결 (싱크)의 배열에 대 한 포인터입니다. 배열의 일부 포인터는 NULL 일 수 있습니다. 이 배열에서 NULL이 아닌 각 포인터는 캐스트 연산자를 사용 하 여 싱크 인터페이스에 대 한 포인터로 안전 하 게 변환할 수 있습니다.

## <a name="cconnectionpointgetcontainer"></a><a name="getcontainer"></a> CConnectionPoint:: GetContainer

연결 지점에 대 한를 검색 하기 위해 프레임 워크에서 호출 `IConnectionPointContainer` 됩니다.

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>반환 값

성공 하면 컨테이너에 대 한 포인터이 고, 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 함수는 일반적으로 BEGIN_CONNECTION_PART 매크로를 통해 구현 됩니다.

## <a name="cconnectionpointgetiid"></a><a name="getiid"></a> CConnectionPoint:: GetIID

연결 지점의 인터페이스 ID를 검색 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>반환 값

연결 지점의 인터페이스 ID에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 연결 지점에 대 한 인터페이스 ID를 반환 하려면이 함수를 재정의 합니다.

## <a name="cconnectionpointgetmaxconnections"></a><a name="getmaxconnections"></a> CConnectionPoint:: GetMaxConnections

연결 지점에서 지원 되는 최대 연결 수를 검색 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>반환 값

컨트롤에서 지 원하는 최대 연결 수입니다. 제한이 없는 경우에는-1입니다.

### <a name="remarks"></a>설명

기본 구현에서는 제한 없음을 나타내는-1을 반환 합니다.

컨트롤에 연결할 수 있는 싱크 수를 제한 하려면이 함수를 재정의 합니다.

## <a name="cconnectionpointgetnextconnection"></a><a name="getnextconnection"></a> CConnectionPoint::GetNextConnection

*Pos* 에서 connection 요소에 대 한 포인터를 검색 합니다.

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
이전 `GetNextConnection` 또는 [Getstartposition](#getstartposition) 호출에서 반환 된 위치 값에 대 한 참조를 지정 합니다.

### <a name="return-value"></a>반환 값

*Pos* 에 지정 된 연결 요소 또는 NULL에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 함수는 연결 맵의 모든 요소를 반복 하는 데 가장 유용 합니다. 반복 하는 경우이 함수에서 반환 된 Null을 건너뜁니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

## <a name="cconnectionpointgetstartposition"></a><a name="getstartposition"></a> CConnectionPoint:: GetStartPosition

[GetNextConnection](#getnextconnection) 호출에 전달 될 수 있는 위치 값을 반환 하 여 map 반복을 시작 합니다.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>반환 값

지도를 반복 하기 위한 시작 위치를 나타내는 위치 값입니다. 또는 map이 비어 있으면 NULL입니다.

### <a name="remarks"></a>설명

반복 시퀀스를 예측할 수 없습니다. 따라서 "맵의 첫 번째 요소"는 특별 한 의미가 없습니다.

### <a name="example"></a>예제

  [CConnectionPoint:: GetNextConnection](#getnextconnection)의 예제를 참조 하세요.

## <a name="cconnectionpointonadvise"></a><a name="onadvise"></a> CConnectionPoint:: OnAdvise

연결이 설정 되거나 끊어질 때 프레임 워크에서 호출 됩니다.

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>매개 변수

*bAdvise*<br/>
연결이 설정 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

기본 구현은 아무 작업도 수행하지 않습니다.

싱크가 연결 지점에 연결 하거나 연결을 끊을 때 알림을 표시 하려면이 함수를 재정의 합니다.

## <a name="cconnectionpointquerysinkinterface"></a><a name="querysinkinterface"></a> CConnectionPoint::QuerySinkInterface

요청 된 싱크 인터페이스에 대 한 포인터를 검색 합니다.

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>매개 변수

*pUnkSink*<br/>
요청 된 싱크 인터페이스의 식별자입니다.

*ppInterface*<br/>
*PUnkSink* 로 식별 되는 인터페이스 포인터에 대 한 포인터입니다. 개체가이 인터페이스를 지원 하지 않으면 \* *PPINTERFACE* 가 NULL로 설정 됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="see-also"></a>참고 항목

[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
