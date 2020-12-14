---
description: '자세히 알아보기: CPropertyPage 클래스'
title: CPropertyPage 클래스
ms.date: 11/04/2016
f1_keywords:
- CPropertyPage
- AFXDLGS/CPropertyPage
- AFXDLGS/CPropertyPage::CPropertyPage
- AFXDLGS/CPropertyPage::CancelToClose
- AFXDLGS/CPropertyPage::Construct
- AFXDLGS/CPropertyPage::GetPSP
- AFXDLGS/CPropertyPage::OnApply
- AFXDLGS/CPropertyPage::OnCancel
- AFXDLGS/CPropertyPage::OnKillActive
- AFXDLGS/CPropertyPage::OnOK
- AFXDLGS/CPropertyPage::OnQueryCancel
- AFXDLGS/CPropertyPage::OnReset
- AFXDLGS/CPropertyPage::OnSetActive
- AFXDLGS/CPropertyPage::OnWizardBack
- AFXDLGS/CPropertyPage::OnWizardFinish
- AFXDLGS/CPropertyPage::OnWizardNext
- AFXDLGS/CPropertyPage::QuerySiblings
- AFXDLGS/CPropertyPage::SetModified
- AFXDLGS/CPropertyPage::m_psp
helpviewer_keywords:
- CPropertyPage [MFC], CPropertyPage
- CPropertyPage [MFC], CancelToClose
- CPropertyPage [MFC], Construct
- CPropertyPage [MFC], GetPSP
- CPropertyPage [MFC], OnApply
- CPropertyPage [MFC], OnCancel
- CPropertyPage [MFC], OnKillActive
- CPropertyPage [MFC], OnOK
- CPropertyPage [MFC], OnQueryCancel
- CPropertyPage [MFC], OnReset
- CPropertyPage [MFC], OnSetActive
- CPropertyPage [MFC], OnWizardBack
- CPropertyPage [MFC], OnWizardFinish
- CPropertyPage [MFC], OnWizardNext
- CPropertyPage [MFC], QuerySiblings
- CPropertyPage [MFC], SetModified
- CPropertyPage [MFC], m_psp
ms.assetid: d9000a21-aa81-4530-85d9-f43432afb4dc
ms.openlocfilehash: ea95b6d909b97e424081e44b4ef618a7c7e3c4dd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343360"
---
# <a name="cpropertypage-class"></a>CPropertyPage 클래스

속성 시트(탭 대화 상자라고도 함)의 개별 페이지를 나타냅니다.

## <a name="syntax"></a>구문

