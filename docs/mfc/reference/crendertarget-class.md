---
description: CRenderTarget 클래스에 대해 자세히 알아보세요.
title: CRenderTarget 클래스
ms.date: 03/27/2019
f1_keywords:
- CRenderTarget
- AFXRENDERTARGET/CRenderTarget
- AFXRENDERTARGET/CRenderTarget::CRenderTarget
- AFXRENDERTARGET/CRenderTarget::Attach
- AFXRENDERTARGET/CRenderTarget::BeginDraw
- AFXRENDERTARGET/CRenderTarget::Clear
- AFXRENDERTARGET/CRenderTarget::COLORREF_TO_D2DCOLOR
- AFXRENDERTARGET/CRenderTarget::CreateCompatibleRenderTarget
- AFXRENDERTARGET/CRenderTarget::Destroy
- AFXRENDERTARGET/CRenderTarget::Detach
- AFXRENDERTARGET/CRenderTarget::DrawBitmap
- AFXRENDERTARGET/CRenderTarget::DrawEllipse
- AFXRENDERTARGET/CRenderTarget::DrawGeometry
- AFXRENDERTARGET/CRenderTarget::DrawGlyphRun
- AFXRENDERTARGET/CRenderTarget::DrawLine
- AFXRENDERTARGET/CRenderTarget::DrawRectangle
- AFXRENDERTARGET/CRenderTarget::DrawRoundedRectangle
- AFXRENDERTARGET/CRenderTarget::DrawText
- AFXRENDERTARGET/CRenderTarget::DrawTextLayout
- AFXRENDERTARGET/CRenderTarget::EndDraw
- AFXRENDERTARGET/CRenderTarget::FillEllipse
- AFXRENDERTARGET/CRenderTarget::FillGeometry
- AFXRENDERTARGET/CRenderTarget::FillMesh
- AFXRENDERTARGET/CRenderTarget::FillOpacityMask
- AFXRENDERTARGET/CRenderTarget::FillRectangle
- AFXRENDERTARGET/CRenderTarget::FillRoundedRectangle
- AFXRENDERTARGET/CRenderTarget::Flush
- AFXRENDERTARGET/CRenderTarget::GetAntialiasMode
- AFXRENDERTARGET/CRenderTarget::GetDpi
- AFXRENDERTARGET/CRenderTarget::GetMaximumBitmapSize
- AFXRENDERTARGET/CRenderTarget::GetPixelFormat
- AFXRENDERTARGET/CRenderTarget::GetPixelSize
- AFXRENDERTARGET/CRenderTarget::GetRenderTarget
- AFXRENDERTARGET/CRenderTarget::GetSize
- AFXRENDERTARGET/CRenderTarget::GetTags
- AFXRENDERTARGET/CRenderTarget::GetTextAntialiasMode
- AFXRENDERTARGET/CRenderTarget::GetTextRenderingParams
- AFXRENDERTARGET/CRenderTarget::GetTransform
- AFXRENDERTARGET/CRenderTarget::IsSupported
- AFXRENDERTARGET/CRenderTarget::IsValid
- AFXRENDERTARGET/CRenderTarget::PopAxisAlignedClip
- AFXRENDERTARGET/CRenderTarget::PopLayer
- AFXRENDERTARGET/CRenderTarget::PushAxisAlignedClip
- AFXRENDERTARGET/CRenderTarget::PushLayer
- AFXRENDERTARGET/CRenderTarget::RestoreDrawingState
- AFXRENDERTARGET/CRenderTarget::SaveDrawingState
- AFXRENDERTARGET/CRenderTarget::SetAntialiasMode
- AFXRENDERTARGET/CRenderTarget::SetDpi
- AFXRENDERTARGET/CRenderTarget::SetTags
- AFXRENDERTARGET/CRenderTarget::SetTextAntialiasMode
- AFXRENDERTARGET/CRenderTarget::SetTextRenderingParams
- AFXRENDERTARGET/CRenderTarget::SetTransform
- AFXRENDERTARGET/CRenderTarget::VerifyResource
- AFXRENDERTARGET/CRenderTarget::m_lstResources
- AFXRENDERTARGET/CRenderTarget::m_pRenderTarget
- AFXRENDERTARGET/CRenderTarget::m_pTextFormatDefault
helpviewer_keywords:
- CRenderTarget [MFC], CRenderTarget
- CRenderTarget [MFC], Attach
- CRenderTarget [MFC], BeginDraw
- CRenderTarget [MFC], Clear
- CRenderTarget [MFC], COLORREF_TO_D2DCOLOR
- CRenderTarget [MFC], CreateCompatibleRenderTarget
- CRenderTarget [MFC], Destroy
- CRenderTarget [MFC], Detach
- CRenderTarget [MFC], DrawBitmap
- CRenderTarget [MFC], DrawEllipse
- CRenderTarget [MFC], DrawGeometry
- CRenderTarget [MFC], DrawGlyphRun
- CRenderTarget [MFC], DrawLine
- CRenderTarget [MFC], DrawRectangle
- CRenderTarget [MFC], DrawRoundedRectangle
- CRenderTarget [MFC], DrawText
- CRenderTarget [MFC], DrawTextLayout
- CRenderTarget [MFC], EndDraw
- CRenderTarget [MFC], FillEllipse
- CRenderTarget [MFC], FillGeometry
- CRenderTarget [MFC], FillMesh
- CRenderTarget [MFC], FillOpacityMask
- CRenderTarget [MFC], FillRectangle
- CRenderTarget [MFC], FillRoundedRectangle
- CRenderTarget [MFC], Flush
- CRenderTarget [MFC], GetAntialiasMode
- CRenderTarget [MFC], GetDpi
- CRenderTarget [MFC], GetMaximumBitmapSize
- CRenderTarget [MFC], GetPixelFormat
- CRenderTarget [MFC], GetPixelSize
- CRenderTarget [MFC], GetRenderTarget
- CRenderTarget [MFC], GetSize
- CRenderTarget [MFC], GetTags
- CRenderTarget [MFC], GetTextAntialiasMode
- CRenderTarget [MFC], GetTextRenderingParams
- CRenderTarget [MFC], GetTransform
- CRenderTarget [MFC], IsSupported
- CRenderTarget [MFC], IsValid
- CRenderTarget [MFC], PopAxisAlignedClip
- CRenderTarget [MFC], PopLayer
- CRenderTarget [MFC], PushAxisAlignedClip
- CRenderTarget [MFC], PushLayer
- CRenderTarget [MFC], RestoreDrawingState
- CRenderTarget [MFC], SaveDrawingState
- CRenderTarget [MFC], SetAntialiasMode
- CRenderTarget [MFC], SetDpi
- CRenderTarget [MFC], SetTags
- CRenderTarget [MFC], SetTextAntialiasMode
- CRenderTarget [MFC], SetTextRenderingParams
- CRenderTarget [MFC], SetTransform
- CRenderTarget [MFC], VerifyResource
- CRenderTarget [MFC], m_lstResources
- CRenderTarget [MFC], m_pRenderTarget
- CRenderTarget [MFC], m_pTextFormatDefault
ms.assetid: 30d1607d-68d3-4d14-ac36-fdbd0ef903a1
ms.openlocfilehash: 040b4a55f749eace2b4cc98b30fc12b02e0808c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264923"
---
# <a name="crendertarget-class"></a>CRenderTarget 클래스

