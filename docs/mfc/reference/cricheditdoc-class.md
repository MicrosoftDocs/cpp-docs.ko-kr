---
description: '자세히 알아보기: CRichEditDoc 클래스'
title: CRichEditDoc 클래스
ms.date: 11/04/2016
f1_keywords:
- CRichEditDoc
- AFXRICH/CRichEditDoc
- AFXRICH/CRichEditDoc::CreateClientItem
- AFXRICH/CRichEditDoc::GetStreamFormat
- AFXRICH/CRichEditDoc::GetView
- AFXRICH/CRichEditDoc::m_bRTF
helpviewer_keywords:
- CRichEditDoc [MFC], CreateClientItem
- CRichEditDoc [MFC], GetStreamFormat
- CRichEditDoc [MFC], GetView
- CRichEditDoc [MFC], m_bRTF
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
ms.openlocfilehash: 5e94fb8edb3f5a596b71ddd55cdcb2077ba6201d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342932"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc 클래스

[CRichEditView](../../mfc/reference/cricheditview-class.md) 및 [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)를 사용 하면 MFC의 문서 뷰 아키텍처 컨텍스트 내에서 rich edit 컨트롤의 기능을 제공 합니다.

## <a name="syntax"></a>구문

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CRichEditDoc:: CreateClientItem](#createclientitem)|문서 정리를 수행 하기 위해 호출 됩니다.|
|[CRichEditDoc:: GetStreamFormat](#getstreamformat)|스트림 입력 및 출력에 형식 지정 정보가 포함 되어야 하는지 여부를 나타냅니다.|
|[CRichEditDoc:: GetView](#getview)|[CRichEditView](../../mfc/reference/cricheditview-class.md) 개체를 검색 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CRichEditDoc:: m_bRTF](#m_brtf)|스트림 i/o에 서식 지정이 포함 되어야 하는지 여부를 나타냅니다.|

## <a name="remarks"></a>설명

"Rich edit 컨트롤"은 사용자가 텍스트를 입력 하 고 편집할 수 있는 창입니다. 텍스트에는 문자 및 단락 서식 지정이 할당 될 수 있으며 포함 된 OLE 개체도 포함 될 수 있습니다. Rich edit 컨트롤은 텍스트 서식 지정을 위한 프로그래밍 인터페이스를 제공 합니다. 그러나 응용 프로그램은 사용자가 서식 지정 작업을 사용 하도록 설정 하는 데 필요한 모든 사용자 인터페이스 구성 요소를 구현 해야 합니다.

`CRichEditView` 텍스트의 텍스트와 서식 특성을 유지 합니다. `CRichEditDoc` 뷰에 있는 클라이언트 항목의 목록을 유지 관리 합니다. `CRichEditCntrItem` OLE 클라이언트 항목에 대 한 컨테이너 쪽 액세스를 제공 합니다.

이 Windows 공용 컨트롤 (및 [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) 및 관련 클래스)은 windows 95/98 및 windows NT 버전 3.51 이상에서 실행 되는 프로그램에만 사용할 수 있습니다.

MFC 응용 프로그램에서 서식 있는 편집 문서를 사용 하는 예제는 [워드 패드](../../overview/visual-cpp-samples.md) 샘플 응용 프로그램을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>요구 사항

**헤더:** afxrich

## <a name="cricheditdoccreateclientitem"></a><a name="createclientitem"></a> CRichEditDoc:: CreateClientItem

개체를 만들어이 문서에 추가 하려면이 함수를 호출 `CRichEditCntrItem` 합니다.

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>매개 변수

*사전 o*<br/>
OLE 항목을 설명 하는 [Reobject](/windows/win32/api/richole/ns-richole-reobject) 구조에 대 한 포인터입니다. `CRichEditCntrItem`이 OLE 항목을 중심으로 새 개체가 생성 됩니다. *Preo* 가 NULL 이면 새 클라이언트 항목이 비어 있습니다.

### <a name="return-value"></a>반환 값

이 문서에 추가 된 새 [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 함수는 OLE 초기화를 수행 하지 않습니다.

자세한 내용은 Windows SDK의 [Reobject](/windows/win32/api/richole/ns-richole-reobject) 구조를 참조 하세요.

## <a name="cricheditdocgetstreamformat"></a><a name="getstreamformat"></a> CRichEditDoc:: GetStreamFormat

Rich edit의 콘텐츠를 스트리밍하는 텍스트 형식을 결정 하려면이 함수를 호출 합니다.

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>반환 값

다음 플래그 중 하나입니다.

- SF_TEXT rich edit 컨트롤이 서식 지정 정보를 유지 관리 하지 않음을 나타냅니다.

- SF_RTF rich edit 컨트롤이 서식 지정 정보를 유지 관리 함을 나타냅니다.

### <a name="remarks"></a>설명

반환 값은 [m_bRTF](#m_brtf) 데이터 멤버를 기반으로 합니다. 이 TRUE 인 경우이 함수 `m_bRTF` 는 SF_RTF을 반환 하 고, 그렇지 않으면 SF_TEXT 합니다.

## <a name="cricheditdocgetview"></a><a name="getview"></a> CRichEditDoc:: GetView

이 개체와 연결 된 [CRichEditView](../../mfc/reference/cricheditview-class.md) 개체에 액세스 하려면이 함수를 호출 `CRichEditDoc` 합니다.

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>반환 값

문서와 연결 된 개체에 대 한 포인터 `CRichEditView` 입니다.

### <a name="remarks"></a>설명

텍스트 및 서식 지정 정보는 개체에 포함 되어 `CRichEditView` 있습니다. `CRichEditDoc`개체는 직렬화를 위해 OLE 항목을 유지 관리 합니다. `CRichEditView`각각에 대해 하나만 있어야 합니다 `CRichEditDoc` .

## <a name="cricheditdocm_brtf"></a><a name="m_brtf"></a> CRichEditDoc:: m_bRTF

TRUE 이면 [CRichEditCtrl:: StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin) 및 [CRichEditCtrl:: streamin](../../mfc/reference/cricheditctrl-class.md#streamout) 에서 단락과 문자 서식 특성을 저장 해야 함을 나타냅니다.

```
BOOL m_bRTF;
```

## <a name="see-also"></a>참고 항목

[MFC 샘플 워드 패드](../../overview/visual-cpp-samples.md)<br/>
[COleServerDoc 클래스](../../mfc/reference/coleserverdoc-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CRichEditView 클래스](../../mfc/reference/cricheditview-class.md)<br/>
[CRichEditCntrItem 클래스](../../mfc/reference/cricheditcntritem-class.md)<br/>
[COleDocument 클래스](../../mfc/reference/coledocument-class.md)<br/>
[CRichEditCtrl 클래스](../../mfc/reference/cricheditctrl-class.md)
