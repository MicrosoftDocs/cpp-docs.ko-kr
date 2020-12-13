---
description: '자세한 정보: Cmfc추가 정보 클래스'
title: Cmfc의 Info 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo::m_uiColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuResID
helpviewer_keywords:
- CMFCToolBarInfo [MFC], m_uiColdResID
- CMFCToolBarInfo [MFC], m_uiDisabledResID
- CMFCToolBarInfo [MFC], m_uiHotResID
- CMFCToolBarInfo [MFC], m_uiLargeColdResID
- CMFCToolBarInfo [MFC], m_uiLargeDisabledResID
- CMFCToolBarInfo [MFC], m_uiLargeHotResID
- CMFCToolBarInfo [MFC], m_uiMenuDisabledResID
- CMFCToolBarInfo [MFC], m_uiMenuResID
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
ms.openlocfilehash: 9b85ef4f39c8b42c35975a15836a21e7cc6dd6b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331705"
---
# <a name="cmfctoolbarinfo-class"></a>Cmfc의 Info 클래스

다양한 상태의 도구 모음 이미지의 리소스 ID를 포함합니다. `CMFCToolBarInfo` 는 [Cmfctoolbar:: LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) 메서드의 매개 변수로 사용 되는 도우미 클래스입니다.

## <a name="syntax"></a>구문

```
class CMFCToolBarInfo
```

## <a name="members"></a>멤버

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[Cmfc작업 정보:: m_uiColdResID](#m_uicoldresid)|일반 (콜드) 도구 모음 이미지를 포함 하는 도구 모음 비트맵의 리소스 ID입니다.|
|[Cmfc작업 정보:: m_uiDisabledResID](#m_uidisabledresid)|비활성화 된 도구 모음 이미지를 포함 하는 도구 모음 비트맵의 리소스 ID입니다.|
|[Cmfc작업 정보:: m_uiHotResID](#m_uihotresid)|선택한 (핫) 도구 모음 이미지를 포함 하는 도구 모음 비트맵의 리소스 ID입니다.|
|[Cmfc작업 정보:: m_uiLargeColdResID](#m_uilargecoldresid)|크고 일반적인 도구 모음 이미지를 포함 하는 도구 모음 비트맵의 리소스 ID입니다.|
|[Cmfc작업 정보:: m_uiLargeDisabledResID](#m_uilargedisabledresid)|사용 하지 않도록 설정 된 크고 도구 모음 이미지를 포함 하는 도구 모음 비트맵의 리소스 ID입니다.|
|[Cmfc작업 정보:: m_uiLargeHotResID](#m_uilargehotresid)|선택 된 크기가 크고 선택 된 도구 모음 이미지를 포함 하는 도구 모음 비트맵의 리소스 ID입니다.|
|[Cmfc작업 정보:: m_uiMenuDisabledResID](#m_uimenudisabledresid)|비활성화 된 메뉴 이미지를 포함 하는 도구 모음 비트맵의 리소스 ID입니다.|
|[Cmfc작업 정보:: m_uiMenuResID](#m_uimenuresid)|메뉴 이미지를 포함 하는 도구 모음 비트맵의 리소스 ID입니다.|

## <a name="remarks"></a>설명

전체 도구 모음 비트맵은 고정 크기의 작은 도구 모음 이미지 (단추)로 구성 됩니다. 개체에 저장 된 각 리소스 ID는 `CMFCToolBarInfo` 도구 모음 이미지의 전체 집합을 단일 상태 (예: 선택, 사용 안 함, 크게 또는 메뉴 이미지)로 포함 하는 비트맵입니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxtoolbar

## <a name="cmfctoolbarinfom_uicoldresid"></a><a name="m_uicoldresid"></a> Cmfc작업 정보:: m_uiColdResID

도구 모음의 모든 일반 단추 이미지에 대 한 리소스 ID를 지정 합니다.

```
UINT m_uiColdResID;
```

## <a name="cmfctoolbarinfom_uidisabledresid"></a><a name="m_uidisabledresid"></a> Cmfc작업 정보:: m_uiDisabledResID

도구 모음의 단추를 사용할 수 없는 이미지에 대 한 리소스 ID를 지정 합니다.

```
UINT m_uiDisabledResID;
```

## <a name="cmfctoolbarinfom_uihotresid"></a><a name="m_uihotresid"></a> Cmfc작업 정보:: m_uiHotResID

도구 모음의 강조 표시 된 모든 단추 이미지에 대 한 리소스 ID를 지정 합니다.

```
UINT m_uiHotResID
```

## <a name="cmfctoolbarinfom_uilargecoldresid"></a><a name="m_uilargecoldresid"></a> Cmfc작업 정보:: m_uiLargeColdResID

도구 모음의 모든 긴 일반 단추 이미지에 대 한 리소스 ID를 지정 합니다.

```
UINT m_uiLargeColdResID
```

## <a name="cmfctoolbarinfom_uilargedisabledresid"></a><a name="m_uilargedisabledresid"></a> Cmfc작업 정보:: m_uiLargeDisabledResID

도구 모음의 모든 비활성화 된 단추 이미지에 대 한 리소스 ID를 지정 합니다.

```
UINT m_uiLargeDisabledResID;
```

## <a name="cmfctoolbarinfom_uilargehotresid"></a><a name="m_uilargehotresid"></a> Cmfc작업 정보:: m_uiLargeHotResID

도구 모음의 모든 강조 표시 된 이미지에 대 한 리소스 ID를 지정 합니다.

```
UINT m_uiLargeHotResID;
```

## <a name="cmfctoolbarinfom_uimenudisabledresid"></a><a name="m_uimenudisabledresid"></a> Cmfc작업 정보:: m_uiMenuDisabledResID

도구 모음의 명령에서 사용할 수 없는 이미지에 대 한 리소스 ID를 지정 합니다.

```
UINT m_uiMenuDisabledResID;
```

## <a name="cmfctoolbarinfom_uimenuresid"></a><a name="m_uimenuresid"></a> Cmfc작업 정보:: m_uiMenuResID

도구 모음의 모든 일반 메뉴 항목 이미지에 대 한 리소스 ID를 지정 합니다.

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)
