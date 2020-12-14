---
description: '자세히 알아보기: CDrawingManager 클래스'
title: CDrawingManager 클래스
ms.date: 11/04/2016
f1_keywords:
- CDrawingManager
- AFXDRAWMANAGER/CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CreateBitmap_32
- AFXDRAWMANAGER/CDrawingManager::DrawAlpha
- AFXDRAWMANAGER/CDrawingManager::DrawRotated
- AFXDRAWMANAGER/CDrawingManager::DrawEllipse
- AFXDRAWMANAGER/CDrawingManager::DrawGradientRing
- AFXDRAWMANAGER/CDrawingManager::DrawRect
- AFXDRAWMANAGER/CDrawingManager::DrawShadow
- AFXDRAWMANAGER/CDrawingManager::Fill4ColorsGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient2
- AFXDRAWMANAGER/CDrawingManager::GrayRect
- AFXDRAWMANAGER/CDrawingManager::HighlightRect
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_ONE
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_TWO
- AFXDRAWMANAGER/CDrawingManager::HSVtoRGB
- AFXDRAWMANAGER/CDrawingManager::HuetoRGB
- AFXDRAWMANAGER/CDrawingManager::MirrorRect
- AFXDRAWMANAGER/CDrawingManager::PixelAlpha
- AFXDRAWMANAGER/CDrawingManager::PrepareShadowMask
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSL
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSV
- AFXDRAWMANAGER/CDrawingManager::SetAlphaPixel
- AFXDRAWMANAGER/CDrawingManager::SetPixel
- AFXDRAWMANAGER/CDrawingManager::SmartMixColors
helpviewer_keywords:
- CDrawingManager [MFC], CDrawingManager
- CDrawingManager [MFC], CreateBitmap_32
- CDrawingManager [MFC], DrawAlpha
- CDrawingManager [MFC], DrawRotated
- CDrawingManager [MFC], DrawEllipse
- CDrawingManager [MFC], DrawGradientRing
- CDrawingManager [MFC], DrawRect
- CDrawingManager [MFC], DrawShadow
- CDrawingManager [MFC], Fill4ColorsGradient
- CDrawingManager [MFC], FillGradient
- CDrawingManager [MFC], FillGradient2
- CDrawingManager [MFC], GrayRect
- CDrawingManager [MFC], HighlightRect
- CDrawingManager [MFC], HLStoRGB_ONE
- CDrawingManager [MFC], HLStoRGB_TWO
- CDrawingManager [MFC], HSVtoRGB
- CDrawingManager [MFC], HuetoRGB
- CDrawingManager [MFC], MirrorRect
- CDrawingManager [MFC], PixelAlpha
- CDrawingManager [MFC], PrepareShadowMask
- CDrawingManager [MFC], RGBtoHSL
- CDrawingManager [MFC], RGBtoHSV
- CDrawingManager [MFC], SetAlphaPixel
- CDrawingManager [MFC], SetPixel
- CDrawingManager [MFC], SmartMixColors
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
ms.openlocfilehash: b30218dd41e3591c4a39df078bb19e3ac653ba1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184792"
---
# <a name="cdrawingmanager-class"></a>CDrawingManager 클래스

`CDrawingManager`클래스는 복잡 한 그리기 알고리즘을 구현 합니다.

## <a name="syntax"></a>구문

