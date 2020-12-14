---
description: '자세히 알아보기: CDocObjectServerItem 클래스'
title: CDocObjectServerItem 클래스
ms.date: 03/27/2019
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnDoVerb
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnDoVerb
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
ms.openlocfilehash: a2d0d924433d812ec5f283d67e8313d20203ca3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184922"
---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServerItem 클래스

DocObject 서버 전용 OLE 서버 동사를 구현합니다.

## <a name="syntax"></a>구문

```
class CDocObjectServerItem : public COleServerItem
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CDocObjectServerItem:: CDocObjectServerItem](#cdocobjectserveritem)|`CDocObjectServerItem` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDocObjectServerItem:: GetDocument](#getdocument)|항목을 포함 하는 문서에 대 한 포인터를 검색 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CDocObjectServerItem:: OnDoVerb](#ondoverb)|동사를 실행 하기 위해 호출 됩니다.|
|[CDocObjectServerItem:: OnHide](#onhide)|프레임 워크에서 DocObject 항목을 숨기려는 경우 예외를 throw 합니다.|
|[CDocObjectServerItem:: OnShow](#onshow)|DocObject 항목을 활성 상태로 만들기 위해 프레임 워크에서 호출 됩니다. 항목이 DocObject가 아니면 [COleServerItem:: OnShow](../../mfc/reference/coleserveritem-class.md#onshow)를 호출 합니다.|

## <a name="remarks"></a>설명

`CDocObjectServerItem`[Onhide](#onhide), [Ondoverb](#ondoverb)및 [onhide](#onshow)의 재정의 가능한 멤버 함수를 정의 합니다.

를 사용 하려면 `CDocObjectServerItem` 파생 클래스의 [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) 재정의가 `COleServerDoc` 새 개체를 반환 하도록 합니다 `CDocObjectServerItem` . 항목의 모든 기능을 변경 해야 하는 경우 고유한 파생 클래스의 새 인스턴스를 만들 수 있습니다 `CDocObjectServerItem` .

DocObjects에 대 한 자세한 내용은 *MFC 참조* 의 [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) 및 [COleCmdUI](../../mfc/reference/colecmdui-class.md) 를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>요구 사항

**헤더:** afxdocob

## <a name="cdocobjectserveritemcdocobjectserveritem"></a><a name="cdocobjectserveritem"></a> CDocObjectServerItem:: CDocObjectServerItem

`CDocObjectServerItem` 개체를 생성합니다.

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>매개 변수

*pServerDoc*<br/>
새 DocObject 항목을 포함 하는 문서에 대 한 포인터입니다.

*bAutoDelete*<br/>
개체에 대 한 링크를 해제할 때 개체를 삭제할 수 있는지 여부를 나타냅니다. `CDocObjectServerItem`개체가 문서 데이터의 정수 부분인 경우 인수를 FALSE로 설정 합니다. 개체가 프레임 워크에서 삭제할 수 있는 문서 데이터의 범위를 식별 하는 데 사용 되는 보조 구조 이면 TRUE로 설정 합니다.

## <a name="cdocobjectserveritemgetdocument"></a><a name="getdocument"></a> CDocObjectServerItem:: GetDocument

항목을 포함 하는 문서에 대 한 포인터를 검색 합니다.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>반환 값

항목을 포함 하는 문서에 대 한 포인터입니다. 항목이 문서의 일부가 아니면 NULL입니다.

### <a name="remarks"></a>설명

이렇게 하면 [CDocObjectServerItem](#cdocobjectserveritem) 생성자에 인수로 전달한 서버 문서에 액세스할 수 있습니다.

## <a name="cdocobjectserveritemondoverb"></a><a name="ondoverb"></a> CDocObjectServerItem:: OnDoVerb

지정 된 동사를 실행 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>매개 변수

*iVerb*<br/>
실행할 동사를 지정 합니다. 가능한 값은 Windows SDK에서 [IOleObject::D 초과 b](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 를 참조 하세요.

### <a name="remarks"></a>설명

항목이 DocObject이 고 OLEIVERB_INPLACEACTIVATE 또는 OLEIVERB_SHOW 지정 된 경우 기본 구현은 [Onshow](#onshow) 멤버 함수를 호출 합니다. 항목이 DocObject가 아니거나 다른 동사가 지정 된 경우 기본 구현에서는 [COleServerItem:: OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb)를 호출 합니다.

## <a name="cdocobjectserveritemonhide"></a><a name="onhide"></a> CDocObjectServerItem:: OnHide

항목을 숨기기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnHide();
```

### <a name="remarks"></a>설명

항목이 DocObject 이면 기본 구현에서 예외를 throw 합니다. 활성 DocObject 항목은 전체 뷰를 사용 하기 때문에 숨길 수 없습니다. DocObject 항목을 비활성화 하 여 사라지게 해야 합니다. 항목이 DocObject가 아닌 경우 기본 구현에서는 [COleServerItem:: OnHide](../../mfc/reference/coleserveritem-class.md#onhide)를 호출 합니다.

## <a name="cdocobjectserveritemonshow"></a><a name="onshow"></a> CDocObjectServerItem:: OnShow

DocObject 항목을 활성 상태로 만들도록 서버 응용 프로그램에 지시 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnShow();
```

### <a name="remarks"></a>설명

항목이 DocObject가 아닌 경우 기본 구현에서는 [COleServerItem:: OnShow](../../mfc/reference/coleserveritem-class.md#onopen)를 호출 합니다. DocObject 항목을 열 때 특별 한 처리를 수행 하려면이 함수를 재정의 합니다.

## <a name="see-also"></a>참고 항목

[COleServerItem 클래스](../../mfc/reference/coleserveritem-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer 클래스](../../mfc/reference/cdocobjectserver-class.md)<br/>
[COleDocObjectItem 클래스](../../mfc/reference/coledocobjectitem-class.md)
