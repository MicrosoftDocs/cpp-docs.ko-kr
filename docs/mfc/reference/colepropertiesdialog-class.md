---
description: '자세히 알아보기: Cole의 대화 상자 클래스'
title: Cole인 대화 상자 클래스
ms.date: 11/04/2016
f1_keywords:
- COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::DoModal
- AFXODLGS/COlePropertiesDialog::OnApplyScale
- AFXODLGS/COlePropertiesDialog::m_gp
- AFXODLGS/COlePropertiesDialog::m_lp
- AFXODLGS/COlePropertiesDialog::m_op
- AFXODLGS/COlePropertiesDialog::m_psh
- AFXODLGS/COlePropertiesDialog::m_vp
helpviewer_keywords:
- COlePropertiesDialog [MFC], COlePropertiesDialog
- COlePropertiesDialog [MFC], DoModal
- COlePropertiesDialog [MFC], OnApplyScale
- COlePropertiesDialog [MFC], m_gp
- COlePropertiesDialog [MFC], m_lp
- COlePropertiesDialog [MFC], m_op
- COlePropertiesDialog [MFC], m_psh
- COlePropertiesDialog [MFC], m_vp
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
ms.openlocfilehash: f0c102412f422ff0eabc9f1ff8e19901845905e8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226768"
---
# <a name="colepropertiesdialog-class"></a>Cole인 대화 상자 클래스

Windows 공용 OLE 개체 속성 대화 상자를 캡슐화합니다.

## <a name="syntax"></a>구문

