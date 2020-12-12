---
description: '자세히 알아보기: CMFCPropertyPage 클래스'
title: CMFCPropertyPage 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
ms.openlocfilehash: 9acdce1fd2f6133d44699f7bea4cce00e9d6dadb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289857"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage 클래스

`CMFCPropertyPage`클래스는 속성 페이지에서 팝업 메뉴의 표시를 지원 합니다.

## <a name="syntax"></a>구문

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|`CMFCPropertyPage` 개체를 생성합니다.|
|`CMFCPropertyPage::~CMFCPropertyPage`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|`CMFCPropertyPage::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|`CMFCPropertyPage::OnSetActive`|이 멤버 함수는 사용자가 페이지를 선택 하 고 활성 페이지가 될 때 프레임 워크에서 호출 됩니다. [CPropertyPage:: OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive)를 재정의 합니다.|
|`CMFCPropertyPage::PreTranslateMessage`|창 메시지가 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 및 [dispatchmessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 함수로 디스패치 되기 전에 변환 합니다. 자세한 내용 및 메서드 구문은 [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)를 참조 하세요. ( `CPropertyPage::PreTranslateMessage`을 재정의합니다.)|

## <a name="remarks"></a>설명

`CMFCPropertyPage`클래스는 속성 시트 (탭 대화 상자 라고도 함)의 개별 페이지를 나타냅니다.

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) 클래스와 함께 `CMFCPropertyPage` 클래스를 사용합니다. 속성 페이지에서 메뉴를 사용 하려면 클래스의 모든 항목을 `CPropertyPage` `CMFCPropertyPage` 클래스로 바꿉니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxpropertypage

## <a name="cmfcpropertypagecmfcpropertypage"></a><a name="cmfcpropertypage"></a> CMFCPropertyPage:: CMFCPropertyPage

`CMFCPropertyPage` 개체를 생성합니다.

```
CMFCPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption=0);

CMFCPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption=0);
```

### <a name="parameters"></a>매개 변수

*nIDTemplate*<br/>
이 페이지에 대 한 템플릿의 리소스 ID입니다.

*nIDCaption*<br/>
이 페이지의 탭에 넣을 레이블의 리소스 ID입니다. 0 인 경우이 페이지에 대 한 대화 상자 템플릿에서 이름을 가져옵니다. 기본값은 0입니다.

*lpszTemplateName*<br/>
이 페이지의 템플릿 이름을 가리킵니다. NULL이 될 수 없습니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

생성자 매개 변수에 대 한 자세한 내용은 [CPropertyPage:: CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertySheet 클래스](../../mfc/reference/cmfcpropertysheet-class.md)
