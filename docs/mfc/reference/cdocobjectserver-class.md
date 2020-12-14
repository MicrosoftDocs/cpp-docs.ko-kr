---
description: '자세히 알아보기: CDocObjectServer 클래스'
title: CDocObjectServer 클래스
ms.date: 09/12/2018
f1_keywords:
- CDocObjectServer
- AFXDOCOB/CDocObjectServer
- AFXDOCOB/CDocObjectServer::CDocObjectServer
- AFXDOCOB/CDocObjectServer::ActivateDocObject
- AFXDOCOB/CDocObjectServer::OnActivateView
- AFXDOCOB/CDocObjectServer::OnApplyViewState
- AFXDOCOB/CDocObjectServer::OnSaveViewState
helpviewer_keywords:
- CDocObjectServer [MFC], CDocObjectServer
- CDocObjectServer [MFC], ActivateDocObject
- CDocObjectServer [MFC], OnActivateView
- CDocObjectServer [MFC], OnApplyViewState
- CDocObjectServer [MFC], OnSaveViewState
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
ms.openlocfilehash: 5a87363fef66a4819fc8efd504da96398cf3c89e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184948"
---
# <a name="cdocobjectserver-class"></a>CDocObjectServer 클래스

일반 `COleDocument` 서버를 전체 DocObject 서버로 만드는 데 필요한 추가 OLE 인터페이스( `IOleDocument`, `IOleDocumentView`, `IOleCommandTarget`, 및 `IPrint`)를 구현합니다.

## <a name="syntax"></a>구문

```
class CDocObjectServer : public CCmdTarget
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDocObjectServer:: CDocObjectServer](#cdocobjectserver)|`CDocObjectServer` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDocObjectServer:: Docobject](#activatedocobject)|문서 개체 서버를 활성화 하지만 표시 하지는 않습니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CDocObjectServer:: OnActivateView](#onactivateview)|DocObject 뷰를 표시 합니다.|
|[CDocObjectServer:: OnApplyViewState](#onapplyviewstate)|DocObject 뷰의 상태를 복원 합니다.|
|[CDocObjectServer:: OnSaveViewState](#onsaveviewstate)|DocObject 뷰의 상태를 저장 합니다.|

## <a name="remarks"></a>설명

`CDocObjectServer` 는에서 파생 되며 `CCmdTarget` `COleServerDoc` 인터페이스를 노출 하는 데와 긴밀 하 게 연동 됩니다.

DocObject 서버 문서는 DocObject 항목에 대 한 서버 인터페이스를 나타내는 [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) 개체를 포함할 수 있습니다.

DocObject 서버를 사용자 지정 하려면에서 고유한 클래스를 파생 하 `CDocObjectServer` 고 해당 뷰 설정 함수, [Onactivateview](#onactivateview), [Onactivateview](#onapplyviewstate)및 [onactivateview](#onsaveviewstate)를 재정의 합니다. 프레임 워크 호출에 대 한 응답으로 클래스의 새 인스턴스를 제공 해야 합니다.

DocObjects에 대 한 자세한 내용은 *MFC 참조* 의 [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) 및 [COleCmdUI](../../mfc/reference/colecmdui-class.md) 를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocObjectServer`

## <a name="requirements"></a>요구 사항

**헤더:** afxdocob

## <a name="cdocobjectserveractivatedocobject"></a><a name="activatedocobject"></a> CDocObjectServer:: Docobject

문서 개체 서버를 활성화 (표시 하지 않음) 하려면이 함수를 호출 합니다.

```cpp
void ActivateDocObject();
```

### <a name="remarks"></a>설명

