---
description: '자세히 알아보기: CMFCRibbonCustomizeDialog 클래스'
title: CMFCRibbonCustomizeDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
ms.openlocfilehash: 9420ebdf32a1c26cba6efee17467fd3dfe202574
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293614"
---
# <a name="cmfcribboncustomizedialog-class"></a>CMFCRibbonCustomizeDialog 클래스

리본 메뉴 **사용자 지정** 페이지를 표시 합니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|`CMFCRibbonCustomizeDialog` 개체를 생성합니다.|
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|`CMFCRibbonCustomizeDialog::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|

## <a name="remarks"></a>설명

AFX_WM_ON_RIBBON_CUSTOMIZE 메시지를 처리 하지 않거나 메시지 처리기에서 0을 반환 하는 경우 MFC는이 클래스를 자동으로 인스턴스화합니다.

응용 프로그램에서이 클래스를 사용 하 여 리본 **사용자 지정** 대화 상자를 표시 하려면 해당 클래스를 인스턴스화하고 메서드를 호출 하기만 하면 `DoModal` 됩니다.

이 클래스는 [CMFCPropertySheet 클래스](../../mfc/reference/cmfcpropertysheet-class.md)에서 파생 되므로 API를 사용 하 여 사용자 지정 페이지를 추가할 수 있습니다 `CMFCPropertySheet` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

[CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxribboncustomizedialog

## <a name="cmfcribboncustomizedialogcmfcribboncustomizedialog"></a><a name="cmfcribboncustomizedialog"></a> CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog

`CMFCRibbonCustomizeDialog` 개체를 생성합니다.

```
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,
    CMFCRibbonBar* pRibbon);
```

### <a name="parameters"></a>매개 변수

*pWndParent*<br/>
진행 부모 창에 대 한 포인터입니다 (일반적으로 주 프레임).

*설정 Bbon*<br/>
진행 사용자 지정할에 대 한 포인터입니다 `CMFCRibbonBar` .

### <a name="example"></a>예제

다음 예제에서는 개체를 생성 하는 방법을 보여 줍니다 `CMFCRibbonCustomizeDialog` .

[!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]

### <a name="remarks"></a>설명

생성자는 [CMFCRibbonCustomizePropertyPage 클래스](../../mfc/reference/cmfcribboncustomizepropertypage-class.md) 개체를 인스턴스화하고 속성 시트 페이지의 컬렉션에 추가 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)