```
class COlePropertiesDialog : public COleDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[Cole인 대화 상자:: Cole의 대화 상자](#colepropertiesdialog)|`COlePropertiesDialog` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Cole인 대화 상자::D oModal](#domodal)|대화 상자를 표시 하 고 사용자가 선택할 수 있게 합니다.|
|[ColeOnApplyScale 대화 상자::](#onapplyscale)|문서 항목의 크기가 변경 될 때 프레임 워크에서 호출 됩니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[Cole인 대화 상자:: m_gp](#m_gp)|개체의 "일반" 페이지를 초기화 하는 데 사용 되는 구조체 `COlePropertiesDialog` 입니다.|
|[Cole인 대화 상자:: m_lp](#m_lp)|개체의 "링크" 페이지를 초기화 하는 데 사용 되는 구조체 `COlePropertiesDialog` 입니다.|
|[Cole인 대화 상자:: m_op](#m_op)|개체를 초기화 하는 데 사용 되는 구조체 `COlePropertiesDialog` 입니다.|
|[Cole인 대화 상자:: m_psh](#m_psh)|사용자 지정 속성 페이지를 추가 하는 데 사용 되는 구조체입니다.|
|[Cole인 대화 상자:: m_vp](#m_vp)|개체의 "뷰" 페이지를 사용자 지정 하는 데 사용 되는 구조체 `COlePropertiesDialog` 입니다.|

## <a name="remarks"></a>설명

일반적인 OLE 개체 속성 대화 상자를 사용 하면 Windows 표준과 일관 된 방식으로 OLE 문서 항목의 속성을 쉽게 표시 하 고 수정할 수 있습니다. 이러한 속성으로는 문서 항목으로 표시 되는 파일에 대 한 정보, 아이콘 및 이미지 크기 조정을 표시 하는 옵션, 항목 링크에 대 한 정보 (항목이 링크 된 경우) 등이 있습니다.

개체를 사용 하려면 `COlePropertiesDialog` 먼저 생성자를 사용 하 여 개체를 만듭니다 `COlePropertiesDialog` . 대화 상자를 생성 한 후에는 `DoModal` 멤버 함수를 호출 하 여 대화 상자를 표시 하 고 사용자가 항목의 모든 속성을 수정할 수 있습니다. `DoModal` 사용자가 [확인] (IDOK) 또는 [취소] (IDCANCEL) 단추를 선택 했는지 여부를 반환 합니다. 확인 및 취소 단추 외에도 적용 단추가 있습니다. 사용자가 적용을 선택 하면 문서 항목의 속성에 대 한 변경 내용이 항목에 적용 되 고 해당 이미지는 자동으로 업데이트 되지만 활성 상태로 유지 됩니다.

[M_psh](#m_psh) 데이터 멤버는 구조체에 대 한 포인터 `PROPSHEETHEADER` 이며, 대부분의 경우 명시적으로 액세스할 필요가 없습니다. 한 가지 예외는 기본 일반, 보기 및 링크 페이지를 벗어나는 추가 속성 페이지가 필요한 경우입니다. 이 경우 `m_psh` 멤버 함수를 호출 하기 전에 사용자 지정 페이지를 포함 하도록 데이터 멤버를 수정할 수 있습니다 `DoModal` .

OLE 대화 상자에 대 한 자세한 내용은 [ole의 아티클 대화 상자](../../mfc/dialog-boxes-in-ole.md)를 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxodlgs

## <a name="colepropertiesdialogcolepropertiesdialog"></a><a name="colepropertiesdialog"></a> Cole인 대화 상자:: Cole의 대화 상자

`COlePropertiesDialog` 개체를 만듭니다.

```
COlePropertiesDialog(
    COleClientItem* pItem,
    UINT nScaleMin = 10,
    UINT nScaleMax = 500,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*pItem*<br/>
속성이 액세스 되는 문서 항목에 대 한 포인터입니다.

*nScaleMin*<br/>
문서 항목 이미지의 최소 배율 비율입니다.

*nScaleMax*<br/>
문서 항목 이미지의 최대 배율 비율입니다.

*pParentWnd*<br/>
대화 상자의 부모 또는 소유자에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`COlePropertiesDialog`문서 항목에 대 한 크기 조정을 구현 하기 위해에서 일반적인 OLE 개체 속성 대화 상자 클래스를 파생 합니다. 이 클래스의 인스턴스에서 구현 하는 모든 대화 상자는 문서 항목의 크기 조정을 지원 하지 않습니다.

기본적으로 일반 OLE 개체 속성 대화 상자에는 다음과 같은 세 가지 기본 페이지가 있습니다.

- 일반

   이 페이지에는 선택한 문서 항목으로 표시 되는 파일에 대 한 시스템 정보가 포함 되어 있습니다. 이 페이지에서 사용자는 선택한 항목을 다른 형식으로 변환할 수 있습니다.

- 보기

   이 페이지에는 항목을 표시 하 고, 아이콘을 변경 하 고, 이미지의 크기를 변경 하는 옵션이 포함 되어 있습니다.

- 링크

   이 페이지에는 연결 된 항목의 위치를 변경 하 고 연결 된 항목을 업데이트 하는 옵션이 포함 되어 있습니다. 이 페이지에서 사용자는 선택한 항목의 링크를 중단할 수 있습니다.

기본적으로 제공 되는 것 보다 많은 페이지를 추가 하려면 파생 클래스의 생성자를 끝내기 전에 [m_psh](#m_psh) 멤버 변수를 수정 합니다 `COlePropertiesDialog` . 이는 생성자의 고급 구현입니다 `COlePropertiesDialog` .

## <a name="colepropertiesdialogdomodal"></a><a name="domodal"></a> Cole인 대화 상자::D oModal

이 멤버 함수를 호출 하 여 Windows 공용 OLE 개체 속성 대화 상자를 표시 하 고 사용자가 문서 항목의 다양 한 속성을 보거나 변경할 수 있습니다.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>반환 값

성공 하는 경우 IDOK 또는 IDCANCEL 그렇지 않으면 0입니다. IDOK 및 IDCANCEL는 사용자가 확인 또는 취소 단추를 선택 했는지 여부를 나타내는 상수입니다.

IDCANCEL이 반환 되는 경우 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) 함수를 호출 하 여 오류가 발생 했는지 여부를 확인할 수 있습니다.

## <a name="colepropertiesdialogm_gp"></a><a name="m_gp"></a> Cole인 대화 상자:: m_gp

OLE 개체 속성 대화 상자의 일반 페이지를 초기화 하는 데 사용 되는 [OLEUIGNRLPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuignrlpropsw)형식의 구조입니다.

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>설명

이 페이지는 포함의 유형 및 크기를 표시 하 고 사용자가 변환 대화 상자에 액세스할 수 있도록 합니다. 이 페이지에는 개체가 링크인 경우 링크 대상도 표시 됩니다.

구조체에 대 한 자세한 내용은 `OLEUIGNRLPROPS` Windows SDK를 참조 하세요.

## <a name="colepropertiesdialogm_lp"></a><a name="m_lp"></a> Cole인 대화 상자:: m_lp

OLE 개체 속성 대화 상자의 링크 페이지를 초기화 하는 데 사용 되는 [OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw)형식의 구조입니다.

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>설명

이 페이지에서는 연결 된 항목의 위치를 표시 하 고 사용자가 항목에 대 한 링크를 업데이트 하거나 중단할 수 있습니다.

구조체에 대 한 자세한 내용은 `OLEUILINKPROPS` Windows SDK를 참조 하세요.

## <a name="colepropertiesdialogm_op"></a><a name="m_op"></a> Cole인 대화 상자:: m_op

공용 OLE 개체 속성 대화 상자를 초기화 하는 데 사용 되는 [OLEUIOBJECTPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiobjectpropsw)형식의 구조입니다.

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>설명

이 구조는 일반, 링크 및 보기 페이지를 초기화 하는 데 사용 되는 멤버를 포함 합니다.

자세한 내용은 Windows SDK OLEUIOBJECTPROPS and [OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw) 구조체를 참조 하십시오.

## <a name="colepropertiesdialogm_psh"></a><a name="m_psh"></a> Cole인 대화 상자:: m_psh

해당 멤버가 dialog 개체의 특성을 저장 하는 [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)형식의 구조체입니다.

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>설명

개체를 생성 한 후에는 `COlePropertiesDialog` `m_psh` 멤버 함수를 호출 하기 전에를 사용 하 여 대화 상자의 다양 한 측면을 설정할 수 있습니다 `DoModal` .

데이터 멤버를 직접 수정 하는 경우 `m_psh` 모든 기본 동작을 재정의 합니다.

구조체에 대 한 자세한 내용은 `PROPSHEETHEADER` Windows SDK를 참조 하세요.

## <a name="colepropertiesdialogm_vp"></a><a name="m_vp"></a> Cole인 대화 상자:: m_vp

OLE 개체 속성 대화 상자의 뷰 페이지를 초기화 하는 데 사용 되는 [OLEUIVIEWPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiviewpropsw)형식의 구조입니다.

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>설명

이 페이지에서는 사용자가 개체의 "콘텐츠" 및 "아이콘" 뷰를 전환 하 고 컨테이너 내에서 크기를 변경할 수 있습니다. 또한 개체를 아이콘으로 표시 하는 경우 사용자가 아이콘 변경 대화 상자에 액세스할 수 있습니다.

구조체에 대 한 자세한 내용은 `OLEUIVIEWPROPS` Windows SDK를 참조 하세요.

## <a name="colepropertiesdialogonapplyscale"></a><a name="onapplyscale"></a> ColeOnApplyScale 대화 상자::

크기 조정 값이 변경 되 고 확인 또는 적용이 선택 된 경우 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>매개 변수

*pItem*<br/>
속성이 액세스 되는 문서 항목에 대 한 포인터입니다.

*nCurrentScale*<br/>
대화 상자 크기의 숫자 값입니다.

*bRelativeToOrig*<br/>
크기 조정이 문서 항목의 원래 크기에 적용 되는지 여부를 나타냅니다.

### <a name="return-value"></a>반환 값

처리 되는 경우 0이 아님 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

기본 구현은 아무 작업도 수행하지 않습니다. 크기 조정 컨트롤을 사용 하려면이 함수를 재정의 해야 합니다.

> [!NOTE]
> 일반 OLE 개체 속성 대화 상자가 표시 되기 전에 프레임 워크는 *Pitem* 의 경우 NULL로, *ncurrentscale* 의 경우-1을 사용 하 여이 함수를 호출 합니다. 크기 조정 컨트롤을 사용 하도록 설정 해야 하는지 여부를 결정 하기 위해이 작업이 수행 됩니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 CIRC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 클래스](../../mfc/reference/coledialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 클래스](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage 클래스](../../mfc/reference/cpropertypage-class.md)
