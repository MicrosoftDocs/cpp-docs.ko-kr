---
description: '자세히 알아보기: CMFCRibbonCustomizePropertyPage 클래스'
title: CMFCRibbonCustomizePropertyPage 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
helpviewer_keywords:
- CMFCRibbonCustomizePropertyPage [MFC], CMFCRibbonCustomizePropertyPage
- CMFCRibbonCustomizePropertyPage [MFC], AddCustomCategory
- CMFCRibbonCustomizePropertyPage [MFC], OnOK
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
ms.openlocfilehash: 93792858cec9d07a73bfec56a282b8d672249cf6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293601"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>CMFCRibbonCustomizePropertyPage 클래스

리본 기반 응용 프로그램의 **사용자** 지정 대화 상자에 대 한 사용자 지정 페이지를 구현 합니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|-|-|
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|`CMFCRibbonCustomizePropertyPage` 개체를 생성합니다.|
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|-|-|
|[CMFCRibbonCustomizePropertyPage:: AddCustomCategory](#addcustomcategory)|사용자 지정 범주를 **명령** 콤보 상자에 추가 합니다.|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CMFCRibbonCustomizePropertyPage:: OnOK](#onok)|사용자가 [ **사용자 지정** ] 대화 상자에서 **[확인]** 을 클릭 하면 시스템에서 호출 됩니다.|

## <a name="remarks"></a>설명

**사용자 지정 대화 상자** 에 사용자 지정 명령을 추가 하려면 AFX_WM_ON_RIBBON_CUSTOMIZE 메시지를 처리 해야 합니다. 메시지 처리기에서 스택에 있는 개체를 인스턴스화합니다 `CMFCRibbonCustomizePropertyPage` . 사용자 지정 명령 목록을 만든 다음를 호출 하 여 `AddCustomCategory` **사용자** 지정 대화 상자에 새 페이지를 추가 합니다.

## <a name="example"></a>예제

다음 예제에서는 개체를 생성 하 `CMFCRibbonCustomizePropertyPage` 고 사용자 지정 범주를 추가 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

[CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxribboncustomizedialog

## <a name="cmfcribboncustomizepropertypageaddcustomcategory"></a><a name="addcustomcategory"></a> CMFCRibbonCustomizePropertyPage:: AddCustomCategory

사용자 지정 범주를 **명령** 콤보 상자에 추가 합니다.

```cpp
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>매개 변수

*lpszName*\
진행 사용자 지정 범주 이름을 지정 합니다.

*lstIDS*\
진행 사용자 지정 범주에 표시 되는 리본 명령 Id를 포함 합니다.

### <a name="remarks"></a>설명

이 메서드는 **명령** 콤보 상자에 *lpszName* 이라는 범주를 추가 합니다. 사용자가 범주를 선택 하면 *Lstids* 에 지정 된 명령이 명령 목록에 표시 됩니다.

## <a name="cmfcribboncustomizepropertypagecmfcribboncustomizepropertypage"></a><a name="cmfcribboncustomizepropertypage"></a> CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage

`CMFCRibbonCustomizePropertyPage` 개체를 생성합니다.

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>매개 변수

*pRibbonBar*<br/>
진행 사용자 지정할 옵션에 대 한 리본 컨트롤에 대 한 포인터입니다.

## <a name="cmfcribboncustomizepropertypageonok"></a><a name="onok"></a> CMFCRibbonCustomizePropertyPage:: OnOK

사용자 **지정** 대화 상자에서 **확인** 을 클릭 하면 시스템에 의해 calleld

```
virtual void OnOK();
```

### <a name="remarks"></a>설명

기본 구현에서는 **사용자 지정** 대화 상자에서 선택한 옵션을 빠른 실행 도구 모음에 적용 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)