`ActivateDocObject` 는 `IOleDocumentSite` 의 `ActivateMe` 메서드를 호출 하지만 뷰를 설정 하 고 표시 하는 방법에 대 한 특정 지침이 [CDocObjectServer:: sign-on view](#onactivateview)에 대 한 호출에 제공 될 때까지 대기 하므로 뷰를 표시 하지 않습니다.

함께를 `ActivateDocObject` `OnActivateView` 활성화 하 고 docobject 뷰를 표시 합니다. DocObject 활성화는 다른 종류의 OLE 내부 활성화와 다릅니다. DocObject 활성화는 내부 해치 테두리와 개체 장식 (예: 크기 조정 핸들)의 표시를 우회 하 고, 개체 익스텐트 함수를 무시 하 고, 뷰 사각형 안에 그리기를 그리는 것과는 반대로 (일반적인 내부 활성화의 경우 처럼) 스크롤 막대를 그립니다.

## <a name="cdocobjectservercdocobjectserver"></a><a name="cdocobjectserver"></a> CDocObjectServer:: CDocObjectServer

`CDocObjectServer` 개체를 생성하고 초기화합니다.

```
explicit CDocObjectServer(
    COleServerDoc* pOwner,
    LPOLEDOCUMENTSITE pDocSite = NULL);
```

### <a name="parameters"></a>매개 변수

*pOwner*<br/>
DocObject server에 대 한 클라이언트 사이트 문서에 대 한 포인터입니다.

*pDocSite*<br/>
컨테이너에 의해 구현 되는 인터페이스에 대 한 포인터 `IOleDocumentSite` 입니다.

### <a name="remarks"></a>설명

DocObject가 활성 상태 이면 클라이언트 사이트 OLE 인터페이스 ()를 `IOleDocumentSite` 사용 하 여 docobject 서버가 클라이언트 (컨테이너)와 통신할 수 있습니다. DocObject 서버를 활성화 하면 먼저 컨테이너에서 인터페이스를 구현 하는지 확인 `IOleDocumentSite` 합니다. 이 경우 [COleServerDoc:: GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver) 를 호출 하 여 컨테이너가 DocObjects를 지원 하는지 확인 합니다. 기본적으로는 `GetDocObjectServer` NULL을 반환 합니다. `COleServerDoc::GetDocObjectServer` `CDocObjectServer` 컨테이너 및 해당 인터페이스에 대 한 포인터를 `COleServerDoc` 생성자에 대 한 인수로 사용 하 여 고유한 새 개체 또는 파생 개체를 생성 하려면를 재정의 해야 합니다 `IOleDocumentSite` .

## <a name="cdocobjectserveronactivateview"></a><a name="onactivateview"></a> CDocObjectServer:: OnActivateView

이 함수를 호출 하 여 DocObject 뷰를 표시 합니다.

```
virtual HRESULT OnActivateView();
```

### <a name="return-value"></a>반환 값

오류 또는 경고 값을 반환 합니다. 성공 하면 기본적으로 NOERROR를 반환 합니다. 그렇지 않으면 E_FAIL 합니다.

### <a name="remarks"></a>설명

이 함수는 내부 프레임 창을 만들고, 뷰 내에 스크롤 막대를 그리고, 서버가 컨테이너와 공유 하는 메뉴를 설정 하 고, 프레임 컨트롤을 추가 하 고, 활성 개체를 설정 하 고, 마지막으로 내부 프레임 창을 표시 하 고 포커스를 설정 합니다.

## <a name="cdocobjectserveronapplyviewstate"></a><a name="onapplyviewstate"></a> CDocObjectServer:: OnApplyViewState

DocObject 뷰의 상태를 복원 하려면이 함수를 재정의 합니다.

```
virtual void OnApplyViewState(CArchive& ar);
```

### <a name="parameters"></a>매개 변수

*ar*<br/>
`CArchive`뷰 상태를 serialize 할 개체입니다.

### <a name="remarks"></a>설명

이 함수는 뷰가 인스턴스화된 후 처음으로 표시 될 때 호출 됩니다. `OnApplyViewState``CArchive` [Onsaveviewstate](#onsaveviewstate)를 사용 하 여 이전에 저장 한 개체의 데이터에 따라 자신을 다시 초기화 하도록 지시 합니다. `CArchive`컨테이너에서 뷰 상태 데이터를 해석 하려고 시도 하지 않으므로 뷰가 개체의 데이터 유효성을 검사 해야 합니다.

를 사용 `OnSaveViewState` 하 여 보기 상태와 관련 한 영구 정보를 저장할 수 있습니다. 을 재정의 하 여 정보를 저장 하는 경우를 재정의 하 여 `OnSaveViewState` `OnApplyViewState` 해당 정보를 읽고 새로 활성화 될 때 보기에 적용할 수 있습니다.

## <a name="cdocobjectserveronsaveviewstate"></a><a name="onsaveviewstate"></a> CDocObjectServer:: OnSaveViewState

이 함수를 재정의 하 여 DocObject 보기에 대 한 추가 상태 정보를 저장 합니다.

```
virtual void OnSaveViewState(CArchive& ar);
```

### <a name="parameters"></a>매개 변수

*ar*<br/>
`CArchive`뷰 상태가 serialize 되는 개체입니다.

### <a name="remarks"></a>설명

상태에는 보기 유형, 확대/축소 비율, 삽입 및 선택 지점과 같은 속성이 포함 될 수 있습니다. 컨테이너는 일반적으로 뷰를 비활성화 하기 전에이 함수를 호출 합니다. 저장 된 상태는 나중에 [Onapplyviewstate](#onapplyviewstate)를 통해 복원할 수 있습니다.

를 사용 `OnSaveViewState` 하 여 보기 상태와 관련 한 영구 정보를 저장할 수 있습니다. 을 재정의 하 여 정보를 저장 하는 경우를 재정의 하 여 `OnSaveViewState` `OnApplyViewState` 해당 정보를 읽고 새로 활성화 될 때 보기에 적용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServerItem 클래스](../../mfc/reference/cdocobjectserveritem-class.md)