```
class CDrawingManager : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|`CDrawingManager` 개체를 생성합니다.|
|`CDrawingManager::~CDrawingManager`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDrawingManager:: CreateBitmap_32](#createbitmap_32)|응용 프로그램에서 직접 쓸 수 있는 32 비트 DIB (장치 독립적 비트맵)를 만듭니다.|
|[CDrawingManager::D rawAlpha](#drawalpha)|투명 또는 반투명 픽셀의 비트맵이 표시 됩니다.|
|[CDrawingManager::D rawRotated](#drawrotated)|소스 DC 콘텐츠를 지정 된 사각형 내에서 +/-90 각도로 회전 합니다.|
|[CDrawingManager::D rawEllipse](#drawellipse)|제공 된 채우기 및 테두리 색을 사용 하 여 타원을 그립니다.|
|[CDrawingManager::D rawGradientRing](#drawgradientring)|링을 그리고 색 그라데이션으로 채웁니다.|
|[CDrawingManager::D rawLine, CDrawingManager::D rawLineA](#drawline_cdrawingmanager__drawlinea)|선을 그립니다.|
|[CDrawingManager::D rawRect](#drawrect)|제공 된 채우기 및 테두리 색을 사용 하 여 사각형을 그립니다.|
|[CDrawingManager::D rawShadow](#drawshadow)|사각형 영역의 그림자를 그립니다.|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|사각형 영역에 두 색 그라데이션을 채웁니다.|
|[CDrawingManager:: FillGradient](#fillgradient)|지정 된 색 그라데이션을 사용 하 여 사각형 영역을 채웁니다.|
|[CDrawingManager::FillGradient2](#fillgradient2)|지정 된 색 그라데이션을 사용 하 여 사각형 영역을 채웁니다. 그라데이션 색 변화 방향도 지정 됩니다.|
|[CDrawingManager::GrayRect](#grayrect)|사각형을 지정 된 회색 색으로 채웁니다.|
|[CDrawingManager::HighlightRect](#highlightrect)|사각형 영역을 강조 표시 합니다.|
|[CDrawingManager:: HLStoRGB_ONE](#hlstorgb_one)|HLS 표현의 색을 RGB 표현으로 변환 합니다.|
|[CDrawingManager:: HLStoRGB_TWO](#hlstorgb_two)|HLS 표현의 색을 RGB 표현으로 변환 합니다.|
|[CDrawingManager:: HSVtoRGB](#hsvtorgb)|HSV 표현의 색을 RGB 표현으로 변환 합니다.|
|[CDrawingManager::HuetoRGB](#huetorgb)|색조 값을 빨간색, 녹색 또는 파랑 구성 요소로 변환 하는 도우미 메서드입니다.|
|[CDrawingManager::MirrorRect](#mirrorrect)|사각형 영역을 대칭 이동 합니다.|
|[CDrawingManager::P ixelAlpha](#pixelalpha)|반투명 픽셀의 최종 색을 결정 하는 도우미 메서드입니다.|
|[CDrawingManager::P repareShadowMask](#prepareshadowmask)|그림자로 사용할 수 있는 비트맵을 만듭니다.|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|RGB 표현의 색을 HSL 표현으로 변환 합니다.|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|RGB 표현의 색을 HSV 표현으로 변환 합니다.|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|비트맵에서 부분적으로 투명 한 픽셀을 색으로 하는 도우미 메서드입니다.|
|[CDrawingManager::SetPixel](#setpixel)|비트맵의 단일 픽셀을 지정 된 색으로 변경 하는 도우미 메서드입니다.|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|가중치가 적용 된 비율을 기준으로 두 색을 결합 합니다.|

## <a name="remarks"></a>설명

`CDrawingManager`클래스는 그림자, 색 그라데이션 및 강조 표시 된 사각형을 그리기 위한 함수를 제공 합니다. 알파 혼합도 수행 합니다. 이 클래스를 사용 하 여 응용 프로그램의 UI를 직접 변경할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>요구 사항

**헤더:** afxdrawmanager

## <a name="cdrawingmanagercdrawingmanager"></a><a name="cdrawingmanager"></a> CDrawingManager::CDrawingManager

[CDrawingManager](../../mfc/reference/cdrawingmanager-class.md) 개체를 생성 합니다.

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>매개 변수

*dc*<br/>
진행 장치 컨텍스트에 대 한 참조입니다. 는 `CDrawingManager` 이 컨텍스트를 그리기에 사용 합니다.

## <a name="cdrawingmanagercreatebitmap_32"></a><a name="createbitmap_32"></a> CDrawingManager:: CreateBitmap_32

응용 프로그램에서 직접 쓸 수 있는 32 비트 DIB (장치 독립적 비트맵)를 만듭니다.

```
static HBITMAP __stdcall CreateBitmap_32(
    const CSize& size,
    void** pBits);

static HBITMAP __stdcall CreateBitmap_32(
    HBITMAP bitmap,
    COLORREF clrTransparent = -1);
```

### <a name="parameters"></a>매개 변수

*크기가*\
진행 비트맵의 크기를 나타내는 [Csize](../../atl-mfc-shared/reference/csize-class.md) 매개 변수입니다.

*pBits*\
제한이 DIB 비트 값의 위치를 받는 데이터 포인터에 대 한 포인터입니다.

*비트맵이*\
원래 비트맵에 대 한 핸들입니다.

*clrTransparent*\
원래 비트맵의 투명 한 색을 지정 하는 RGB 값입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 새로 만든 DIB 비트맵에 대 한 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

DIB 비트맵을 만드는 방법에 대 한 자세한 내용은 [CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibitmap)를 참조 하세요.

## <a name="cdrawingmanagerdrawalpha"></a><a name="drawalpha"></a> CDrawingManager::D rawAlpha

투명 또는 반투명 픽셀의 비트맵이 표시 됩니다.

```cpp
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>매개 변수

*pDstDC*<br/>
진행 대상에 대 한 장치 컨텍스트에 대 한 포인터입니다.

*rectDst*<br/>
진행 대상 사각형입니다.

*pSrcDC*<br/>
진행 소스에 대 한 장치 컨텍스트에 대 한 포인터입니다.

*rectSrc*<br/>
진행 소스 사각형입니다.

### <a name="remarks"></a>설명

이 메서드는 두 비트맵에 대해 알파 혼합을 수행 합니다. 알파 혼합에 대 한 자세한 내용은 Windows SDK의 [AlphaBlend](/windows/win32/api/wingdi/nf-wingdi-alphablend) 를 참조 하세요.

## <a name="cdrawingmanagerdrawellipse"></a><a name="drawellipse"></a> CDrawingManager::D rawEllipse

제공 된 채우기 및 테두리 색을 사용 하 여 타원을 그립니다.