```
class CPropertyPage : public CDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CPropertyPage:: CPropertyPage](#cpropertypage)|`CPropertyPage` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPropertyPage:: CancelToClose](#canceltoclose)|모달 속성 시트의 페이지에서 복구할 수 없는 변경 후 취소 단추를 사용 하지 않도록 설정 하 여 확인 단추를 변경 합니다.|
|[CPropertyPage:: 생성자](#construct)|`CPropertyPage` 개체를 생성합니다. `Construct`런타임에 매개 변수를 지정 하려면를 사용 하 고, 배열을 사용 하는 경우를 사용 합니다.|
|[CPropertyPage:: GetPSP](#getpsp)|개체와 연결 된 Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) 구조체를 검색 합니다 `CPropertyPage` .|
|[CPropertyPage:: OnApply](#onapply)|지금 적용 단추를 클릭할 때 프레임 워크에서 호출 됩니다.|
|[CPropertyPage:: OnCancel](#oncancel)|취소 단추를 클릭할 때 프레임 워크에서 호출 됩니다.|
|[CPropertyPage:: OnKillActive](#onkillactive)|현재 페이지가 더 이상 활성 페이지가 아닌 경우 프레임 워크에서 호출 됩니다. 여기에서 데이터 유효성 검사를 수행 합니다.|
|[CPropertyPage:: OnOK](#onok)|확인, 지금 적용 또는 닫기 단추가 클릭 될 때 프레임 워크에서 호출 됩니다.|
|[CPropertyPage:: OnQueryCancel](#onquerycancel)|취소 단추를 클릭 한 후 취소가 수행 되기 전에 프레임 워크에서 호출 됩니다.|
|[CPropertyPage:: OnReset](#onreset)|취소 단추를 클릭할 때 프레임 워크에서 호출 됩니다.|
|[CPropertyPage:: OnSetActive](#onsetactive)|페이지를 활성 페이지로 만들 때 프레임 워크에서 호출 됩니다.|
|[CPropertyPage:: OnWizardBack](#onwizardback)|마법사 형식의 속성 시트를 사용 하는 동안 뒤로 단추를 클릭 하면 프레임 워크에서 호출 됩니다.|
|[CPropertyPage:: OnWizardFinish](#onwizardfinish)|마법사 유형 속성 시트를 사용 하는 동안 [마침] 단추를 클릭 하면 프레임 워크에서 호출 됩니다.|
|[CPropertyPage:: OnWizardNext](#onwizardnext)|마법사 형식의 속성 시트를 사용 하는 동안 다음 단추를 클릭 하면 프레임 워크에서 호출 됩니다.|
|[CPropertyPage:: QuerySiblings](#querysiblings)|속성 시트의 각 페이지로 메시지를 전달 합니다.|
|[CPropertyPage:: SetModified](#setmodified)|을 호출 하 여 지금 적용 단추를 활성화 하거나 비활성화 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CPropertyPage:: m_psp](#m_psp)|Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) 구조체입니다. 기본 속성 페이지 매개 변수에 대 한 액세스를 제공 합니다.|

## <a name="remarks"></a>설명

표준 대화 상자와 마찬가지로 `CPropertyPage` 속성 시트의 각 페이지에 대해에서 클래스를 파생 시킬 수 있습니다. 파생 개체를 사용 하려면 `CPropertyPage` 먼저 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md) 개체를 만든 다음 속성 시트에서 이동 하는 각 페이지에 대 한 개체를 만듭니다. 시트의 각 페이지에 대해 [CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) 를 호출한 다음 모달 속성 시트에 대 한 [CPropertySheet::D omodal](../../mfc/reference/cpropertysheet-class.md#domodal) 또는 모덜리스 속성 시트에 대 한 [CPropertySheet:: Create](../../mfc/reference/cpropertysheet-class.md#create) 를 호출 하 여 속성 시트를 표시 합니다.

마법사 라는 유형의 탭 대화 상자를 만들 수 있습니다 .이 대화 상자는 사용자가 장치를 설정 하거나 뉴스레터를 만드는 등의 작업 단계를 안내 하는 일련의 속성 페이지를 사용 하 여 속성 시트로 구성 됩니다. 마법사-형식 탭 대화 상자에서 속성 페이지에 탭이 없으며 한 번에 하나의 속성 페이지만 표시 됩니다. 또한 확인 및 지금 적용 단추 대신 마법사 유형 탭 대화 상자에 뒤로 단추, 다음 또는 마침 단추 및 취소 단추가 있습니다.

속성 시트를 마법사로 설정 하는 방법에 대 한 자세한 내용은 [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)를 참조 하세요. 개체 사용에 대 한 자세한 내용은 `CPropertyPage` 아티클 [속성 시트 및 속성 페이지](../../mfc/property-sheets-and-property-pages-in-mfc.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>요구 사항

**헤더:** afxdlgs

## <a name="cpropertypagecanceltoclose"></a><a name="canceltoclose"></a> CPropertyPage:: CancelToClose

모달 속성 시트의 페이지에 있는 데이터에 대해 복구할 수 없는 변경 내용이 발생 한 후이 함수를 호출 합니다.

```cpp
void CancelToClose();
```

### <a name="remarks"></a>설명

이 함수는 취소 단추를 닫거나 사용 하지 않도록 설정 하는 확인 단추를 변경 합니다. 이 변경으로 인해 사용자에 게 변경 내용이 영구적이 고 수정 내용을 취소할 수 없다는 경고가 발생 합니다.

모덜리스 속성 시트 `CancelToClose` 에는 기본적으로 취소 단추가 없기 때문에 멤버 함수는 모덜리스 속성 시트에서 아무 작업도 수행 하지 않습니다.

### <a name="example"></a>예제

  [CPropertyPage:: QuerySiblings](#querysiblings)의 예제를 참조 하세요.

## <a name="cpropertypageconstruct"></a><a name="construct"></a> CPropertyPage:: 생성자

개체를 생성 하려면이 멤버 함수를 호출 `CPropertyPage` 합니다.

```cpp
void Construct(
    UINT nIDTemplate,
    UINT nIDCaption = 0);

