---
description: '자세히 알아보기: CSmartDockingInfo 클래스'
title: CSmartDockingInfo 클래스
ms.date: 11/19/2018
f1_keywords:
- CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo::CopyTo
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_bUseThemeColorInShading
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrBaseBackground
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneDest
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneSrc
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrTransparent
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_nCentralGroupOffset
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_sizeTotal
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerBmpResID
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerLightBmpResID
helpviewer_keywords:
- CSmartDockingInfo [MFC], CopyTo
- CSmartDockingInfo [MFC], m_bUseThemeColorInShading
- CSmartDockingInfo [MFC], m_clrBaseBackground
- CSmartDockingInfo [MFC], m_clrToneDest
- CSmartDockingInfo [MFC], m_clrToneSrc
- CSmartDockingInfo [MFC], m_clrTransparent
- CSmartDockingInfo [MFC], m_nCentralGroupOffset
- CSmartDockingInfo [MFC], m_sizeTotal
- CSmartDockingInfo [MFC], m_uiMarkerBmpResID
- CSmartDockingInfo [MFC], m_uiMarkerLightBmpResID
ms.assetid: cab04f38-4bc1-4378-9337-c56fc87fbd68
ms.openlocfilehash: 290f9eef208ceed425739ab26e7811c04309e057
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345136"
---
# <a name="csmartdockinginfo-class"></a>CSmartDockingInfo 클래스

스마트 도킹 표식의 모양을 정의합니다.

## <a name="syntax"></a>구문