```cpp
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
진행 타원의 경계 사각형입니다.

*clrFill*<br/>
진행 이 메서드가 타원을 채우는 데 사용 하는 색입니다.

*clrLine*<br/>
진행 이 메서드가 타원의 테두리로 사용 하는 색입니다.

### <a name="remarks"></a>설명

색이-1로 설정 된 경우이 메서드는 타원을 그리지 않고를 반환 합니다. 경계 사각형의 두 차원이 모두 0 인 경우에도 타원을 그리지 않고를 반환 합니다.

## <a name="cdrawingmanagerdrawgradientring"></a><a name="drawgradientring"></a> CDrawingManager::D rawGradientRing

링을 그리고 색 그라데이션으로 채웁니다.

```
BOOL DrawGradientRing(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    COLORREF colorBorder,
    int nAngle,
    int nWidth,
    COLORREF clrFace = (COLORREF)-1);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
진행 그라데이션 링의 경계를 지정 하는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 매개 변수입니다.

*colorStart*<br/>
진행 그라데이션의 첫 번째 색입니다.

*색 끝*<br/>
진행 그라데이션의 마지막 색입니다.

*colorBorder*<br/>
진행 테두리의 색입니다.

*n 각도*<br/>
진행 초기 그라데이션 그리기 각도를 지정 하는 매개 변수입니다. 이 값은 0에서 360 사이 여야 합니다.

*nWidth*<br/>
진행 링 테두리의 너비입니다.

*clrFace*<br/>
진행 링의 내부 색입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*Rect* 에서 정의 되는 사각형의 너비는 5 픽셀 이상, 높이는 5 픽셀 이상 이어야 합니다.

## <a name="cdrawingmanagerdrawline-cdrawingmanagerdrawlinea"></a><a name="drawline_cdrawingmanager__drawlinea"></a> CDrawingManager::D rawLine, CDrawingManager::D rawLineA

선을 그립니다.

```cpp
void DrawLine(
    int x1,
    int y1,
    int x2,
    int y2,
    COLORREF clrLine);

void DrawLineA(
    double x1,
    double y1,
    double x2,
    double y2,
    COLORREF clrLine);
```

### <a name="parameters"></a>매개 변수

*x*\
진행 줄이 시작 되는 x 좌표입니다.

*y1*\
진행 줄이 시작 되는 y 좌표입니다.

*x2*\
진행 선이 끝나는 x 좌표입니다.

*y2*\
진행 선이 끝나는 y 좌표입니다.

*clrLine*\
진행 선의 색입니다.

### <a name="remarks"></a>설명

*Clrline* 이-1과 같으면이 메서드는 실패 합니다.

## <a name="cdrawingmanagerdrawrect"></a><a name="drawrect"></a> CDrawingManager::D rawRect

제공 된 채우기 및 테두리 색을 사용 하 여 사각형을 그립니다.

```cpp
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
진행 사각형의 경계입니다.

*clrFill*<br/>
진행 이 메서드가 사각형을 채우는 데 사용 하는 색입니다.

*clrLine*<br/>
진행 사각형 테두리에 대해이 메서드가 사용 하는 색입니다.

### <a name="remarks"></a>설명

이 메서드는 색이-1로 설정 된 경우 사각형을 그리지 않고 반환 합니다. 사각형의 두 차원이 모두 0 인 경우에도를 반환 합니다.

## <a name="cdrawingmanagerdrawshadow"></a><a name="drawshadow"></a> CDrawingManager::D rawShadow

사각형 영역의 그림자를 그립니다.

```
BOOL DrawShadow(
    CRect rect,
    int nDepth,
    int iMinBrightness = 100,
    int iMaxBrightness = 50,
    CBitmap* pBmpSaveBottom = NULL,
    CBitmap* pBmpSaveRight = NULL,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bRightShadow = TRUE);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
진행 응용 프로그램의 사각형 영역입니다. 드로잉 관리자가이 영역 아래에 그림자를 그립니다.

*nDepth*<br/>
진행 그림자의 너비와 높이입니다.

*iMinBrightness*<br/>
진행 그림자의 최소 밝기입니다.

*iMaxBrightness*<br/>
진행 그림자의 최대 밝기입니다.

*pBmpSaveBottom*<br/>
진행 그림자 아래쪽 부분의 이미지를 포함 하는 비트맵에 대 한 포인터입니다.

*pBmpSaveRight*<br/>
진행 사각형의 오른쪽에 그려지는 그림자의 이미지를 포함 하는 비트맵에 대 한 포인터입니다.

*clrBase*<br/>
진행 그림자의 색입니다.