ID2D1RenderTarget에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CRenderTarget : public CObject;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CRenderTarget:: CRenderTarget](#crendertarget)|CRenderTarget 개체를 생성 합니다.|
|[CRenderTarget:: ~ CRenderTarget](#_dtorcrendertarget)|소멸자입니다. 렌더링 대상 개체가 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CRenderTarget:: Attach](#attach)|기존 렌더링 대상 인터페이스를 개체에 연결 합니다.|
|[CRenderTarget:: BeginDraw](#begindraw)|이 렌더링 대상에서 그리기를 시작 합니다.|
|[CRenderTarget:: Clear](#clear)|그리기 영역을 지정 된 색으로 지웁니다.|
|[CRenderTarget:: COLORREF_TO_D2DCOLOR](#colorref_to_d2dcolor)|GDI 색 및 알파 값을 D2D1_COLOR_F 개체로 변환 합니다.|
|[CRenderTarget:: CreateCompatibleRenderTarget](#createcompatiblerendertarget)|현재 렌더링 대상과 호환 되는 중간 오프 스크린을 그리는 동안 사용할 새 비트맵 렌더링 대상을 만듭니다.|
|[CRenderTarget::D estroy](#destroy)|하나 이상의 리소스를 삭제 합니다.|
|[CRenderTarget::D etach](#detach)|개체에서 렌더링 대상 인터페이스를 분리 합니다.|
|[CRenderTarget::D rawBitmap](#drawbitmap)|지정 된 IDWriteTextLayout 개체에 설명 된 서식 있는 텍스트를 그립니다.|
|[CRenderTarget::D rawEllipse](#drawellipse)|지정 된 스트로크 스타일을 사용 하 여 지정 된 타원의 윤곽선을 그립니다.|
|[CRenderTarget::D rawGeometry](#drawgeometry)|지정 된 스트로크 스타일을 사용 하 여 지정 된 기 하 도형의 윤곽선을 그립니다.|
|[CRenderTarget::D rawGlyphRun](#drawglyphrun)|지정 된 문자 모양을 그립니다.|
|[CRenderTarget::D rawLine](#drawline)|지정 된 스트로크 스타일을 사용 하 여 지정 된 요소 사이에 선을 그립니다.|
|[CRenderTarget::D rawRectangle](#drawrectangle)|지정 된 크기와 스트로크 스타일을 가진 사각형의 윤곽선을 그립니다.|
|[CRenderTarget::D rawRoundedRectangle](#drawroundedrectangle)|지정 된 스트로크 스타일을 사용 하 여 지정 된 모퉁이가 둥근 사각형의 윤곽선을 그립니다.|
|[CRenderTarget::D rawText](#drawtext)|IDWriteTextFormat 개체에서 제공 하는 형식 정보를 사용 하 여 지정 된 텍스트를 그립니다.|
|[CRenderTarget::D rawTextLayout](#drawtextlayout)|지정 된 IDWriteTextLayout 개체에 설명 된 서식 있는 텍스트를 그립니다.|
|[CRenderTarget:: EndDraw](#enddraw)|렌더링 대상에서 그리기 작업을 종료 하 고 현재 오류 상태 및 관련 태그를 나타냅니다.|
|[CRenderTarget:: FillEllipse](#fillellipse)|지정 된 타원의 내부를 그립니다.|
|[CRenderTarget:: FillGeometry](#fillgeometry)|지정 된 기 하 도형의 내부를 그립니다.|
|[CRenderTarget:: FillMesh](#fillmesh)|지정 된 망상의 내부를 그립니다.|
|[CRenderTarget:: FillOpacityMask](#fillopacitymask)|지정 된 비트맵에 설명 된 불투명 마스크를 브러시에 적용 하 고 해당 브러시를 사용 하 여 렌더링 대상의 영역을 그립니다.|
|[CRenderTarget:: FillRectangle](#fillrectangle)|지정 된 사각형의 내부를 그립니다.|
|[CRenderTarget:: FillRoundedRectangle](#fillroundedrectangle)|지정 된 모퉁이가 둥근 사각형의 내부를 그립니다.|
|[CRenderTarget:: Flush](#flush)|보류 중인 모든 그리기 명령을 실행 합니다.|
|[CRenderTarget:: GetAntialiasMode](#getantialiasmode)|텍스트가 아닌 그리기 작업의 현재 앤티 앨리어싱 모드를 검색 합니다.|
|[CRenderTarget:: GetDpi](#getdpi)|렌더링 대상의 DPI (인치당 도트 수)를 반환 합니다.|
|[CRenderTarget:: GetMaximumBitmapSize](#getmaximumbitmapsize)|렌더링 대상에서 지 원하는 하나의 비트맵 차원에 대 한 최대 크기 (장치 종속 단위 (픽셀))를 가져옵니다.|
|[CRenderTarget:: GetPixelFormat](#getpixelformat)|렌더링 대상의 픽셀 형식 및 알파 모드를 검색 합니다.|
|[CRenderTarget:: GetPixelSize](#getpixelsize)|장치 픽셀에서 렌더링 대상의 크기를 반환 합니다.|
|[CRenderTarget:: GetRenderTarget](#getrendertarget)|ID2D1RenderTarget 인터페이스를 반환 합니다.|
|[CRenderTarget:: GetSize](#getsize)|렌더링 대상의 크기를 장치 독립적 픽셀 단위로 반환 합니다.|
|[CRenderTarget:: GetTags](#gettags)|이후 그리기 작업의 레이블을 가져옵니다.|
|[CRenderTarget:: GetTextAntialiasMode](#gettextantialiasmode)|텍스트 및 문자 모양 그리기 작업의 현재 앤티엘리어싱 모드를 가져옵니다.|
|[CRenderTarget:: GetTextRenderingParams](#gettextrenderingparams)|렌더링 대상의 현재 텍스트 렌더링 옵션을 검색 합니다.|
|[CRenderTarget:: GetTransform](#gettransform)|지정 된 변환을 렌더링 대상에 적용 하 여 기존 변환을 바꿉니다. 모든 후속 그리기 작업은 변환 된 공간에서 발생 합니다.|
|[CRenderTarget:: IsSupported](#issupported)|렌더링 대상이 지정 된 속성을 지원 하는지 여부를 나타냅니다.|
|[CRenderTarget:: IsValid](#isvalid)|리소스 유효성 검사|
|[CRenderTarget::P opAxisAlignedClip](#popaxisalignedclip)|렌더링 대상에서 마지막 축에 맞춰진 클립을 제거 합니다. 이 메서드를 호출한 후에는 클립이 이후 그리기 작업에 더 이상 적용 되지 않습니다.|
|[CRenderTarget::P opLayer](#poplayer)|마지막 PushLayer 호출로 지정 된 계층으로 그리기 작업 리디렉션을 중지 합니다.|
|[CRenderTarget::P ushAxisAlignedClip](#pushaxisalignedclip)|렌더링 대상에서 마지막 축에 맞춰진 클립을 제거 합니다. 이 메서드를 호출한 후에는 클립이 이후 그리기 작업에 더 이상 적용 되지 않습니다.|
|[CRenderTarget::P ushLayer](#pushlayer)|PopLayer가 호출 될 때까지 이후의 모든 그리기 작업을 받도록 지정 된 계층을 렌더링 대상에 추가 합니다.|
|[CRenderTarget:: RestoreDrawingState](#restoredrawingstate)|렌더링 대상의 그리기 상태를 지정 된 ID2D1DrawingStateBlock 설정 합니다.|
|[CRenderTarget:: SaveDrawingState](#savedrawingstate)|현재 그리기 상태를 지정 된 ID2D1DrawingStateBlock에 저장 합니다.|
|[CRenderTarget:: SetAntialiasMode](#setantialiasmode)|렌더링 대상의 앤티엘리어싱 모드를 설정 합니다. 앤티 앨리어싱 모드는 텍스트 및 문자 모양 그리기 작업을 제외 하 고 모든 후속 그리기 작업에 적용 됩니다.|
|[CRenderTarget:: SetDpi](#setdpi)|렌더링 대상의 DPI (인치당 도트 수)를 설정 합니다.|
|[CRenderTarget:: SetTags](#settags)|이후 그리기 작업에 사용할 레이블을 지정 합니다.|
|[CRenderTarget:: SetTextAntialiasMode](#settextantialiasmode)|후속 텍스트 및 문자 모양 그리기 작업에 사용할 앤티엘리어싱 모드를 지정 합니다.|
|[CRenderTarget:: SetTextRenderingParams](#settextrenderingparams)|모든 후속 텍스트 및 문자 모양 그리기 작업에 적용할 텍스트 렌더링 옵션을 지정 합니다.|
|[CRenderTarget:: SetTransform](#settransform)|오버로드됨. 지정 된 변환을 렌더링 대상에 적용 하 여 기존 변환을 바꿉니다. 모든 후속 그리기 작업은 변환 된 공간에서 발생 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CRenderTarget:: VerifyResource](#verifyresource)|CD2DResource 개체 유효성을 확인 합니다. 아직 없는 경우 개체를 만듭니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CRenderTarget:: operator ID2D1RenderTarget *](#operator_id2d1rendertarget_star)|ID2D1RenderTarget 인터페이스를 반환 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CRenderTarget:: m_lstResources](#m_lstresources)|CD2DResource 개체에 대 한 포인터 목록입니다.|
|[CRenderTarget:: m_pRenderTarget](#m_prendertarget)|ID2D1RenderTarget 개체에 대 한 포인터입니다.|
|[CRenderTarget:: m_pTextFormatDefault](#m_ptextformatdefault)|기본 텍스트 형식을 포함 하는 CD2DTextFormat 개체에 대 한 포인터입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="crendertargetcrendertarget"></a><a name="_dtorcrendertarget"></a> CRenderTarget:: ~ CRenderTarget

소멸자입니다. 렌더링 대상 개체가 제거 될 때 호출 됩니다.

```
virtual ~CRenderTarget();
```

## <a name="crendertargetattach"></a><a name="attach"></a> CRenderTarget:: Attach

기존 렌더링 대상 인터페이스를 개체에 연결 합니다.

```cpp
void Attach(ID2D1RenderTarget* pRenderTarget);
```

### <a name="parameters"></a>매개 변수

*pRenderTarget*<br/>
기존 렌더링 대상 인터페이스입니다. NULL 일 수 없음

## <a name="crendertargetbegindraw"></a><a name="begindraw"></a> CRenderTarget:: BeginDraw

이 렌더링 대상에서 그리기를 시작 합니다.

```cpp
void BeginDraw();
```

## <a name="crendertargetclear"></a><a name="clear"></a> CRenderTarget:: Clear

그리기 영역을 지정 된 색으로 지웁니다.

```cpp
void Clear(D2D1_COLOR_F color);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
그리기 영역이 지워지는 색입니다.

## <a name="crendertargetcolorref_to_d2dcolor"></a><a name="colorref_to_d2dcolor"></a> CRenderTarget:: COLORREF_TO_D2DCOLOR

GDI 색 및 알파 값을 D2D1_COLOR_F 개체로 변환 합니다.

```
static D2D1_COLOR_F COLORREF_TO_D2DCOLOR(
    COLORREF color,
    int nAlpha = 255);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
RGB 값입니다.

*nAlpha*

### <a name="return-value"></a>반환 값

D2D1_COLOR_F 값입니다.

## <a name="crendertargetcreatecompatiblerendertarget"></a><a name="createcompatiblerendertarget"></a> CRenderTarget:: CreateCompatibleRenderTarget

현재 렌더링 대상과 호환 되는 중간 오프 스크린을 그리는 동안 사용할 새 비트맵 렌더링 대상을 만듭니다.

```
BOOL CreateCompatibleRenderTarget(
    CBitmapRenderTarget& bitmapTarget,
    CD2DSizeF sizeDesired = CD2DSizeF(0., 0.),
    CD2DSizeU sizePixelDesired = CD2DSizeU(0, 0),
    D2D1_PIXEL_FORMAT* desiredFormat = NULL,
    D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS options = D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS_NONE);
```

### <a name="parameters"></a>매개 변수

*bitmapTarget*<br/>
이 메서드는 반환 될 때 새 비트맵 렌더링 대상에 대 한 포인터의 주소를 포함 합니다. 이 매개 변수는 초기화되지 않은 상태로 전달됩니다.

*sizeDesired*<br/>
원본 렌더링 대상과 다르거나 NULL 이어야 하는 경우 장치 독립적 픽셀에 있는 새 렌더링 대상의 원하는 크기입니다. 자세한 내용은 설명 섹션을 참조하세요.

*sizePixelDesired*<br/>
원래 렌더링 대상과 다르거나 NULL 인 경우 새 렌더링 대상의 원하는 크기 (픽셀)입니다. 자세한 내용은 설명 섹션을 참조하세요.

*desiredFormat*<br/>
새 렌더링 대상의 원하는 픽셀 형식 및 알파 모드 이거나 NULL입니다. 픽셀 형식이 DXGI_FORMAT_UNKNOWN로 설정 되거나이 매개 변수가 null 이면 새 렌더링 대상은 원래 렌더링 대상과 동일한 픽셀 형식을 사용 합니다. 알파 모드가 D2D1_ALPHA_MODE_UNKNOWN 되거나이 매개 변수가 NULL 이면 새 렌더링 대상의 알파 모드는 기본적으로 D2D1_ALPHA_MODE_PREMULTIPLIED입니다. 지원 되는 픽셀 형식에 대 한 자세한 내용은 지원 되는 픽셀 형식 및 알파 모드를 참조 하세요.

*options*<br/>
새 렌더링 대상이 GDI와 호환 되어야 하는지 여부를 지정 하는 값입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="crendertargetcrendertarget"></a><a name="crendertarget"></a> CRenderTarget:: CRenderTarget

CRenderTarget 개체를 생성 합니다.

```
CRenderTarget();
```

## <a name="crendertargetdestroy"></a><a name="destroy"></a> CRenderTarget::D estroy

하나 이상의 리소스를 삭제 합니다.

```
BOOL Destroy(BOOL bDeleteResources = TRUE);
```

### <a name="parameters"></a>매개 변수

*bDeleteResources*<br/>
BDeleteResources가 TRUE 이면 m_lstResources에 있는 모든 리소스가 자동으로 삭제 됩니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="crendertargetdetach"></a><a name="detach"></a> CRenderTarget::D etach

개체에서 렌더링 대상 인터페이스를 분리 합니다.

```
ID2D1RenderTarget* Detach ();
```

### <a name="return-value"></a>반환 값

분리 된 렌더링 대상 인터페이스에 대 한 포인터입니다.

## <a name="crendertargetdrawbitmap"></a><a name="drawbitmap"></a> CRenderTarget::D rawBitmap

지정 된 IDWriteTextLayout 개체에 설명 된 서식 있는 텍스트를 그립니다.

```cpp
void DrawBitmap(
    CD2DBitmap* pBitmap,
    const CD2DRectF& rectDest,
    float fOpacity = 1.0,
    D2D1_BITMAP_INTERPOLATION_MODE interpolationMode = D2D1_BITMAP_INTERPOLATION_MODE_LINEAR,
    const CD2DRectF* pRectSrc = NULL);
```

### <a name="parameters"></a>매개 변수

*pBitmap*<br/>
렌더링할 비트맵입니다.

*rectDest*<br/>
비트맵을 그릴 영역의 크기와 위치 (렌더링 대상의 좌표 공간에 있는 장치 독립적 픽셀)입니다. 사각형이 잘 정렬 되지 않은 경우 아무 것도 그려지지 않지만 렌더링 대상이 오류 상태가 되지 않습니다.

*fOpacity*<br/>
비트맵에 적용할 불투명도 값을 지정 하는 0.0 f와 1.0 f (포함) 사이의 값입니다. 이 값은 비트맵 콘텐츠의 알파 값에 곱합니다.

*interpolationMode*<br/>
그리기 작업에서 비트맵의 크기를 조정 하거나 회전할 때 사용할 보간 모드입니다.

*pRectSrc*<br/>
그릴 비트맵 내 영역의 크기와 위치 (비트맵 좌표 공간의 장치 독립적 픽셀)입니다.

## <a name="crendertargetdrawellipse"></a><a name="drawellipse"></a> CRenderTarget::D rawEllipse

지정 된 스트로크 스타일을 사용 하 여 지정 된 타원의 윤곽선을 그립니다.

```cpp
void DrawEllipse(
    const CD2DEllipse& ellipse,
    CD2DBrush* pBrush,
    FLOAT fStrokeWidth = 1.0,
    ID2D1StrokeStyle* strokeStyle = NULL);
```

### <a name="parameters"></a>매개 변수

*타원형*<br/>
그릴 타원의 위치와 반지름 (장치 독립적 픽셀)입니다.

*pBrush*<br/>
타원의 윤곽선을 그리는 데 사용 되는 브러시입니다.

*fStrokeWidth*<br/>
타원 스트로크의 두께입니다. 스트로크가 타원의 윤곽선 가운데에 배치 됩니다.

*strokeStyle*<br/>
타원의 윤곽선에 적용할 스트로크의 스타일 이거나, 단색 스트로크를 그리려면 NULL입니다.

## <a name="crendertargetdrawgeometry"></a><a name="drawgeometry"></a> CRenderTarget::D rawGeometry

지정 된 스트로크 스타일을 사용 하 여 지정 된 기 하 도형의 윤곽선을 그립니다.

```cpp
void DrawGeometry(
    CD2DGeometry* pGeometry,
    CD2DBrush* pBrush,
    FLOAT fStrokeWidth = 1.0,
    ID2D1StrokeStyle* strokeStyle = NULL);
```

### <a name="parameters"></a>매개 변수

*pGeometry*<br/>
그릴 기 하 도형입니다.

*pBrush*<br/>
기 하 도형의 스트로크를 그리는 데 사용 되는 브러시입니다.

*fStrokeWidth*<br/>
기 하 도형의 스트로크 두께입니다. 스트로크는 기 하 도형의 윤곽선 가운데에 있습니다.

*strokeStyle*<br/>
기 하 도형의 윤곽선에 적용할 스트로크의 스타일 또는 단색 스트로크를 그리는 경우 NULL입니다.

## <a name="crendertargetdrawglyphrun"></a><a name="drawglyphrun"></a> CRenderTarget::D rawGlyphRun

지정 된 문자 모양을 그립니다.

```cpp
void DrawGlyphRun(
    const CD2DPointF& ptBaseLineOrigin,
    const DWRITE_GLYPH_RUN& glyphRun,
    CD2DBrush* pForegroundBrush,
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```

### <a name="parameters"></a>매개 변수

*ptBaseLineOrigin*<br/>
문자 모양 기준선의 원본 (장치 독립적 픽셀)입니다.

*glyphRun*<br/>
렌더링할 문자 모양입니다.

*pForegroundBrush*<br/>
지정 된 문자 모양을 그리는 데 사용 되는 브러시입니다.

*measuringMode*<br/>
서식 지정 시 텍스트 측정에 문자 모양 메트릭을 사용 하는 방법을 나타내는 값입니다. 기본값은 DWRITE_MEASURING_MODE_NATURAL입니다.

## <a name="crendertargetdrawline"></a><a name="drawline"></a> CRenderTarget::D rawLine

지정 된 스트로크 스타일을 사용 하 여 지정 된 요소 사이에 선을 그립니다.

```cpp
void DrawLine(
    const CD2DPointF& ptFrom,
    const CD2DPointF& ptTo,
    CD2DBrush* pBrush,
    FLOAT fStrokeWidth = 1.0,
    ID2D1StrokeStyle* strokeStyle = NULL);
```

### <a name="parameters"></a>매개 변수

*ptFrom*<br/>
장치 독립적 픽셀 단위로 된 줄의 시작점입니다.

*ptTo*<br/>
장치 독립적 픽셀 단위의 선 끝점입니다.

*pBrush*<br/>
선의 스트로크를 칠하는 데 사용 되는 브러시입니다.

*fStrokeWidth*<br/>
스트로크 너비를 지정 하는 0.0 f 보다 크거나 같은 값입니다. 이 매개 변수를 지정 하지 않으면 기본값은 1.0 f입니다. 스트로크가 선 가운데에 배치 됩니다.

*strokeStyle*<br/>
칠할 스트로크의 스타일 이거나, 실선을 그리려면 NULL입니다.

## <a name="crendertargetdrawrectangle"></a><a name="drawrectangle"></a> CRenderTarget::D rawRectangle

지정 된 크기와 스트로크 스타일을 가진 사각형의 윤곽선을 그립니다.

```cpp
void DrawRectangle(
    const CD2DRectF& rectangle,
    CD2DBrush* pBrush,
    FLOAT fStrokeWidth = 1.0,
    ID2D1StrokeStyle* strokeStyle = NULL);
```

### <a name="parameters"></a>매개 변수

*사각형*<br/>
그릴 사각형의 크기 (장치 독립적 픽셀)입니다.

*pBrush*<br/>
사각형의 스트로크를 그리는 데 사용 되는 브러시입니다.

*fStrokeWidth*<br/>
사각형 스트로크의 너비를 지정 하는 0.0 f 보다 크거나 같은 값입니다. 스트로크는 사각형의 윤곽선 가운데에 배치 됩니다.

*strokeStyle*<br/>
칠할 스트로크의 스타일 이거나, 단색 스트로크를 그리려면 NULL입니다.

## <a name="crendertargetdrawroundedrectangle"></a><a name="drawroundedrectangle"></a> CRenderTarget::D rawRoundedRectangle

지정 된 스트로크 스타일을 사용 하 여 지정 된 모퉁이가 둥근 사각형의 윤곽선을 그립니다.

```cpp
void DrawRoundedRectangle(
    const CD2DRoundedRect& rectRounded,
    CD2DBrush* pBrush,
    FLOAT fStrokeWidth = 1.0,
    ID2D1StrokeStyle* strokeStyle = NULL);
```

### <a name="parameters"></a>매개 변수

*rectRounded*<br/>
그릴 모퉁이가 둥근 사각형의 크기 (장치 독립적 픽셀)입니다.

*pBrush*<br/>
모퉁이가 둥근 사각형의 윤곽선을 그리는 데 사용 되는 브러시입니다.

*fStrokeWidth*<br/>
모퉁이가 둥근 사각형 스트로크의 너비입니다. 스트로크가 모퉁이가 둥근 사각형의 윤곽선 가운데에 배치 됩니다. 기본값은 1.0 f입니다.

*strokeStyle*<br/>
모퉁이가 둥근 사각형 스트로크의 스타일 이거나, 단색 스트로크를 그리려면 NULL입니다. 기본값은 NULL입니다.

## <a name="crendertargetdrawtext"></a><a name="drawtext"></a> CRenderTarget::D rawText

IDWriteTextFormat 개체에서 제공 하는 형식 정보를 사용 하 여 지정 된 텍스트를 그립니다.

```cpp
void DrawText(
    const CString& strText,
    const CD2DRectF& rectangle,
    CD2DBrush* pForegroundBrush,
    CD2DTextFormat* textFormat = NULL,
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE,
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```

### <a name="parameters"></a>매개 변수

*strText*<br/>
그릴 유니코드 문자 배열에 대 한 포인터입니다.

*사각형*<br/>
텍스트를 그릴 영역의 크기와 위치입니다.

*pForegroundBrush*<br/>
텍스트를 그리는 데 사용되는 브러시입니다.

*textFormat*<br/>
글꼴, 글꼴 크기 및 흐름 방향과 같이 그릴 텍스트의 형식 세부 정보를 설명 하는 개체입니다.

*options*<br/>
텍스트를 픽셀 경계에 맞춰야 하는지 여부와 텍스트를 레이아웃 사각형으로 잘라내야 할지 여부를 나타내는 값입니다. 기본값은 D2D1_DRAW_TEXT_OPTIONS_NONE입니다 .이 값은 텍스트를 픽셀 경계로 맞춘 후 레이아웃 사각형으로 잘리지 않아야 함을 나타냅니다.

*measuringMode*<br/>
서식 지정 시 텍스트 측정에 문자 모양 메트릭을 사용 하는 방법을 나타내는 값입니다. 기본값은 DWRITE_MEASURING_MODE_NATURAL입니다.

## <a name="crendertargetdrawtextlayout"></a><a name="drawtextlayout"></a> CRenderTarget::D rawTextLayout

지정 된 IDWriteTextLayout 개체에 설명 된 서식 있는 텍스트를 그립니다.

```cpp
void DrawTextLayout(
    const CD2DPointF& ptOrigin,
    CD2DTextLayout* textLayout,
    CD2DBrush* pBrushForeground,
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE);
```

### <a name="parameters"></a>매개 변수

*ptOrigin*<br/>
TextLayout으로 설명 되는 텍스트의 왼쪽 위 모퉁이가 그려지는 장치 독립적 픽셀에 설명 된 점입니다.

*textLayout*<br/>
그릴 서식 있는 텍스트입니다. ID2D1Resource에서 상속 하지 않는 그리기 효과는 무시 됩니다. 브러시가 아닌 ID2D1Resource에서 상속 되는 그리기 효과가 있는 경우이 메서드가 실패 하 고 렌더링 대상이 오류 상태로 전환 됩니다.

*pBrushForeground*<br/>
지정 된 브러시를 그리기 효과로 사용 하지 않는 textLayout의 텍스트를 그리는 데 사용 되는 브러시입니다 (IDWriteTextLayout:: SetDrawingEffect 메서드를 사용 하 여 지정).

*options*<br/>
텍스트를 픽셀 경계에 맞춰야 하는지 여부와 텍스트를 레이아웃 사각형으로 잘라내야 할지 여부를 나타내는 값입니다. 기본값은 D2D1_DRAW_TEXT_OPTIONS_NONE입니다 .이 값은 텍스트를 픽셀 경계로 맞춘 후 레이아웃 사각형으로 잘리지 않아야 함을 나타냅니다.

## <a name="crendertargetenddraw"></a><a name="enddraw"></a> CRenderTarget:: EndDraw

렌더링 대상에서 그리기 작업을 종료 하 고 현재 오류 상태 및 관련 태그를 나타냅니다.

```
HRESULT EndDraw();
```

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="crendertargetfillellipse"></a><a name="fillellipse"></a> CRenderTarget:: FillEllipse

지정 된 타원의 내부를 그립니다.

```cpp
void FillEllipse(
    const CD2DEllipse& ellipse,
    CD2DBrush* pBrush);
```

### <a name="parameters"></a>매개 변수

*타원형*<br/>
칠할 타원의 위치 및 반지름 (장치 독립적 픽셀)입니다.

*pBrush*<br/>
타원의 내부를 그리는 데 사용 되는 브러시입니다.

## <a name="crendertargetfillgeometry"></a><a name="fillgeometry"></a> CRenderTarget:: FillGeometry

지정 된 기 하 도형의 내부를 그립니다.

```cpp
void FillGeometry(
    CD2DGeometry* pGeometry,
    CD2DBrush* pBrush,
    CD2DBrush* pOpacityBrush = NULL);
```

### <a name="parameters"></a>매개 변수

*pGeometry*<br/>
그릴 기 하 도형입니다.

*pBrush*<br/>
기 하 도형의 내부를 그리는 데 사용 되는 브러시입니다.

*pOpacityBrush*<br/>
기 하 도형에 적용할 불투명 마스크입니다. 불투명 마스크가 없는 경우 NULL입니다. 불투명 마스크 (opacityBrush 매개 변수)를 지정 하는 경우 브러시는 x 및 y 확장 모드가 D2D1_EXTEND_MODE_CLAMP로 설정 된 ID2D1BitmapBrush 이어야 합니다. 자세한 내용은 설명 섹션을 참조하세요.

## <a name="crendertargetfillmesh"></a><a name="fillmesh"></a> CRenderTarget:: FillMesh

지정 된 망상의 내부를 그립니다.

```cpp
void FillMesh(
    CD2DMesh* pMesh,
    CD2DBrush* pBrush);
```

### <a name="parameters"></a>매개 변수

*pMesh*<br/>
그릴 메시입니다.

*pBrush*<br/>
메시를 그리는 데 사용 되는 브러시입니다.

## <a name="crendertargetfillopacitymask"></a><a name="fillopacitymask"></a> CRenderTarget:: FillOpacityMask

지정 된 비트맵에 설명 된 불투명 마스크를 브러시에 적용 하 고 해당 브러시를 사용 하 여 렌더링 대상의 영역을 그립니다.

```cpp
void FillOpacityMask(
    CD2DBitmap* pOpacityMask,
    CD2DBrush* pBrush,
    D2D1_OPACITY_MASK_CONTENT content,
    const CD2DRectF& rectDest,
    const CD2DRectF& rectSrc);
```

### <a name="parameters"></a>매개 변수

*pOpacityMask*<br/>
칠할 타원의 위치 및 반지름 (장치 독립적 픽셀)입니다.

*pBrush*<br/>
DestinationRectangle에서 지정 하는 렌더링 대상의 영역을 그리는 데 사용 되는 브러시입니다.

*content*<br/>
불투명 마스크에 포함 된 콘텐츠 형식입니다. 값은 불투명도 마스크가 혼합 되는 색 공간을 결정 하는 데 사용 됩니다.

*rectDest*<br/>
그릴 렌더링 대상의 영역 (장치 독립적 픽셀)입니다.

*rectSrc*<br/>
불투명 마스크로 사용할 비트맵의 영역 (장치 독립적 픽셀)입니다.

## <a name="crendertargetfillrectangle"></a><a name="fillrectangle"></a> CRenderTarget:: FillRectangle

지정 된 사각형의 내부를 그립니다.

```cpp
void FillRectangle(
    const CD2DRectF& rectangle,
    CD2DBrush* pBrush);
```

### <a name="parameters"></a>매개 변수

*사각형*<br/>
그릴 사각형의 차원 (장치 독립적 픽셀)입니다.

*pBrush*<br/>
사각형의 내부를 그리는 데 사용 되는 브러시입니다.

## <a name="crendertargetfillroundedrectangle"></a><a name="fillroundedrectangle"></a> CRenderTarget:: FillRoundedRectangle

지정 된 모퉁이가 둥근 사각형의 내부를 그립니다.

```cpp
void FillRoundedRectangle(
    const CD2DRoundedRect& rectRounded,
    CD2DBrush* pBrush);
```

### <a name="parameters"></a>매개 변수

*rectRounded*<br/>
칠할 모퉁이가 둥근 사각형의 크기 (장치 독립적 픽셀)입니다.

*pBrush*<br/>
모퉁이가 둥근 사각형의 내부를 그리는 데 사용 되는 브러시입니다.

## <a name="crendertargetflush"></a><a name="flush"></a> CRenderTarget:: Flush

보류 중인 모든 그리기 명령을 실행 합니다.

```cpp
void Flush(
    D2D1_TAG* tag1 = NULL,
    D2D1_TAG* tag2 = NULL);
```

### <a name="parameters"></a>매개 변수

*tag1*<br/>
오류를 발생 시킨 그리기 작업의 태그를 포함 하거나 오류가 없는 경우 0을 포함 합니다. 이 매개 변수는 초기화되지 않은 상태로 전달됩니다.

*tag2*<br/>
오류를 발생 시킨 그리기 작업의 태그를 포함 하거나 오류가 없는 경우 0을 포함 합니다. 이 매개 변수는 초기화되지 않은 상태로 전달됩니다.

## <a name="crendertargetgetantialiasmode"></a><a name="getantialiasmode"></a> CRenderTarget:: GetAntialiasMode

텍스트가 아닌 그리기 작업의 현재 앤티 앨리어싱 모드를 검색 합니다.

```
D2D1_ANTIALIAS_MODE GetAntialiasMode() const;
```

### <a name="return-value"></a>반환 값

텍스트가 아닌 그리기 작업의 현재 앤티 앨리어싱 모드입니다.

## <a name="crendertargetgetdpi"></a><a name="getdpi"></a> CRenderTarget:: GetDpi

렌더링 대상의 DPI (인치당 도트 수)를 반환 합니다.

```
CD2DSizeF GetDpi() const;
```

### <a name="return-value"></a>반환 값

렌더링 대상의 DPI (인치당 도트 수)입니다.

## <a name="crendertargetgetmaximumbitmapsize"></a><a name="getmaximumbitmapsize"></a> CRenderTarget:: GetMaximumBitmapSize

렌더링 대상에서 지 원하는 하나의 비트맵 차원에 대 한 최대 크기 (장치 종속 단위 (픽셀))를 가져옵니다.

```
UINT32 GetMaximumBitmapSize() const;
```

### <a name="return-value"></a>반환 값

렌더링 대상에서 지 원하는 하나의 비트맵 차원에 대 한 최대 크기 (픽셀)입니다.

## <a name="crendertargetgetpixelformat"></a><a name="getpixelformat"></a> CRenderTarget:: GetPixelFormat

렌더링 대상의 픽셀 형식 및 알파 모드를 검색 합니다.

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>반환 값

렌더링 대상의 픽셀 형식 및 알파 모드입니다.

## <a name="crendertargetgetpixelsize"></a><a name="getpixelsize"></a> CRenderTarget:: GetPixelSize

장치 픽셀에서 렌더링 대상의 크기를 반환 합니다.

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>반환 값

장치 픽셀의 렌더링 대상 크기

## <a name="crendertargetgetrendertarget"></a><a name="getrendertarget"></a> CRenderTarget:: GetRenderTarget

ID2D1RenderTarget 인터페이스를 반환 합니다.

```
ID2D1RenderTarget* GetRenderTarget();
```

### <a name="return-value"></a>반환 값

ID2D1RenderTarget 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="crendertargetgetsize"></a><a name="getsize"></a> CRenderTarget:: GetSize

렌더링 대상의 크기를 장치 독립적 픽셀 단위로 반환 합니다.

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>반환 값

렌더링 대상의 현재 크기 (장치 독립적 픽셀)입니다.

## <a name="crendertargetgettags"></a><a name="gettags"></a> CRenderTarget:: GetTags

이후 그리기 작업의 레이블을 가져옵니다.

```cpp
void GetTags(
    D2D1_TAG* tag1 = NULL,
    D2D1_TAG* tag2 = NULL) const;
```

### <a name="parameters"></a>매개 변수

*tag1*<br/>
후속 그리기 작업의 첫 번째 레이블을 포함 합니다. 이 매개 변수는 초기화되지 않은 상태로 전달됩니다. NULL을 지정 하면이 매개 변수에 대 한 값이 검색 되지 않습니다.

*tag2*<br/>
후속 그리기 작업에 사용할 두 번째 레이블을 포함 합니다. 이 매개 변수는 초기화되지 않은 상태로 전달됩니다. NULL을 지정 하면이 매개 변수에 대 한 값이 검색 되지 않습니다.

## <a name="crendertargetgettextantialiasmode"></a><a name="gettextantialiasmode"></a> CRenderTarget:: GetTextAntialiasMode

텍스트 및 문자 모양 그리기 작업의 현재 앤티엘리어싱 모드를 가져옵니다.

```
D2D1_TEXT_ANTIALIAS_MODE GetTextAntialiasMode() const;
```

### <a name="return-value"></a>반환 값

텍스트 및 문자 모양 그리기 작업의 현재 앤티 앨리어싱 모드입니다.

## <a name="crendertargetgettextrenderingparams"></a><a name="gettextrenderingparams"></a> CRenderTarget:: GetTextRenderingParams

렌더링 대상의 현재 텍스트 렌더링 옵션을 검색 합니다.

```cpp
void GetTextRenderingParams(IDWriteRenderingParams** textRenderingParams);
```

### <a name="parameters"></a>매개 변수

*textRenderingParams*<br/>
이 메서드가 반환 될 때 렌더링 대상의 현재 텍스트 렌더링 옵션에 대 한 포인터의 주소를 textRenderingParamscontains 합니다.

## <a name="crendertargetgettransform"></a><a name="gettransform"></a> CRenderTarget:: GetTransform

렌더링 대상의 현재 변환을 가져옵니다.

```cpp
void GetTransform(D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>매개 변수

*transform*<br/>
이 값이 반환 되 면 렌더링 대상의 현재 변환이 포함 됩니다. 이 매개 변수는 초기화되지 않은 상태로 전달됩니다.

## <a name="crendertargetissupported"></a><a name="issupported"></a> CRenderTarget:: IsSupported

렌더링 대상이 지정 된 속성을 지원 하는지 여부를 나타냅니다.

```
BOOL IsSupported(const D2D1_RENDER_TARGET_PROPERTIES& renderTargetProperties) const;
```

### <a name="parameters"></a>매개 변수

*renderTargetProperties*<br/>
테스트할 렌더링 대상 속성입니다.

### <a name="return-value"></a>반환 값

지정 된 렌더링 대상 속성이이 렌더링 대상에서 지원 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="crendertargetisvalid"></a><a name="isvalid"></a> CRenderTarget:: IsValid

리소스 유효성 검사

```
BOOL IsValid() const;
```

### <a name="return-value"></a>반환 값

리소스가 올바르면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="crendertargetm_lstresources"></a><a name="m_lstresources"></a> CRenderTarget:: m_lstResources

CD2DResource 개체에 대 한 포인터 목록입니다.

```
CObList m_lstResources;
```

## <a name="crendertargetm_prendertarget"></a><a name="m_prendertarget"></a> CRenderTarget:: m_pRenderTarget

ID2D1RenderTarget 개체에 대 한 포인터입니다.

```
ID2D1RenderTarget* m_pRenderTarget;
```

## <a name="crendertargetm_ptextformatdefault"></a><a name="m_ptextformatdefault"></a> CRenderTarget:: m_pTextFormatDefault

기본 텍스트 형식을 포함 하는 CD2DTextFormat 개체에 대 한 포인터입니다.

```
CD2DTextFormat* m_pTextFormatDefault;
```

## <a name="crendertargetoperator-id2d1rendertarget"></a><a name="operator_id2d1rendertarget_star"></a> CRenderTarget:: operator ID2D1RenderTarget *

ID2D1RenderTarget 인터페이스를 반환 합니다.

```
operator ID2D1RenderTarget*();
```

### <a name="return-value"></a>반환 값

ID2D1RenderTarget 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="crendertargetpopaxisalignedclip"></a><a name="popaxisalignedclip"></a> CRenderTarget::P opAxisAlignedClip

렌더링 대상에서 마지막 축에 맞춰진 클립을 제거 합니다. 이 메서드를 호출한 후에는 클립이 이후 그리기 작업에 더 이상 적용 되지 않습니다.

```cpp
void PopAxisAlignedClip();
```

## <a name="crendertargetpoplayer"></a><a name="poplayer"></a> CRenderTarget::P opLayer

마지막 PushLayer 호출로 지정 된 계층으로 그리기 작업 리디렉션을 중지 합니다.

```cpp
void PopLayer();
```

## <a name="crendertargetpushaxisalignedclip"></a><a name="pushaxisalignedclip"></a> CRenderTarget::P ushAxisAlignedClip

렌더링 대상에서 마지막 축에 맞춰진 클립을 제거 합니다. 이 메서드를 호출한 후에는 클립이 이후 그리기 작업에 더 이상 적용 되지 않습니다.

```cpp
void PushAxisAlignedClip(
    const CD2DRectF& rectClip,
    D2D1_ANTIALIAS_MODE mode = D2D1_ANTIALIAS_MODE_PER_PRIMITIVE);
```

### <a name="parameters"></a>매개 변수

*rectClip*<br/>
클리핑 영역의 크기와 위치 (장치 독립적 픽셀)입니다.

*mode*<br/>
하위 픽셀 경계를 포함 하는 클립 사각형의 가장자리를 그리고 장면 내용과 클립을 혼합 하는 데 사용 되는 앤티엘리어싱 모드입니다. 혼합은 PopAxisAlignedClip 메서드가 호출 될 때 한 번 수행 되며 계층 내의 각 기본 형식에는 적용 되지 않습니다.

## <a name="crendertargetpushlayer"></a><a name="pushlayer"></a> CRenderTarget::P ushLayer

PopLayer가 호출 될 때까지 이후의 모든 그리기 작업을 받도록 지정 된 계층을 렌더링 대상에 추가 합니다.

```cpp
void PushLayer(
    const D2D1_LAYER_PARAMETERS& layerParameters,
    CD2DLayer& layer);
```

### <a name="parameters"></a>매개 변수

*layerParameters*<br/>
계층의 콘텐츠 범위, 기하학적 마스크, 불투명도, 불투명 마스크 및 앤티 앨리어싱 옵션입니다.

*레이어도*<br/>
후속 그리기 작업을 받는 계층입니다.

## <a name="crendertargetrestoredrawingstate"></a><a name="restoredrawingstate"></a> CRenderTarget:: RestoreDrawingState

렌더링 대상의 그리기 상태를 지정 된 ID2D1DrawingStateBlock 설정 합니다.

```cpp
void RestoreDrawingState(ID2D1DrawingStateBlock& drawingStateBlock);
```

### <a name="parameters"></a>매개 변수

*drawingStateBlock*<br/>
렌더링 대상의 새 그리기 상태입니다.

## <a name="crendertargetsavedrawingstate"></a><a name="savedrawingstate"></a> CRenderTarget:: SaveDrawingState

현재 그리기 상태를 지정 된 ID2D1DrawingStateBlock에 저장 합니다.

```cpp
void SaveDrawingState(ID2D1DrawingStateBlock& drawingStateBlock) const;
```

### <a name="parameters"></a>매개 변수

*drawingStateBlock*<br/>
이 메서드가 반환 될 때 렌더링 대상의 현재 그리기 상태를 포함 합니다. 이 매개 변수를 메서드에 전달 하기 전에 초기화 해야 합니다.

## <a name="crendertargetsetantialiasmode"></a><a name="setantialiasmode"></a> CRenderTarget:: SetAntialiasMode

렌더링 대상의 앤티엘리어싱 모드를 설정 합니다. 앤티 앨리어싱 모드는 텍스트 및 문자 모양 그리기 작업을 제외 하 고 모든 후속 그리기 작업에 적용 됩니다.

```cpp
void SetAntialiasMode(D2D1_ANTIALIAS_MODE antialiasMode);
```

### <a name="parameters"></a>매개 변수

*antialiasMode*<br/>
이후 그리기 작업을 위한 앤티엘리어싱 모드입니다.

## <a name="crendertargetsetdpi"></a><a name="setdpi"></a> CRenderTarget:: SetDpi

렌더링 대상의 DPI (인치당 도트 수)를 설정 합니다.

```cpp
void SetDpi(const CD2DSizeF& sizeDPI);
```

### <a name="parameters"></a>매개 변수

*sizeDPI*<br/>
렌더링 대상의 가로/verticalDPI을 지정 하는 0 보다 크거나 같은 값입니다.

## <a name="crendertargetsettags"></a><a name="settags"></a> CRenderTarget:: SetTags

이후 그리기 작업에 사용할 레이블을 지정 합니다.

```cpp
void SetTags(
    D2D1_TAG tag1,
    D2D1_TAG tag2);
```

### <a name="parameters"></a>매개 변수

*tag1*<br/>
후속 그리기 작업에 적용할 레이블입니다.

*tag2*<br/>
후속 그리기 작업에 적용할 레이블입니다.

## <a name="crendertargetsettextantialiasmode"></a><a name="settextantialiasmode"></a> CRenderTarget:: SetTextAntialiasMode

후속 텍스트 및 문자 모양 그리기 작업에 사용할 앤티엘리어싱 모드를 지정 합니다.

```cpp
void SetTextAntialiasMode(D2D1_TEXT_ANTIALIAS_MODE textAntialiasMode);
```

### <a name="parameters"></a>매개 변수

*textAntialiasMode*<br/>
후속 텍스트 및 문자 모양 그리기 작업에 사용할 앤티엘리어싱 모드입니다.

## <a name="crendertargetsettextrenderingparams"></a><a name="settextrenderingparams"></a> CRenderTarget:: SetTextRenderingParams

모든 후속 텍스트 및 문자 모양 그리기 작업에 적용할 텍스트 렌더링 옵션을 지정 합니다.

```cpp
void SetTextRenderingParams(IDWriteRenderingParams* textRenderingParams = NULL);
```

### <a name="parameters"></a>매개 변수

*textRenderingParams*<br/>
모든 후속 텍스트 및 문자 모양 그리기 작업에 적용할 텍스트 렌더링 옵션입니다. 현재 텍스트 렌더링 옵션을 지우려면 NULL입니다.

## <a name="crendertargetsettransform"></a><a name="settransform"></a> CRenderTarget:: SetTransform

지정 된 변환을 렌더링 대상에 적용 하 여 기존 변환을 바꿉니다. 모든 후속 그리기 작업은 변환 된 공간에서 발생 합니다.

```cpp
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
void SetTransform(const D2D1_MATRIX_3X2_F& transform);
```

### <a name="parameters"></a>매개 변수

*transform*<br/>
렌더링 대상에 적용할 변환입니다.

## <a name="crendertargetverifyresource"></a><a name="verifyresource"></a> CRenderTarget:: VerifyResource

CD2DResource 개체 유효성을 확인 합니다. 아직 없는 경우 개체를 만듭니다.

```
BOOL VerifyResource(CD2DResource* pResource);
```

### <a name="parameters"></a>매개 변수

*보도 Ource*<br/>
CD2DResource 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

유효 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