```
class CSmartDockingInfo : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CSmartDockingInfo::CSmartDockingInfo`|기본 생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSmartDockingInfo:: CopyTo](#copyto)|현재 스마트 도킹 정보 매개 변수를 제공 된 [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) 개체에 복사 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CSmartDockingInfo:: m_bUseThemeColorInShading](#m_busethemecolorinshading)|프레임 워크에서 스마트 도킹 표식을 표시할 때 현재 테마 색을 사용할지 여부를 지정 합니다.|
|[CSmartDockingInfo:: m_clrBaseBackground](#m_clrbasebackground)|스마트 도킹 표식의 기본 배경색을 지정 합니다.|
|[CSmartDockingInfo:: m_clrToneDest](#m_clrtonedest)|스마트 도킹 표식 비트맵에서 대체 되는 색을 지정 합니다 `m_clrToneSrc` .|
|[CSmartDockingInfo:: m_clrToneSrc](#m_clrtonesrc)|스마트 도킹 표식 비트맵의 색을 지정 합니다.|
|[CSmartDockingInfo:: m_clrTransparent](#m_clrtransparent)|투명 한 경우 스마트 도킹 표식 비트맵의 색을 지정 합니다.|
|[CSmartDockingInfo:: m_nCentralGroupOffset](#m_ncentralgroupoffset)|중앙 그룹 사각형의 경계에서 스마트 도킹 표식의 중앙 그룹의 오프셋을 지정 합니다.|
|[CSmartDockingInfo:: m_sizeTotal](#m_sizetotal)|그룹에 있는 모든 스마트 도킹 표식의 전체 크기를 지정 합니다.|
|[CSmartDockingInfo:: m_uiMarkerBmpResID](#m_uimarkerbmpresid)|프레임 워크가 강조 표시 되지 않은 스마트 도킹 표식에 사용 하는 비트맵의 리소스 Id를 정의 합니다.|
|[CSmartDockingInfo:: m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|프레임 워크가 강조 표시 된 스마트 도킹 표식에 사용 하는 비트맵의 리소스 Id를 정의 합니다.|

## <a name="remarks"></a>설명

프레임 워크는 내부적으로 스마트 도킹 표식을 처리 합니다. 다음 그림에서는 표준 스마트 도킹 표식을 보여 줍니다.

![스마트 도킹의 표준 마커](../../mfc/reference/media/nextsdmarkers.png "스마트 도킹의 표준 마커")

이 그림에서 왼쪽 이미지는 탭에 대 한 도킹을 사용 하지 않는 중앙 그룹 스마트 도킹 표식을 보여 줍니다. 가운데에 있는 이미지는 오른쪽 가장자리 스마트 도킹 표식을 보여 줍니다. 오른쪽의 이미지에는 탭에 도킹할 수 있는 중앙 그룹 스마트 도킹 표식이 표시 됩니다. 중앙 그룹 스마트 도킹 표식에는 주 비트맵과 5 개의 스마트 도킹 표식 비트맵이 있습니다.

스마트 도킹 표식의 다음 매개 변수를 사용자 지정할 수 있습니다.

- 색 예를 들어, 그림에서 표식의 파란색 색을 사용자 정의 색으로 바꿀 수 있습니다.

- 투명도 색입니다.

- 경계 사각형의 테두리에서 중앙 그룹의 스마트 도킹 표식 오프셋입니다.

- 중앙 그룹을 나타내는 기본 비트맵입니다.

- 일반 및 강조 표시 된 스마트 도킹 표식을 나타내는 비트맵입니다.

다음 그림은 사용자 지정 된 스마트 도킹 표식의 예를 보여 줍니다.

![스마트 도킹의 사용자 지정 마커](../../mfc/reference/media/nextsdmarkerscustom.png "스마트 도킹의 사용자 지정 마커")

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxDockingManager

## <a name="csmartdockinginfocopyto"></a><a name="copyto"></a> CSmartDockingInfo:: CopyTo

현재 스마트 도킹 매개 변수를 제공 된 [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) 개체에 복사 합니다.

```cpp
void CopyTo(CSmartDockingInfo& params);
```

### <a name="parameters"></a>매개 변수

*params*<br/>
제한이 `CSmartDockingInfo` 현재 스마트 도킹 매개 변수로 채워지는 형식의 개체입니다.

## <a name="csmartdockinginfom_busethemecolorinshading"></a><a name="m_busethemecolorinshading"></a> CSmartDockingInfo:: m_bUseThemeColorInShading

프레임 워크에서 스마트 도킹 표식을 표시할 때 현재 테마 색을 사용할지 여부를 지정 합니다.

```
BOOL m_bUseThemeColorInShading;
```

### <a name="remarks"></a>설명

TRUE 이면 현재 테마 색을 사용 하 여 표식이 그려집니다. 그렇지 않으면 표식이 연한 파란색으로 그려집니다.

기본값은 FALSE입니다.

## <a name="csmartdockinginfom_clrbasebackground"></a><a name="m_clrbasebackground"></a> CSmartDockingInfo:: m_clrBaseBackground

스마트 도킹 표식의 기본 배경색을 지정 합니다.

```
COLORREF m_clrBaseBackground;
```

## <a name="csmartdockinginfom_clrtonedest"></a><a name="m_clrtonedest"></a> CSmartDockingInfo:: m_clrToneDest

`m_clrToneSrc`스마트 도킹 표식 비트맵에서 바꿀 색을 지정 합니다.

```
COLORREF m_clrToneDest;
```

### <a name="remarks"></a>설명

표식 비트맵의 색을 프로그래밍 방식으로 변경 하려면이 값을 설정 합니다. 예를 들어 프레임 워크에서 제공 하는 표준 표식의 색을 변경 하려면이 값을 원하는 색으로 설정 합니다. 기본적으로 [CSmartDockingInfo:: m_clrToneSrc](#m_clrtonesrc) 는 RGB (61, 123, 241) (bluish color)로 설정 됩니다.

사용자 지정 표식의 색을 변경 하려면 및를 모두 지정 해야 `m_clrToneDest` 합니다 `m_clrToneSrc` .

## <a name="csmartdockinginfom_clrtonesrc"></a><a name="m_clrtonesrc"></a> CSmartDockingInfo:: m_clrToneSrc

스마트 도킹 표식 비트맵의 색을 지정 합니다.

```
COLORREF m_clrToneSrc;
```

### <a name="remarks"></a>설명

사용자 지정 비트맵의 색을 다른 색으로 바꾸려는 경우에만이 값을 설정 합니다. 표준 (프레임 워크 제공) 표식의 색을 변경 하는 경우에는이 값을 설정할 필요가 없습니다.

`(COLORREF)-1`스마트 도킹 그룹의 멤버를 빈 상태로 두려면를 사용 합니다.

## <a name="csmartdockinginfom_clrtransparent"></a><a name="m_clrtransparent"></a> CSmartDockingInfo:: m_clrTransparent

투명 한 경우 스마트 도킹 표식 비트맵의 색을 지정 합니다.

```
COLORREF m_clrTransparent;
```

### <a name="remarks"></a>설명

도킹 그룹에 사용자 지정 표식 및 사용자 지정 비트맵을 표시 하는 경우이 값을 설정 해야 합니다.

## <a name="csmartdockinginfom_ncentralgroupoffset"></a><a name="m_ncentralgroupoffset"></a> CSmartDockingInfo:: m_nCentralGroupOffset

스마트 도킹 표식의 중앙 그룹과 중앙 그룹 사각형의 경계 사이의 오프셋을 지정 합니다.

```
int m_nCentralGroupOffset;
```

### <a name="remarks"></a>설명

사용자 지정 표식과 기본 고정 표식의 중앙 그룹 경계 사이의 기본 오프셋을 변경 하려면이 값을 지정 합니다. 기본 오프셋은 5 픽셀입니다.

## <a name="csmartdockinginfom_sizetotal"></a><a name="m_sizetotal"></a> CSmartDockingInfo:: m_sizeTotal

중앙 그룹의 모든 스마트 도킹 표식을 둘러싸는 경계 사각형의 전체 크기를 지정 합니다.

```
CSize m_sizeTotal;
```

### <a name="remarks"></a>설명

`m_sizeTotal`중앙 그룹 표식의 경계 사각형 크기로 설정 합니다. 표식에 대 한 사용자 지정 비트맵을 사용 하는 경우이 값을 지정 해야 합니다.

## <a name="csmartdockinginfom_uimarkerbmpresid"></a><a name="m_uimarkerbmpresid"></a> CSmartDockingInfo:: m_uiMarkerBmpResID

강조 표시 되지 않은 사용자 지정 스마트 도킹 표식에 사용 되는 비트맵의 리소스 Id를 정의 합니다.

```
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>설명

스마트 도킹 표식을 나타내는 비트맵의 리소스 Id로이 배열을 채웁니다. AFX_SD_MARKERS_NUM 현재 5로 정의 되어 있습니다. 다음과 같이 배열을 채웁니다.

```cpp
params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;
params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;
params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;
params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;
params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;
```

## <a name="csmartdockinginfom_uimarkerlightbmpresid"></a><a name="m_uimarkerlightbmpresid"></a> CSmartDockingInfo:: m_uiMarkerLightBmpResID

강조 표시 된 사용자 지정 스마트 도킹 표식에 사용 되는 비트맵의 리소스 Id를 정의 합니다.

```
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>설명

강조 표시 된 스마트 도킹 표식을 나타내는 비트맵의 리소스 Id로이 배열을 채웁니다. AFX_SD_MARKERS_NUM 현재 5로 정의 되어 있습니다. 다음과 같이 배열을 채웁니다.

```cpp
params.m_uiMarkerLightBmpResID[0] = IDB_MARKER_LEFT_LIGHT;
params.m_uiMarkerLightBmpResID[1] = IDB_MARKER_RIGHT_LIGHT;
params.m_uiMarkerLightBmpResID[2] = IDB_MARKER_TOP_LIGHT;
params.m_uiMarkerLightBmpResID[3] = IDB_MARKER_BOTTOM_LIGHT;
params.m_uiMarkerLightBmpResID[4] = IDB_MARKER_CENTER_LIGHT;
```

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)