*bRightShadow*<br/>
진행 그림자를 그리는 방법을 나타내는 부울 매개 변수입니다. *BRightShadow* 가 인 경우는 `TRUE` `DrawShadow` 사각형의 오른쪽에 그림자를 그립니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*Pbmpsavebottom* 및 *pBmpSaveRight* 매개 변수를 사용 하 여 아래쪽과 오른쪽 그림자에 대 한 유효한 두 개의 비트맵을 제공할 수 있습니다. 이러한 [Cbitmap](../../mfc/reference/cbitmap-class.md) 개체에 연결 된 GDI 개체가 있으면에서 `DrawShadow` 해당 비트맵을 그림자로 사용 합니다. `CBitmap`매개 변수에 연결 된 GDI 개체가 없는 경우는 그림자를 `DrawShadow` 그리고 비트맵을 매개 변수에 연결 합니다. 이후 호출에서 `DrawShadow` 이러한 비트맵을 제공 하 여 그리기 프로세스의 속도를 높일 수 있습니다. 클래스 및 GDI 개체에 대 한 자세한 내용은 `CBitmap` [그래픽 개체](../../mfc/graphic-objects.md)를 참조 하세요.

이러한 매개 변수 중 하나가 이면 `NULL` 에서 `DrawShadow` 자동으로 그림자를 그립니다.

*BRightShadow* 를 FALSE로 설정 하면 그림자가 사각형 영역의 왼쪽 아래에 그려집니다.

### <a name="example"></a>예제