void Construct(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption = 0);

void Construct(
    UINT nIDTemplate,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0);

void Construct(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0);
```

### <a name="parameters"></a>매개 변수

*nIDTemplate*<br/>
이 페이지에 사용 되는 템플릿의 ID입니다.

*nIDCaption*<br/>
이 페이지의 탭에 배치할 이름의 ID입니다. 0 인 경우이 페이지에 대 한 대화 상자 템플릿에서 이름을 가져옵니다.

*lpszTemplateName*<br/>
템플릿 리소스의 이름인 null로 끝나는 문자열을 포함 합니다.

*nIDHeaderTitle*<br/>
속성 페이지 머리글의 제목 위치에 배치할 이름의 ID입니다. 기본적으로 0입니다.

*nIDHeaderSubTitle*<br/>
속성 페이지 머리글의 부제목 위치에 배치할 이름의 ID입니다. 기본적으로 0입니다.

### <a name="remarks"></a>설명

다음 조건이 모두 충족 되 면 개체가 표시 됩니다.

- [CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage)를 사용 하 여 페이지가 속성 시트에 추가 되었습니다.

- 속성 시트의 [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) 또는 [Create](../../mfc/reference/cpropertysheet-class.md#create) 함수를 호출 했습니다.

- 사용자가이 페이지를 선택 (탭) 합니다.

`Construct`다른 클래스 생성자 중 하나가 호출 되지 않은 경우를 호출 합니다. `Construct`멤버 함수는 매개 변수 문을 비워 두고 코드의 임의 위치에서 여러 매개 변수 및 생성을 지정할 수 있으므로 유연 합니다.

배열을 사용 하 여 작업할 때를 사용 해야 `Construct` 하며, `Construct` 데이터 멤버에 적절 한 값이 할당 되도록 배열의 각 멤버에 대해를 호출 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

## <a name="cpropertypagecpropertypage"></a><a name="cpropertypage"></a> CPropertyPage:: CPropertyPage

`CPropertyPage` 개체를 생성합니다.

```
CPropertyPage();

explicit CPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

explicit CPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

CPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

CPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));
```

### <a name="parameters"></a>매개 변수

*nIDTemplate*<br/>
이 페이지에 사용 되는 템플릿의 ID입니다.

*nIDCaption*<br/>
이 페이지의 탭에 배치할 이름의 ID입니다. 0 인 경우이 페이지에 대 한 대화 상자 템플릿에서 이름을 가져옵니다.

*dwSize*<br/>
*lpszTemplateName* 이 페이지의 템플릿 이름을 포함 하는 문자열을 가리킵니다. NULL이 될 수 없습니다.

*nIDHeaderTitle*<br/>
속성 페이지 머리글의 제목 위치에 배치할 이름의 ID입니다.

*nIDHeaderSubTitle*<br/>
속성 페이지 머리글의 부제목 위치에 배치할 이름의 ID입니다.

### <a name="remarks"></a>설명

다음 조건이 모두 충족 되 면 개체가 표시 됩니다.

- [CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage)를 사용 하 여 페이지가 속성 시트에 추가 되었습니다.

- 속성 시트의 [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) 또는 [Create](../../mfc/reference/cpropertysheet-class.md#create) 함수를 호출 했습니다.

- 사용자가이 페이지를 선택 (탭) 합니다.

배열을 사용 하는 경우와 같이 여러 매개 변수가 있는 경우 대신 [CPropertySheet:: 구문을](../../mfc/reference/cpropertysheet-class.md#construct) 사용 `CPropertyPage` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

## <a name="cpropertypagegetpsp"></a><a name="getpsp"></a> CPropertyPage:: GetPSP

개체와 연결 된 Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) 구조체를 검색 합니다 `CPropertyPage` .

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>반환 값

구조체에 대 한 참조 `PROPSHEETPAGE` 입니다.

## <a name="cpropertypagem_psp"></a><a name="m_psp"></a> CPropertyPage:: m_psp

`m_psp` 는 해당 멤버가 [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)의 특성을 저장 하는 구조체입니다.

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>설명

이 구조체를 사용 하 여 속성 페이지가 생성 된 후 해당 페이지의 모양을 초기화할 수 있습니다.

멤버 목록을 포함 하 여이 구조에 대 한 자세한 내용은 Windows SDK을 참조 `PROPSHEETPAGE` 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

## <a name="cpropertypageonapply"></a><a name="onapply"></a> CPropertyPage:: OnApply

이 멤버 함수는 사용자가 확인 또는 지금 적용 단추를 선택할 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>반환 값

변경 내용이 수락 되는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

프레임 워크에서이 함수를 호출 하면 속성 시트의 모든 속성 페이지에서 변경한 내용이 수락 되 고, 속성 시트가 포커스를 유지 하 고, `OnApply` TRUE (값 1)를 반환 합니다. 가 `OnApply` 프레임 워크에서 호출 될 수 있도록 하려면 [setmodified](#setmodified) 를 호출 하 고 매개 변수를 TRUE로 설정 해야 합니다. 이렇게 하면 사용자가 속성 페이지에서 변경 하는 즉시 적용 단추가 활성화 됩니다.

사용자가 지금 적용 단추를 클릭할 때 프로그램에서 수행 하는 작업을 지정 하려면이 멤버 함수를 재정의 합니다. 을 재정의 하는 경우 함수는 변경 내용을 적용 하기 위해 TRUE를 반환 하 고 변경 내용을 적용 하지 않도록 하려면 FALSE를 반환 해야 합니다.

호출의 기본 구현 `OnApply` `OnOK` 입니다.

사용자가 속성 시트에서 지금 적용 또는 확인 단추를 누를 때 전송 되는 알림 메시지에 대 한 자세한 내용은 Windows SDK [PSN_APPLY](/windows/win32/Controls/psn-apply) 을 참조 하세요.

### <a name="example"></a>예제

  [CPropertyPage:: OnOK](#onok)의 예제를 참조 하세요.

## <a name="cpropertypageoncancel"></a><a name="oncancel"></a> CPropertyPage:: OnCancel

이 멤버 함수는 취소 단추를 선택할 때 프레임 워크에서 호출 됩니다.

```
virtual void OnCancel();
```

### <a name="remarks"></a>설명

취소 단추 작업을 수행 하려면이 멤버 함수를 재정의 합니다. 기본값은 적용 된 모든 변경 내용을 부정 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

## <a name="cpropertypageonkillactive"></a><a name="onkillactive"></a> CPropertyPage:: OnKillActive

이 멤버 함수는 페이지가 더 이상 활성 페이지가 아닌 경우 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>반환 값

데이터가 성공적으로 업데이트 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

특수 한 데이터 유효성 검사 작업을 수행 하려면이 멤버 함수를 재정의 합니다.

이 멤버 함수의 기본 구현은 속성 페이지의 컨트롤에서 속성 페이지의 멤버 변수로 설정을 복사 합니다. DDV (대화 상자 데이터 유효성 검사) 오류로 인해 데이터가 성공적으로 업데이트 되지 않은 경우 페이지는 포커스를 유지 합니다.

이 멤버 함수가 성공적으로 반환 되 면 프레임 워크에서 페이지의 [OnOK](#onok) 함수를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

## <a name="cpropertypageonok"></a><a name="onok"></a> CPropertyPage:: OnOK

이 멤버 함수는 프레임 워크에서 [OnKillActive](#onkillactive)를 호출한 직후에 사용자가 확인 또는 지금 적용 단추를 선택할 때 프레임 워크에서 호출 됩니다.

```
virtual void OnOK();
```

### <a name="remarks"></a>설명

사용자가 확인 또는 지금 적용 단추를 선택 하면 프레임 워크는 속성 페이지에서 [PSN_APPLY](/windows/win32/Controls/psn-apply) 알림을 받습니다. `OnOK` [CPropertySheet::P ressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton) 을 호출 하는 경우에 대 한 호출을 수행 하지 않습니다 .이 경우 속성 페이지에서 알림을 보내지 않기 때문입니다.

사용자가 전체 속성 시트를 닫을 때 현재 활성화 된 페이지와 관련 된 추가 동작을 구현 하려면이 멤버 함수를 재정의 합니다.

이 멤버 함수의 기본 구현은 페이지를 "clean"으로 표시 하 여 데이터를 함수에서 업데이트 했음을 반영 합니다 `OnKillActive` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

## <a name="cpropertypageonquerycancel"></a><a name="onquerycancel"></a> CPropertyPage:: OnQueryCancel

이 멤버 함수는 사용자가 취소 단추를 클릭 한 후 취소 작업이 수행 되기 전에 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>반환 값

취소 작업을 방지 하려면 FALSE를 반환 하 고, 허용 하려면 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

사용자가 취소 단추를 클릭할 때 프로그램에서 수행 하는 동작을 지정 하려면이 멤버 함수를 재정의 합니다.

의 기본 구현에서는 `OnQueryCancel` TRUE를 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

## <a name="cpropertypageonreset"></a><a name="onreset"></a> CPropertyPage:: OnReset

이 멤버 함수는 사용자가 취소 단추를 선택할 때 프레임 워크에서 호출 됩니다.

```
virtual void OnReset();
```

### <a name="remarks"></a>설명

프레임 워크에서이 함수를 호출 하면 이전에 적용 단추를 선택 하 여 사용자가 만든 모든 속성 페이지의 변경 내용이 삭제 되 고 속성 시트가 포커스를 유지 합니다.

사용자가 취소 단추를 클릭할 때 프로그램에서 수행 하는 작업을 지정 하려면이 멤버 함수를 재정의 합니다.

의 기본 구현은 `OnReset` 아무 작업도 수행 하지 않습니다.

### <a name="example"></a>예제

  [CPropertyPage:: OnCancel](#oncancel)의 예제를 참조 하세요.

## <a name="cpropertypageonsetactive"></a><a name="onsetactive"></a> CPropertyPage:: OnSetActive

이 멤버 함수는 사용자가 페이지를 선택 하 고 활성 페이지가 될 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>반환 값

페이지가 활성 상태로 설정 되 면 0이 아닌 값으로 설정 됩니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

페이지가 활성화 될 때 작업을 수행 하려면이 멤버 함수를 재정의 합니다. 이 멤버 함수의 재정의는 일반적으로 데이터 멤버를 업데이트 한 후 기본 버전을 호출 하 여 새 데이터를 사용 하 여 페이지 컨트롤을 업데이트할 수 있게 합니다.

기본 구현을 사용 하면 페이지에 대 한 창이 생성 되 고, 이전에 생성 되지 않은 경우 활성 페이지로 설정 됩니다.

### <a name="example"></a>예제

  [CPropertySheet:: Set 텍스트](../../mfc/reference/cpropertysheet-class.md#setfinishtext)의 예제를 참조 하세요.

## <a name="cpropertypageonwizardback"></a><a name="onwizardback"></a> CPropertyPage:: OnWizardBack

이 멤버 함수는 사용자가 마법사에서 뒤로 단추를 클릭할 때 프레임 워크에서 호출 됩니다.

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>반환 값

0은 자동으로 다음 페이지로 이동 합니다. -1은 페이지가 변경 되지 않도록 합니다. 다음 페이지로 이동 하려면 표시 되는 대화 상자의 식별자를 반환 합니다.

### <a name="remarks"></a>설명

뒤로 단추를 누를 때 사용자가 수행 해야 하는 동작을 지정 하려면이 멤버 함수를 재정의 합니다.

마법사 유형 속성 시트를 만드는 방법에 대 한 자세한 내용은 [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

## <a name="cpropertypageonwizardfinish"></a><a name="onwizardfinish"></a> CPropertyPage:: OnWizardFinish

이 멤버 함수는 사용자가 마법사에서 마침 단추를 클릭할 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>반환 값

마법사가 완료 될 때 속성 시트가 제거 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

사용자가 마법사에서 **마침** 단추를 클릭 하면 프레임 워크에서이 함수를 호출 합니다. `OnWizardFinish` 이 0이 아닌 값을 반환 하면 속성 시트를 제거할 수 있지만 실제로는 제거 되지 않습니다. `DestroyWindow`을 호출 하 여 속성 시트를 제거 합니다. 에서를 호출 하지 마십시오. 이렇게 하면 `DestroyWindow` `OnWizardFinish` 힙이 손상 되거나 다른 오류가 발생 합니다.

이 멤버 함수를 재정의 하 여 마침 단추를 누를 때 사용자가 수행 해야 하는 동작을 지정할 수 있습니다. 이 함수를 재정의 하는 경우 FALSE를 반환 하 여 속성 시트가 제거 되지 않도록 합니다.

사용자가 마법사 속성 시트에서 마침 단추를 누를 때 전송 되는 알림 메시지에 대 한 자세한 내용은 Windows SDK [PSN_WIZFINISH](/windows/win32/Controls/psn-wizfinish) 을 참조 하세요.

마법사 유형 속성 시트를 만드는 방법에 대 한 자세한 내용은 [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

## <a name="cpropertypageonwizardnext"></a><a name="onwizardnext"></a> CPropertyPage:: OnWizardNext

이 멤버 함수는 사용자가 마법사에서 다음 단추를 클릭할 때 프레임 워크에서 호출 됩니다.

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>반환 값

0은 자동으로 다음 페이지로 이동 합니다. -1은 페이지가 변경 되지 않도록 합니다. 다음 페이지로 이동 하려면 표시 되는 대화 상자의 식별자를 반환 합니다.

### <a name="remarks"></a>설명

다음 단추를 누를 때 사용자가 수행 해야 하는 동작을 지정 하려면이 멤버 함수를 재정의 합니다.

마법사 유형 속성 시트를 만드는 방법에 대 한 자세한 내용은 [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

## <a name="cpropertypagequerysiblings"></a><a name="querysiblings"></a> CPropertyPage:: QuerySiblings

이 멤버 함수를 호출 하 여 속성 시트의 각 페이지에 메시지를 전달 합니다.

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>매개 변수

*wParam*<br/>
추가 메시지 종속 정보를 지정 합니다.

*lParam*<br/>
추가 메시지 종속 정보를 지정 합니다.

### <a name="return-value"></a>반환 값

속성 시트의 페이지에서 0이 아닌 값을 반환 하거나, 모든 페이지가 값 0을 반환 하는 경우 0을 반환 합니다.

### <a name="remarks"></a>설명

페이지에서 0이 아닌 값을 반환 하면 속성 시트는 이후 페이지로 메시지를 보내지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

## <a name="cpropertypagesetmodified"></a><a name="setmodified"></a> CPropertyPage:: SetModified

속성 페이지의 설정이 적절 한 외부 개체에 적용 되어야 하는지 여부에 따라 [지금 적용] 단추를 사용 하거나 사용 하지 않도록 설정 하려면이 멤버 함수를 호출 합니다.

```cpp
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>매개 변수

*bChanged 됨*<br/>
마지막으로 적용 된 이후에 속성 페이지 설정이 수정 되었음을 나타내려면 TRUE이 고, 속성 페이지 설정이 적용 되었거나 무시 되어야 함을 나타내려면 FALSE입니다.

### <a name="remarks"></a>설명

프레임 워크는를 호출한 속성 페이지와 같은 "더티" 페이지를 추적 합니다 `SetModified( TRUE )` . 페이지 중 하나에 대해를 호출 하면 지금 적용 단추가 항상 사용 하도록 설정 됩니다 `SetModified( TRUE )` . 페이지 중 하나에 대해를 호출할 때 [지금 적용] 단추를 사용할 수 없습니다 `SetModified( FALSE )` . 단, 다른 페이지에는 "더티"가 없는 경우에만 적용 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CDialog 클래스](../../mfc/reference/cdialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CPropertySheet 클래스](../../mfc/reference/cpropertysheet-class.md)<br/>
[CDialog 클래스](../../mfc/reference/cdialog-class.md)
