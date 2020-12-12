---
description: '자세히 알아보기: CMFCTabToolTipInfo Structure'
title: CMFCTabToolTipInfo 구조체
ms.date: 11/04/2016
f1_keywords:
- CMFCTabToolTipInfo
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
ms.openlocfilehash: ce9e9f4fdbcf367921e7f0559a4d04e66f4303dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164070"
---
# <a name="cmfctabtooltipinfo-structure"></a>CMFCTabToolTipInfo 구조체

이 구조는 사용자가 가리키고 있는 MDI 탭에 대 한 정보를 제공 합니다.

## <a name="syntax"></a>구문

```
struct CMFCTabToolTipInfo
```

## <a name="members"></a>멤버

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CMFCTabToolTipInfo:: m_nTabIndex](#m_ntabindex)|탭 컨트롤의 인덱스를 지정 합니다.|
|[CMFCTabToolTipInfo:: m_pTabWnd](#m_ptabwnd)|탭 컨트롤에 대 한 포인터입니다.|
|[CMFCTabToolTipInfo:: m_strText](#m_strtext)|도구 설명 텍스트입니다.|

## <a name="remarks"></a>설명

구조체에 대 한 포인터는 `CMFCTabToolTipInfo` AFX_WM_ON_GET_TAB_TOOLTIP 메시지의 매개 변수로 전달 됩니다. 이 메시지는 MDI 탭을 사용 하도록 설정 하 고 사용자가 탭 컨트롤을 마우스로 가리킬 때 생성 됩니다.

## <a name="example"></a>예제

다음 예제에서는 `CMFCTabToolTipInfo` [MDITabsDemo 샘플: MFC 탭 MDI 응용 프로그램](../../overview/visual-cpp-samples.md)에서를 사용 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxbasetabctrl.h

## <a name="cmfctabtooltipinfom_ntabindex"></a><a name="m_ntabindex"></a> CMFCTabToolTipInfo:: m_nTabIndex

탭 컨트롤의 인덱스를 지정 합니다.

```
int m_nTabIndex;
```

### <a name="remarks"></a>설명

사용자가 가리키고 있는 탭의 인덱스입니다.

### <a name="example"></a>예제

다음 예제에서는 `m_nTabIndex` [MDITabsDemo 샘플: MFC 탭 MDI 응용 프로그램](../../overview/visual-cpp-samples.md)에서를 사용 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_ptabwnd"></a><a name="m_ptabwnd"></a> CMFCTabToolTipInfo:: m_pTabWnd

탭 컨트롤에 대 한 포인터입니다.

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>예제

다음 예제에서는 `m_pTabWnd` [MDITabsDemo 샘플: MFC 탭 MDI 응용 프로그램](../../overview/visual-cpp-samples.md)에서를 사용 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_strtext"></a><a name="m_strtext"></a> CMFCTabToolTipInfo:: m_strText

도구 설명 텍스트입니다.

```
CString m_strText;
```

### <a name="remarks"></a>설명

문자열이 비어 있으면 도구 설명이 표시 되지 않습니다.

### <a name="example"></a>예제

다음 예제에서는 `m_strText` [MDITabsDemo 샘플: MFC 탭 MDI 응용 프로그램](../../overview/visual-cpp-samples.md)에서를 사용 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)