다음 예제에서는 클래스의 메서드를 사용 하는 방법을 보여 줍니다 `DrawShadow` `CDrawingManager` . 이 코드 조각은 [Prop 시트 데모 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

## <a name="cdrawingmanagerfill4colorsgradient"></a><a name="fill4colorsgradient"></a> CDrawingManager::Fill4ColorsGradient

사각형 영역에 두 색 그라데이션을 채웁니다.

```cpp
void Fill4ColorsGradient(
    CRect rect,
    COLORREF colorStart1,
    COLORREF colorFinish1,
    COLORREF colorStart2,
    COLORREF colorFinish2,
    BOOL bHorz = TRUE,
    int nPercentage = 50);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
진행 채울 사각형입니다.

*colorStart1*<br/>
진행 첫 번째 색 그라데이션의 초기 색입니다.

*colorFinish1*<br/>
진행 첫 번째 색 그라데이션의 마지막 색입니다.

*colorStart2*<br/>
진행 두 번째 색 그라데이션의 초기 색입니다.

*colorFinish2*<br/>
진행 두 번째 색 그라데이션의 마지막 색입니다.

*bHorz*<br/>
진행 `Fill4ColorsGradient` 가 가로 또는 세로 그라데이션을 색으로 지정 하는지 여부를 나타내는 부울 매개 변수입니다. TRUE는 가로 그라데이션을 나타냅니다.

*n 백분율*<br/>
진행 0-100의 정수입니다. 이 값은 첫 번째 색 그라데이션으로 채울 사각형의 비율을 나타냅니다.

### <a name="remarks"></a>설명

사각형을 두 개의 색 그라데이션으로 채우면 *Bhorz* 의 값에 따라 서로 다른 색 그라데이션으로, 서로 인접 하 게 배치 됩니다. 각 색 그라데이션은 [CDrawingManager:: FillGradient](#fillgradient)메서드와 독립적으로 계산 됩니다.

*Npercentage* 0 보다 작거나 100 보다 많은 경우이 메서드는 어설션 오류를 생성 합니다.

## <a name="cdrawingmanagerfillgradient"></a><a name="fillgradient"></a> CDrawingManager:: FillGradient

지정 된 색 그라데이션을 사용 하 여 사각형 영역을 채웁니다.

```cpp
void FillGradient(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    BOOL bHorz = TRUE,
    int nStartFlatPercentage = 0,
    int nEndFlatPercentage = 0);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
진행 채울 사각형 영역입니다.

*colorStart*<br/>
진행 그라데이션의 첫 번째 색입니다.

*색 끝*<br/>
진행 그라데이션의 마지막 색입니다.

*bHorz*<br/>
진행 가 `FillGradient` 가로 또는 세로 그라데이션을 그려야 할지 여부를 지정 하는 부울 매개 변수입니다.

*nStartFlatPercentage*<br/>
진행 `FillGradient` 색이 그라데이션을 시작 하기 전에 *colorstart* 로 채워지는 사각형의 백분율입니다.

*nEndFlatPercentage*<br/>
진행 `FillGradient` 그라데이션을 완료 한 후 *colorfinish* 로 채우는 사각형의 백분율입니다.

### <a name="example"></a>예제

다음 예제에서는 클래스의 메서드를 사용 하는 방법을 보여 줍니다 `FillGradient` `CDrawingManager` . 이 코드 조각은 [MS Office 2007 Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

## <a name="cdrawingmanagerfillgradient2"></a><a name="fillgradient2"></a> CDrawingManager::FillGradient2

지정 된 색 그라데이션을 사용 하 여 사각형 영역을 채웁니다.

```cpp
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
진행 채울 사각형 영역입니다.

*colorStart*<br/>
진행 그라데이션의 첫 번째 색입니다.

*색 끝*<br/>
진행 그라데이션의 마지막 색입니다.

*n 각도*<br/>
진행 0에서 360 사이의 정수입니다. 이 매개 변수는 색 그라데이션의 방향을 지정 합니다.

### <a name="remarks"></a>설명

*N 각도* 를 사용 하 여 색 그라데이션의 방향을 지정 합니다. 색 그라데이션의 방향을 지정 하는 경우 색 그라데이션을 시작할 위치도 지정 합니다. *Nangle* 의 값 0은 그라데이션이 사각형 위쪽에서 시작 됨을 나타냅니다. *Nangle* 이 늘어나면 그라데이션의 시작 위치는 각도를 기준으로 시계 반대 방향으로 이동 합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스의 메서드를 사용 하는 방법을 보여 줍니다 `FillGradient2` `CDrawingManager` . 이 코드 조각은 [새 Controls 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

## <a name="cdrawingmanagergrayrect"></a><a name="grayrect"></a> CDrawingManager::GrayRect

사각형을 지정 된 회색 색으로 채웁니다.

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
진행 채울 사각형 영역입니다.

*n 백분율*<br/>
진행 사각형에서 원하는 회색의 백분율입니다.

*clrTransparent*<br/>
진행 투명 한 색입니다.

*clrDisabled*<br/>
진행 *Npercentage* -1로 설정 된 경우이 메서드가 채도 취소에 사용 하는 색입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

매개 변수 *Npercentage* 의 경우 낮은 값은 더 짙은 색을 나타냅니다.

*Npercentage* 의 최대값은 200입니다. 200 보다 큰 값은 사각형의 모양을 변경 하지 않습니다. 값이-1 인 경우이 메서드는 *Clrdisabled* 를 사용 하 여 사각형의 채도를 제한 합니다.

## <a name="cdrawingmanagerhighlightrect"></a><a name="highlightrect"></a> CDrawingManager::HighlightRect

사각형 영역을 강조 표시 합니다.

```
BOOL HighlightRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    int nTolerance = 0,
    COLORREF clrBlend = (COLORREF)-1);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
진행 강조 표시 하는 사각형 영역입니다.

*n 백분율*<br/>
진행 강조 표시의 투명도를 나타내는 백분율입니다.

*clrTransparent*<br/>
진행 투명 한 색입니다.

*nTolerance*<br/>
진행 색 허용 오차를 나타내는 0에서 255 사이의 정수입니다.

*clrBlend*<br/>
진행 혼합을 위한 기본 색입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

*Npercentage* 0에서 99 사이인 경우는 `HighlightRect` 알파 혼합 알고리즘을 사용 합니다. 알파 혼합에 대 한 자세한 내용은 [선 및 채우기 알파 혼합](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills)을 참조 하세요. *Npercentage* -1 인 경우이 메서드는 기본 강조 표시 수준을 사용 합니다. *Npercentage* 100 인 경우이 메서드는 아무 작업도 수행 하지 않고 TRUE를 반환 합니다.

메서드는 *Ntolerance* 매개 변수를 사용 하 여 사각형 영역을 강조할 지 여부를 결정 합니다. 사각형을 강조 표시 하려면 각 색 구성 요소 (빨강, 녹색 및 파랑)에서 응용 프로그램의 배경색과 *Clrtransparent* 의 차이가 *ntolerance* 미만 이어야 합니다.

## <a name="cdrawingmanagerhlstorgb_one"></a><a name="hlstorgb_one"></a> CDrawingManager:: HLStoRGB_ONE

HLS 표현의 색을 RGB 표현으로 변환 합니다.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>매개 변수

*H*<br/>
진행 색의 색상을 나타내는 0과 1 사이의 숫자입니다.

*L*<br/>
진행 색의 명도를 나타내는 0에서 1 사이의 숫자입니다.

*S*<br/>
진행 색의 채도를 나타내는 0에서 1 사이의 숫자입니다.

### <a name="return-value"></a>반환 값

제공 된 HLS 색의 RGB 표현입니다.

### <a name="remarks"></a>설명

색은 HSV (색상, 채도 및 값), HSL (색상, 채도 및 명도) 또는 RGB (빨강, 녹색, 파랑)로 표현 될 수 있습니다. 다른 색 표현에 대 한 자세한 내용은 [color](/windows/win32/uxguide/vis-color)를 참조 하세요.

이 메서드와 메서드는 `CDrawingManager::HLStoRGB_TWO` 동일한 작업을 수행 하지만 *H* 매개 변수에는 다른 값이 필요 합니다. 이 메서드에서 *H* 는 원의 백분율입니다. `CDrawingManager::HLStoRGB_TWO`메서드에서 *H* 는 빨강을 나타내는 0에서 360 사이의 각도 값입니다. 예를 들어를 사용 하는 경우 `HLStoRGB_ONE` *H* 의 값 0.25은 with 90 값과 동일 `HLStoRGB_TWO` 합니다.

## <a name="cdrawingmanagerhlstorgb_two"></a><a name="hlstorgb_two"></a> CDrawingManager:: HLStoRGB_TWO

HLS 표현의 색을 RGB 표현으로 변환 합니다.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>매개 변수

*H*<br/>
진행 색의 색상을 나타내는 0에서 360 사이의 숫자입니다.

*L*<br/>
진행 색의 명도를 나타내는 0에서 1 사이의 숫자입니다.

*S*<br/>
진행 색의 채도를 나타내는 0에서 1 사이의 숫자입니다.

### <a name="return-value"></a>반환 값

제공 된 HLS 색의 RGB 표현입니다.

### <a name="remarks"></a>설명

색은 HSV (색상, 채도 및 값), HSL (색상, 채도 및 명도) 또는 RGB (빨강, 녹색, 파랑)로 표현 될 수 있습니다. 다른 색 표현에 대 한 자세한 내용은 [color](/windows/win32/uxguide/vis-color)를 참조 하세요.

이 메서드와 [CDrawingManager:: HLStoRGB_ONE](#hlstorgb_one) 메서드는 동일한 작업을 수행 하지만 *H* 매개 변수에는 다른 값이 필요 합니다. 이 메서드에서 *H* 는 빨강을 나타내는 0에서 360 사이의 수준 값입니다. [CDrawingManager:: HLStoRGB_ONE](#hlstorgb_one) 메서드에서 *H* 는 원의 백분율입니다. 예를 들어를 사용 하는 경우 `HLStoRGB_ONE` *H* 의 값 0.25은 with 90 값과 동일 `HLStoRGB_TWO` 합니다.

## <a name="cdrawingmanagerhsvtorgb"></a><a name="hsvtorgb"></a> CDrawingManager:: HSVtoRGB

HSV 표현의 색을 RGB 표현으로 변환 합니다.

```
static COLORREF __stdcall HSVtoRGB(
    double H,
    double S,
    double V);
```

### <a name="parameters"></a>매개 변수

*넣기*\
진행 색의 색상을 나타내는 0에서 360 사이의 숫자입니다.

*삭제*\
진행 색의 채도를 나타내는 0에서 1 사이의 숫자입니다.

*Hyper-v*\
진행 색에 대 한 값을 나타내는 0과 1 사이의 숫자입니다.

### <a name="return-value"></a>반환 값

제공 된 HSV 색의 RGB 표현입니다.

### <a name="remarks"></a>설명

색은 HSV (색상, 채도 및 값), HSL (색상, 채도 및 명도) 또는 RGB (빨강, 녹색, 파랑)로 표현 될 수 있습니다. 다른 색 표현에 대 한 자세한 내용은 [color](/windows/win32/uxguide/vis-color)를 참조 하세요.

## <a name="cdrawingmanagerhuetorgb"></a><a name="huetorgb"></a> CDrawingManager::HuetoRGB

색조 값을 빨간색, 녹색 또는 파랑 구성 요소로 변환 합니다.

```
static double __stdcall HuetoRGB(
    double m1,
    double m2,
    double h);

static BYTE __stdcall HueToRGB(
    float rm1,
    float rm2,
    float rh);
```

### <a name="parameters"></a>매개 변수

*m 1*<br/>
진행 설명을 참조 하세요.

*m2*<br/>
진행 설명을 참조 하세요.

*h*<br/>
진행 설명을 참조 하세요.

*rm1*<br/>
진행 설명을 참조 하세요.

*rm2*<br/>
진행 설명을 참조 하세요.

*rh*<br/>
진행 설명을 참조 하세요.

### <a name="return-value"></a>반환 값

제공 된 색상에 대 한 개별 빨간색, 녹색 또는 파랑 구성 요소입니다.

### <a name="remarks"></a>설명

이 메서드는 `CDrawingManager` HSV 또는 HSL 표현에서 색의 빨간색, 녹색 및 파랑의 개별 구성 요소를 계산 하기 위해 클래스에서 사용 하는 도우미 메서드입니다. 이 메서드는 프로그래머가 직접 호출 하도록 설계 되지 않았습니다. 입력 매개 변수는 변환 알고리즘에 따라 달라 지는 값입니다.

HSV 또는 HSL 색을 RGB 표현으로 변환 하려면 다음 메서드 중 하나를 호출 합니다.

- [CDrawingManager:: HSVtoRGB](#hsvtorgb)

- [CDrawingManager:: HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager:: HLStoRGB_TWO](#hlstorgb_two)

## <a name="cdrawingmanagermirrorrect"></a><a name="mirrorrect"></a> CDrawingManager::MirrorRect

사각형 영역을 대칭 이동 합니다.

```cpp
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
진행 대칭 이동할 영역의 경계 사각형입니다.

*bHorz*<br/>
진행 사각형이 가로 또는 세로로 대칭 이동 하는지 여부를 나타내는 부울 매개 변수입니다.

### <a name="remarks"></a>설명

이 메서드는 클래스에서 소유 하는 장치 컨텍스트의 모든 영역을 대칭 이동할 수 있습니다 `CDrawingManager` . *Bhorz* 이 TRUE로 설정 된 경우이 메서드는 영역을 가로로 대칭 이동 합니다. 그렇지 않으면 영역을 세로로 대칭 이동 합니다.

## <a name="cdrawingmanagerpixelalpha"></a><a name="pixelalpha"></a> CDrawingManager::P ixelAlpha

반투명 픽셀의 최종 색을 계산 합니다.

```
static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    int percent);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    double percentR,
    double percentG,
    double percentB);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    COLORREF dstPixel,
    int percent);
```

### <a name="parameters"></a>매개 변수

*srcPixel*<br/>
진행 픽셀의 초기 색입니다.

*수익률*<br/>
진행 투명도의 백분율을 나타내는 0에서 100 사이의 숫자입니다. 값 100은 초기 색이 완전히 투명 함을 나타냅니다.

*percentR*<br/>
진행 빨강 구성 요소에 대 한 투명도의 백분율을 나타내는 0에서 100 사이의 숫자입니다.

*percentG*<br/>
진행 녹색 구성 요소에 대 한 투명도 비율을 나타내는 0에서 100 사이의 숫자입니다.

*percentB*<br/>
진행 파랑 구성 요소에 대 한 투명도의 백분율을 나타내는 0에서 100 사이의 숫자입니다.

*dstPixel*<br/>
진행 픽셀의 기본 색입니다.

### <a name="return-value"></a>반환 값

반투명 픽셀의 마지막 색입니다.

### <a name="remarks"></a>설명

이 클래스는 반투명 비트맵을 강조 하기 위한 도우미 클래스 이며 프로그래머가 직접 호출 하도록 설계 되지 않았습니다.

*Dstpixel* 를 사용 하는 메서드 버전을 사용 하는 경우 최종 색은 *Dstpixel* 및 *srcpixel* 의 조합입니다. *Srcpixel* 색은 기본 색 *dstpixel* 에 대 한 부분적으로 투명 한 색입니다.

## <a name="cdrawingmanagerprepareshadowmask"></a><a name="prepareshadowmask"></a> CDrawingManager::P repareShadowMask

그림자로 사용할 수 있는 비트맵을 만듭니다.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>매개 변수

*nDepth*<br/>
진행 그림자의 너비와 높이입니다.

*clrBase*<br/>
진행 그림자의 색입니다.

*iMinBrightness*<br/>
진행 그림자의 최소 밝기입니다.

*iMaxBrightness*<br/>
진행 그림자의 최대 밝기입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하는 경우 생성 된 비트맵에 대 한 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

*Ndepth* 가 0으로 설정 되 면이 메서드는 종료 되 고 NULL을 반환 합니다. *Ndepth* 가 3 보다 작은 경우 그림자의 너비와 높이는 3 픽셀로 설정 됩니다.

## <a name="cdrawingmanagerrgbtohsl"></a><a name="rgbtohsl"></a> CDrawingManager::RGBtoHSL

빨강, 녹색 및 파랑 (RGB) 표현의 색을 색상, 채도 및 밝기 (HSL) 표현으로 변환 합니다.

```
static void __stdcall RGBtoHSL(
    COLORREF rgb,
    double* H,
    double* S,
    double* L);
```

### <a name="parameters"></a>매개 변수

*rgb*\
진행 RGB 값의 색입니다.

*넣기*\
제한이 메서드가 색의 색상을 저장 하는 double에 대 한 포인터입니다.

*삭제*\
제한이 메서드가 색의 채도를 저장 하는 double에 대 한 포인터입니다.

*L-value*\
제한이 메서드가 색의 밝기를 저장 하는 double에 대 한 포인터입니다.

### <a name="remarks"></a>설명

색은 HSV (색상, 채도 및 값), HSL (색상, 채도 및 명도) 또는 RGB (빨강, 녹색, 파랑)로 표현 될 수 있습니다. 다른 색 표현에 대 한 자세한 내용은 [color](/windows/win32/uxguide/vis-color)를 참조 하세요.

*H* 에 대해 반환 되는 값은 0과 1 사이의 분수로 표시 됩니다. 여기서 0과 1은 빨강을 나타냅니다. *S* 와 *L* 에 대해 반환 된 값은 0에서 1 사이의 숫자입니다.

## <a name="cdrawingmanagerrgbtohsv"></a><a name="rgbtohsv"></a> CDrawingManager::RGBtoHSV

RGB 표현의 색을 HSV 표현으로 변환 합니다.

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>매개 변수

*rgb*<br/>
진행 RGB 표현에서 변환할 색입니다.

*H*<br/>
제한이 이 메서드가 색의 결과 색상을 저장 하는 double에 대 한 포인터입니다.

*S*<br/>
제한이 이 메서드가 색의 결과 채도를 저장 하는 double에 대 한 포인터입니다.

*V*<br/>
제한이 이 메서드가 색의 결과 값을 저장 하는 double에 대 한 포인터입니다.

### <a name="remarks"></a>설명

색은 HSV (색상, 채도 및 값), HSL (색상, 채도 및 명도) 또는 RGB (빨강, 녹색, 파랑)로 표현 될 수 있습니다. 다른 색 표현에 대 한 자세한 내용은 [color](/windows/win32/uxguide/vis-color)를 참조 하세요.

*H* 에 대해 반환 되는 값은 0과 360 사이의 숫자입니다. 여기서 0과 360은 모두 빨간색을 의미 합니다. *S* 및 *V* 의 반환 값은 0에서 1 사이의 숫자입니다.

## <a name="cdrawingmanagersetalphapixel"></a><a name="setalphapixel"></a> CDrawingManager::SetAlphaPixel

비트맵의 투명 픽셀을 색으로 만듭니다.

```
static void __stdcall SetAlphaPixel(
    COLORREF* pBits,
    CRect rect,
    int x,
    int y,
    int percent,
    int iShadowSize,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bIsRight = TRUE);
```

### <a name="parameters"></a>매개 변수

*pBits*<br/>
진행 비트맵의 비트 값에 대 한 포인터입니다.

*rect*<br/>
진행 응용 프로그램의 사각형 영역입니다. 드로잉 관리자는이 영역의 오른쪽에 그림자를 그립니다.

*x*<br/>
진행 색에 대 한 픽셀의 가로 좌표입니다.

*y*<br/>
진행 색에 대 한 픽셀의 세로 좌표입니다.

*수익률*<br/>
진행 투명도의 백분율입니다.

*iShadowSize*<br/>
진행 그림자의 너비와 높이입니다.

*clrBase*<br/>
진행 그림자의 색입니다.

*bIsRight*<br/>
진행 색을 지정 하는 픽셀을 나타내는 부울 매개 변수입니다. 자세한 내용은 설명 부분을 참조하세요.

### <a name="remarks"></a>설명

이 메서드는 [CDrawingManager::D rawshadow](#drawshadow) 메서드에서 사용 하는 도우미 메서드입니다. 그림자를 그리려면 대신를 호출 하는 것이 좋습니다 `CDrawingManager::DrawShadow` .

*BIsRight* 가 TRUE로 설정 된 경우 픽셀을 색으로 설정 하면 *사각형* 의 오른쪽 가장자리에서 *x* 픽셀으로 측정 됩니다. FALSE 이면 *사각형* 의 왼쪽 가장자리에서 색 *의 픽셀을 측정 합니다* .

## <a name="cdrawingmanagersetpixel"></a><a name="setpixel"></a> CDrawingManager::SetPixel

비트맵의 단일 픽셀을 지정 된 색으로 변경 합니다.

```
static void __stdcall SetPixel(
    COLORREF* pBits,
    int cx,
    int cy,
    int x,
    int y,
    COLORREF color);
```

### <a name="parameters"></a>매개 변수

*pBits*\
진행 비트맵의 비트 값에 대 한 포인터입니다.

*cx*\
진행 비트맵의 총 너비입니다.

*cy*\
진행 비트맵의 총 높이입니다.

*.x*\
진행 비트맵에서 변경할 픽셀의 x 좌표입니다.

*x.y*\
진행 변경할 비트맵의 픽셀에 대 한 y-좌표입니다.

*색*\
진행 제공 된 좌표로 식별 되는 픽셀의 새 색입니다.

## <a name="cdrawingmanagersmartmixcolors"></a><a name="smartmixcolors"></a> CDrawingManager::SmartMixColors

가중치가 적용 된 비율을 기준으로 두 색을 결합 합니다.

```
static COLORREF __stdcall SmartMixColors(
    COLORREF color1,
    COLORREF color2,
    double dblLumRatio = 1.,
    int k1 = 1,
    int k2 = 1);
```

### <a name="parameters"></a>매개 변수

*color1*\
진행 혼합할 첫째 색입니다.

*color2*\
진행 혼합할 두 번째 색입니다.

*dblLumRatio*\
진행 새 색의 명도에 대 한 비율입니다. `SmartMixColors` 최종 색을 결정 하기 전에 혼합 색의 광도를이 비율로 곱합니다.

*k1*\
진행 첫 번째 색의 가중치가 적용 된 비율입니다.

*k2*\
진행 두 번째 색의 가중치가 적용 된 비율입니다.

### <a name="return-value"></a>반환 값

제공 된 색의 가중치가 혼합 된 색을 나타내는 색입니다.

### <a name="remarks"></a>설명

*K1* 또는 *k2* 가 0 보다 작은 경우이 메서드는 오류와 함께 실패 합니다. 두 매개 변수가 모두 0으로 설정 된 경우이 메서드는를 반환 `RGB(0, 0, 0)` 합니다.

가중치가 적용 된 비율은 (color1 \* k1 + color2 \* k2)/(k1 + k2) 수식을 사용 하 여 계산 됩니다. 가중치가 적용 된 비율을 확인 한 후에는이 메서드는 혼합 색의 광도를 계산 합니다. 그런 다음 광도를 *dblLumRatio* 곱합니다. 값이 1.0 보다 큰 경우이 메서드는 혼합 색의 광도를 새 값으로 설정 합니다. 그렇지 않으면 명도는 1.0로 설정 됩니다.

## <a name="cdrawingmanagerdrawrotated"></a><a name="drawrotated"></a> CDrawingManager::D rawRotated

원본 DC 콘텐츠를 지정 된 사각형 내에서 90 도씩 회전 합니다.

```cpp
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>매개 변수

*rectDest*<br/>
대상 사각형입니다.

*dcSrc*<br/>
원본 장치 컨텍스트입니다.

*bClockWise*<br/>
TRUE는 회전 + 90도를 나타냅니다. FALSE는 회전-90도를 나타냅니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)
