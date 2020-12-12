---
description: '자세히 알아보기: 사용 되지 않는 ANSI Api'
title: 사용되지 않는 ANSI API
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, ANSI deprecated methods
ms.assetid: c7c5a6fd-95e4-4bee-b3d5-d3826c30947d
ms.openlocfilehash: b709e67a032a25335fe6d05b3662db264232193c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290988"
---
# <a name="deprecated-ansi-apis"></a>사용되지 않는 ANSI API

MFC (Microsoft Foundation Class) 라이브러리는 유니코드 문자 집합을 기반으로 하는 클래스 및 메서드로 마이그레이션됩니다. 따라서 여러 MFC 메서드의 ANSI 버전은 더 이상 사용 되지 않습니다. 이후 응용 프로그램에서 이러한 메서드의 유니코드 버전을 사용 합니다.

Windows 공용 컨트롤 버전 6.1부터 Windows Vista에서 제공 되는 다음 ANSI 메서드는 더 이상 사용 되지 않습니다.

## <a name="cbutton-class"></a>CButton 클래스

```
AFX_ANSI_DEPRECATED BOOL GetIdealSize(LPSIZE psize) const;

AFX_ANSI_DEPRECATED BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist) const;

AFX_ANSI_DEPRECATED BOOL GetTextMargin(LPRECT pmargin) const;

AFX_ANSI_DEPRECATED BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);

AFX_ANSI_DEPRECATED BOOL SetTextMargin(LPRECT pmargin);
```

## <a name="ccomboboxex-class"></a>CComboBoxEx 클래스

```
AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

## <a name="cedit-class"></a>CEdit 클래스

```
AFX_ANSI_DEPRECATED BOOL GetCueBanner(LPWSTR lpszText,
    int cchText) const;

AFX_ANSI_DEPRECATED BOOL SetCueBanner(LPCWSTR lpszText,
    BOOL fDrawIfFocused = FALSE);
```

## <a name="clinkctrl-class"></a>CLinkCtrl 클래스

전체 클래스는 더 이상 사용 되지 않습니다.

## <a name="clistctrl-class"></a>CListCtrl 클래스

```
AFX_ANSI_DEPRECATED void CancelEditLabel();

AFX_ANSI_DEPRECATED int EnableGroupView(BOOL fEnable);

AFX_ANSI_DEPRECATED int GetGroupInfo(int iGroupId,
    PLVGROUP pgrp) const;

AFX_ANSI_DEPRECATED void GetGroupMetrics(PLVGROUPMETRICS pGroupMetrics) const;

AFX_ANSI_DEPRECATED BOOL GetInsertMark(LPLVINSERTMARK lvim) const;

AFX_ANSI_DEPRECATED COLORREF GetInsertMarkColor() const;

AFX_ANSI_DEPRECATED int GetInsertMarkRect(LPRECT pRect) const;

AFX_ANSI_DEPRECATED COLORREF GetOutlineColor() const;

AFX_ANSI_DEPRECATED UINT GetSelectedColumn() const;

AFX_ANSI_DEPRECATED BOOL GetTileInfo(PLVTILEINFO pti) const;

AFX_ANSI_DEPRECATED BOOL GetTileViewInfo(PLVTILEVIEWINFO ptvi) const;

AFX_ANSI_DEPRECATED DWORD GetView() const;

AFX_ANSI_DEPRECATED BOOL HasGroup(int iGroupId) const;

AFX_ANSI_DEPRECATED int InsertGroup(int index,
    PLVGROUP pgrp);

AFX_ANSI_DEPRECATED void InsertGroupSorted(PLVINSERTGROUPSORTED pStructInsert);

AFX_ANSI_DEPRECATED int InsertMarkHitTest(LPPOINT pPoint,
    LPLVINSERTMARK lvim) const;

AFX_ANSI_DEPRECATED BOOL IsGroupViewEnabled() const;

AFX_ANSI_DEPRECATED void MoveGroup(int iGroupId,
    int toIndex);

AFX_ANSI_DEPRECATED void MoveItemToGroup(int idItemFrom,
    int idGroupTo);

AFX_ANSI_DEPRECATED void RemoveAllGroups();

AFX_ANSI_DEPRECATED int RemoveGroup(int iGroupId);

AFX_ANSI_DEPRECATED BOOL SetGroupInfo(int iGroupId,
    PLVGROUP pGroup);

AFX_ANSI_DEPRECATED void SetGroupMetrics(PLVGROUPMETRICS pGroupMetrics);

AFX_ANSI_DEPRECATED BOOL SetInfoTip(PLVSETINFOTIP plvInfoTip);

AFX_ANSI_DEPRECATED BOOL SetInsertMark(LPLVINSERTMARK lvim);

AFX_ANSI_DEPRECATED COLORREF SetInsertMarkColor(COLORREF color);

AFX_ANSI_DEPRECATED COLORREF SetOutlineColor(COLORREF color);

AFX_ANSI_DEPRECATED void SetSelectedColumn(int iCol);

AFX_ANSI_DEPRECATED BOOL SetTileInfo(PLVTILEINFO pti);

AFX_ANSI_DEPRECATED BOOL SetTileViewInfo(PLVTILEVIEWINFO ptvi);

AFX_ANSI_DEPRECATED DWORD SetView(int iView);

AFX_ANSI_DEPRECATED BOOL SortGroups(PFNLVGROUPCOMPARE _pfnGroupCompare,
    LPVOID _plv);
```

## <a name="crebarctrl-class"></a>CReBarCtrl 클래스

```
AFX_ANSI_DEPRECATED void GetBandMargins(PMARGINS pMargins) const;

AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

## <a name="ctoolbarctrl-class"></a>CToolBarCtrl 클래스

```
AFX_ANSI_DEPRECATED void GetMetrics(LPTBMETRICS ptbm) const;

AFX_ANSI_DEPRECATED void SetMetrics(LPTBMETRICS ptbm);

AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

## <a name="ctooltipctrl-class"></a>CToolTipCtrl 클래스

```
AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

## <a name="see-also"></a>참고 항목

[Windows Vista 공용 컨트롤의 빌드 요구 사항](build-requirements-for-windows-vista-common-controls.md)
