---
description: '자세히 알아보기: CRichEditCntrItem 클래스'
title: CRichEditCntrItem 클래스
ms.date: 11/04/2016
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
helpviewer_keywords:
- CRichEditCntrItem [MFC], CRichEditCntrItem
- CRichEditCntrItem [MFC], SyncToRichEditObject
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
ms.openlocfilehash: 9e65e70a3fb03b65ebf9af7a619a5c4fbd3dba32
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342962"
---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem 클래스

[CRichEditView](../../mfc/reference/cricheditview-class.md) 및 [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)를 사용 하면 MFC의 문서 뷰 아키텍처 컨텍스트 내에서 rich edit 컨트롤의 기능을 제공 합니다.

## <a name="syntax"></a>구문

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CRichEditCntrItem:: CRichEditCntrItem](#cricheditcntritem)|`CRichEditCntrItem` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CRichEditCntrItem:: SyncToRichEditObject](#synctoricheditobject)|항목을 다른 형식으로 활성화 합니다.|

## <a name="remarks"></a>설명

"Rich edit 컨트롤"은 사용자가 텍스트를 입력 하 고 편집할 수 있는 창입니다. 텍스트에는 문자 및 단락 서식 지정이 할당 될 수 있으며 포함 된 OLE 개체도 포함 될 수 있습니다. Rich edit 컨트롤은 텍스트 서식 지정을 위한 프로그래밍 인터페이스를 제공 합니다. 그러나 응용 프로그램은 사용자가 서식 지정 작업을 사용 하도록 설정 하는 데 필요한 모든 사용자 인터페이스 구성 요소를 구현 해야 합니다.

`CRichEditView` 텍스트의 텍스트와 서식 특성을 유지 합니다. `CRichEditDoc` 뷰에 있는 OLE 클라이언트 항목의 목록을 유지 관리 합니다. `CRichEditCntrItem` OLE 클라이언트 항목에 대 한 컨테이너 쪽 액세스를 제공 합니다.

이 Windows 공용 컨트롤 (및 [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) 및 관련 클래스)은 windows 95/98 및 windows NT 버전 3.51 이상에서 실행 되는 프로그램에만 사용할 수 있습니다.

MFC 응용 프로그램에서 rich edit 컨테이너 항목을 사용 하는 예제는 [워드 패드](../../overview/visual-cpp-samples.md) 샘플 응용 프로그램을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>요구 사항

**헤더:** afxrich

## <a name="cricheditcntritemcricheditcntritem"></a><a name="cricheditcntritem"></a> CRichEditCntrItem:: CRichEditCntrItem

개체를 만들어 컨테이너 문서에 추가 하려면이 함수를 호출 `CRichEditCntrItem` 합니다.

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>매개 변수

*사전 o*<br/>
OLE 항목을 설명 하는 [Reobject](/windows/win32/api/richole/ns-richole-reobject) 구조에 대 한 포인터입니다. `CRichEditCntrItem`이 OLE 항목을 중심으로 새 개체가 생성 됩니다. *Preo* 가 NULL 이면 클라이언트 항목이 비어 있습니다.

*pContainer*<br/>
이 항목을 포함 하는 컨테이너 문서에 대 한 포인터입니다. *Pcontainer* 가 NULL 이면 [Coledocument:: AddItem](../../mfc/reference/coledocument-class.md#additem) 을 명시적으로 호출 하 여이 클라이언트 항목을 문서에 추가 해야 합니다.

### <a name="remarks"></a>설명

이 함수는 OLE 초기화를 수행 하지 않습니다.

자세한 내용은 Windows SDK의 [Reobject](/windows/win32/api/richole/ns-richole-reobject) 구조를 참조 하세요.

## <a name="cricheditcntritemsynctoricheditobject"></a><a name="synctoricheditobject"></a> CRichEditCntrItem:: SyncToRichEditObject

이 함수를 호출 하 여이의 장치 측면, [Dvaspect](/windows/win32/api/wtypes/ne-wtypes-dvaspect)를 `CRichEditCntrltem` *reo* 로 지정 된와 동기화 합니다.

```cpp
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>매개 변수

*reo*<br/>
OLE 항목을 설명 하는 [Reobject](/windows/win32/api/richole/ns-richole-reobject) 구조에 대 한 참조입니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK [Dvaspect](/windows/win32/api/wtypes/ne-wtypes-dvaspect) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 워드 패드](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem 클래스](../../mfc/reference/coleclientitem-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc 클래스](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditView 클래스](../../mfc/reference/cricheditview-class.md)
