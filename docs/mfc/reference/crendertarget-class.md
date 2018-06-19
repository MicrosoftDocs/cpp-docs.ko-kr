---
title: CRenderTarget 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c7550e3e3d8bf7e49f9f93ea6e9a931d6567ef0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377760"
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
|[CRenderTarget::CRenderTarget](#crendertarget)|CRenderTarget 개체를 만듭니다.|  
|[CRenderTarget:: ~ CRenderTarget](#crendertarget__~crendertarget)|소멸자입니다. 렌더링 대상 개체가 소멸 될 때 호출 됩니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CRenderTarget::Attach](#attach)|기존 연결 개체를 대상 인터페이스를 렌더링 합니다.|  
|[CRenderTarget::BeginDraw](#begindraw)|이 렌더링 대상에 그리기를 시작 합니다.|  
|[CRenderTarget::Clear](#clear)|지정된 된 색을 그리기 영역을 지웁니다.|  
|[CRenderTarget::COLORREF_TO_D2DCOLOR](#colorref_to_d2dcolor)|GDI 색상 및 알파 값 D2D1_COLOR_F 개체로 변환합니다.|  
|[CRenderTarget::CreateCompatibleRenderTarget](#createcompatiblerendertarget)|현재 렌더링 대상과 호환 되는 중간 스크린 그림 하는 동안 사용 하기 위해 새 비트맵 렌더링 대상을 만듭니다.|  
|[CRenderTarget::Destroy](#destroy)|하나 이상의 리소스를 삭제합니다.|  
|[CRenderTarget::Detach](#detach)|렌더링 대상 인터페이스 개체에서 분리|  
|[CRenderTarget::DrawBitmap](#drawbitmap)|지정된 된 IDWriteTextLayout 개체에서 설명 된 서식 있는 텍스트를 그립니다.|  
|[CRenderTarget::DrawEllipse](#drawellipse)|지정 된 선 스타일을 사용 하 여 지정된 된 타원의 윤곽선을 그립니다.|  
|[CRenderTarget::DrawGeometry](#drawgeometry)|지정 된 선 스타일을 사용 하 여 지정 된 기 하 도형의 윤곽선을 그립니다.|  
|[CRenderTarget::DrawGlyphRun](#drawglyphrun)|지정 된 문자 모양을 그립니다.|  
|[CRenderTarget::DrawLine](#drawline)|지정 된 선 스타일을 사용 하 여 지정 된 점 사이의 선을 그립니다.|  
|[CRenderTarget::DrawRectangle](#drawrectangle)|지정 된 크기 및 선 스타일 들어 있는 사각형의 윤곽선을 그립니다.|  
|[CRenderTarget::DrawRoundedRectangle](#drawroundedrectangle)|지정 된 선 스타일을 사용 하 여 지정된 된 모퉁이가 둥근된 사각형의 윤곽선을 그립니다.|  
|[CRenderTarget::DrawText](#drawtext)|IDWriteTextFormat 개체에서 제공 된 형식 정보를 사용 하 여 지정된 된 텍스트를 그립니다.|  
|[CRenderTarget::DrawTextLayout](#drawtextlayout)|지정된 된 IDWriteTextLayout 개체에서 설명 된 서식 있는 텍스트를 그립니다.|  
|[CRenderTarget::EndDraw](#enddraw)|렌더링 대상에 대 한 그리기 작업을 종료 하 고 현재 오류 상태와 연결 된 태그를 나타냅니다.|  
|[CRenderTarget::FillEllipse](#fillellipse)|지정된 된 타원의 내부를 칠합니다.|  
|[CRenderTarget::FillGeometry](#fillgeometry)|지정 된 기 하 도형의 내부를 칠합니다.|  
|[CRenderTarget::FillMesh](#fillmesh)|지정된 된 메시의 내부를 칠합니다.|  
|[CRenderTarget::FillOpacityMask](#fillopacitymask)|브러시에 지정한 비트맵에서 설명 된 불투명 마스크를 적용 하 고 해당 브러시를 사용 하 여 렌더링 대상의 영역을 그리는 합니다.|  
|[CRenderTarget::FillRectangle](#fillrectangle)|지정된 된 사각형의 내부를 칠합니다.|  
|[CRenderTarget::FillRoundedRectangle](#fillroundedrectangle)|지정된 된 모퉁이가 둥근된 사각형의 내부를 칠합니다.|  
|[CRenderTarget::Flush](#flush)|모든 보류 중인 그리기 명령을 실행합니다.|  
|[CRenderTarget::GetAntialiasMode](#getantialiasmode)|텍스트가 아닌 그리기 작업에 대 한 현재 앨리어싱 사용 안 함 모드를 검색합니다.|  
|[CRenderTarget::GetDpi](#getdpi)|렌더링 대상의 dpi (인치당 도트) 반환|  
|[CRenderTarget::GetMaximumBitmapSize](#getmaximumbitmapsize)|렌더링 대상에서 지 원하는 한 비트맵 차원의의 장치 독립적 단위 (픽셀)의 최대 크기를 가져옵니다.|  
|[CRenderTarget::GetPixelFormat](#getpixelformat)|렌더링 대상의 픽셀 형식 및 알파 모드 검색|  
|[CRenderTarget::GetPixelSize](#getpixelsize)|렌더링 대상의 크기 (장치 픽셀)를 반환|  
|[CRenderTarget::GetRenderTarget](#getrendertarget)|반환 ID2D1RenderTarget 인터페이스|  
|[CRenderTarget::GetSize](#getsize)|장치 독립적 픽셀 단위로 렌더링 대상의 크기를 반환합니다.|  
|[CRenderTarget::GetTags](#gettags)|후속 그리기 작업에 대 한 레이블을 가져옵니다.|  
|[CRenderTarget::GetTextAntialiasMode](#gettextantialiasmode)|텍스트 및 문자 모양 그리기 작업에 대 한 현재 앨리어싱 사용 안 함 모드를 가져옵니다.|  
|[CRenderTarget::GetTextRenderingParams](#gettextrenderingparams)|렌더링 대상의 현재 텍스트 렌더링 옵션을 검색합니다.|  
|[CRenderTarget::GetTransform](#gettransform)|기존 변환을 바꾸는 렌더링 대상으로 지정된 된 변환을 적용 합니다. 이후의 모든 그리기 작업은 변환 된 공간에서 발생 합니다.|  
|[CRenderTarget::IsSupported](#issupported)|렌더링 대상이 지정된 된 속성을 지원 하는지 여부를 나타냅니다.|  
|[CRenderTarget::IsValid](#isvalid)|리소스 유효성 검사|  
|[CRenderTarget::PopAxisAlignedClip](#popaxisalignedclip)|마지막 축에 맞춰진 클립 렌더링 대상에서 제거합니다. 이 메서드가 호출 되 면 클립은 더 이상 다음 그리기 작업에 적용 됩니다.|  
|[CRenderTarget::PopLayer](#poplayer)|마지막 PushLayer 변수로 지정 된 계층에 그리기 작업 리디렉션을 중지를 호출 합니다.|  
|[CRenderTarget::PushAxisAlignedClip](#pushaxisalignedclip)|마지막 축에 맞춰진 클립 렌더링 대상에서 제거합니다. 이 메서드가 호출 되 면 클립은 더 이상 다음 그리기 작업에 적용 됩니다.|  
|[CRenderTarget::PushLayer](#pushlayer)|PopLayer를 호출할 때까지 이후의 모든 그리기 작업을 받을 수 있도록 렌더링 대상으로 지정 된 계층을 추가 합니다.|  
|[CRenderTarget::RestoreDrawingState](#restoredrawingstate)|지정 된 ID2D1DrawingStateBlock의 렌더링 대상의 그리기 상태를 설정합니다.|  
|[CRenderTarget::SaveDrawingState](#savedrawingstate)|지정 된 ID2D1DrawingStateBlock를 현재 그리기 상태를 저장합니다.|  
|[CRenderTarget::SetAntialiasMode](#setantialiasmode)|렌더링 대상의 앨리어싱 사용 안 함 모드를 설정합니다. 앤티 앨리어싱 모드 이후의 모든 그리기 작업, 텍스트 및 문자 모양 그리기 작업에 적용 됩니다.|  
|[CRenderTarget::SetDpi](#setdpi)|렌더링 대상의 (DPI) 인치당 도트를 설정합니다.|  
|[CRenderTarget::SetTags](#settags)|후속 그리기 작업에 대 한 레이블을 지정합니다.|  
|[CRenderTarget::SetTextAntialiasMode](#settextantialiasmode)|후속 텍스트와 문자 모양 그리기 작업에 사용할 앨리어싱 사용 안 함 모드를 지정 합니다.|  
|[CRenderTarget::SetTextRenderingParams](#settextrenderingparams)|모든 후속 텍스트와 문자 모양 그리기 작업에 적용할 텍스트 렌더링 옵션을 지정 합니다.|  
|[CRenderTarget::SetTransform](#settransform)|오버로드됨. 기존 변환을 바꾸는 렌더링 대상으로 지정된 된 변환을 적용 합니다. 이후의 모든 그리기 작업은 변환 된 공간에서 발생 합니다.|  
  
### <a name="protected-methods"></a>보호된 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CRenderTarget::VerifyResource](#verifyresource)|CD2DResource 개체 validity; 확인 존재 하지 않은 경우 해당 개체를 만듭니다.|  
  
### <a name="public-operators"></a>Public 연산자  
  
|이름|설명|  
|----------|-----------------|  
|[CRenderTarget::operator ID2D1RenderTarget *](#operator_id2d1rendertarget_star)|반환 ID2D1RenderTarget 인터페이스|  
  
### <a name="protected-data-members"></a>보호된 데이터 멤버  
  
|이름|설명|  
|----------|-----------------|  
|[CRenderTarget::m_lstResources](#m_lstresources)|목록 CD2DResource 개체에 대 한 포인터입니다.|  
|[CRenderTarget::m_pRenderTarget](#m_prendertarget)|ID2D1RenderTarget 개체에 대 한 포인터입니다.|  
|[CRenderTarget::m_pTextFormatDefault](#m_ptextformatdefault)|기본 텍스트 서식을 포함 하는 CD2DTextFormat 개체에 대 한 포인터입니다.|  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxrendertarget.h  
  
##  <a name="_dtorcrendertarget"></a>  CRenderTarget:: ~ CRenderTarget  
 소멸자입니다. 렌더링 대상 개체가 소멸 될 때 호출 됩니다.  
  
```  
virtual ~CRenderTarget();
```  
  
##  <a name="attach"></a>  CRenderTarget::Attach  
 기존 연결 개체를 대상 인터페이스를 렌더링 합니다.  
  
```  
void Attach(ID2D1RenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>매개 변수  
 `pRenderTarget`  
 기존 렌더링 대상 인터페이스입니다. NULL 일 수 없습니다.  
  
##  <a name="begindraw"></a>  CRenderTarget::BeginDraw  
 이 렌더링 대상에 그리기를 시작 합니다.  
  
```  
void BeginDraw();
```  
  
##  <a name="clear"></a>  CRenderTarget::Clear  
 지정된 된 색을 그리기 영역을 지웁니다.  
  
```  
void Clear(D2D1_COLOR_F color);
```  
  
### <a name="parameters"></a>매개 변수  
 `color`  
 그리기 영역을 지워집니다 색입니다.  
  
##  <a name="colorref_to_d2dcolor"></a>  CRenderTarget::COLORREF_TO_D2DCOLOR  
 GDI 색상 및 알파 값 D2D1_COLOR_F 개체로 변환합니다.  
  
```  
static D2D1_COLOR_F COLORREF_TO_D2DCOLOR(
    COLORREF color,  
    int nAlpha = 255);
```  
  
### <a name="parameters"></a>매개 변수  
 `color`  
 RGB 값입니다.  
  
 `nAlpha`  
  
### <a name="return-value"></a>반환 값  
 D2D1_COLOR_F 값입니다.  
  
##  <a name="createcompatiblerendertarget"></a>  CRenderTarget::CreateCompatibleRenderTarget  
 현재 렌더링 대상과 호환 되는 중간 스크린 그림 하는 동안 사용 하기 위해 새 비트맵 렌더링 대상을 만듭니다.  
  
```  
BOOL CreateCompatibleRenderTarget(
    CBitmapRenderTarget& bitmapTarget,  
    CD2DSizeF sizeDesired = CD2DSizeF(0., 0.), 
    CD2DSizeU sizePixelDesired = CD2DSizeU(0, 0), 
    D2D1_PIXEL_FORMAT* desiredFormat = NULL,  
    D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS options = D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS_NONE);
```  
  
### <a name="parameters"></a>매개 변수  
 `bitmapTarget`  
 이 메서드가 반환 될 때 새 비트맵 렌더링 대상에 대 한 포인터의 주소를 포함 합니다. 이 매개 변수는 초기화되지 않은 상태로 전달됩니다.  
  
 `sizeDesired`  
 장치 독립적 픽셀 원래 달라 야 하는 경우 새 렌더링 대상의 원하는 크기 렌더 대상, 되었거나 NULL입니다. 자세한 내용은 설명 섹션을 참조하세요.  
  
 `sizePixelDesired`  
 원하는 크기의 픽셀 원래 달라 야 하는 경우 새 렌더링 대상 렌더 대상, 되었거나 NULL입니다. 자세한 내용은 설명 섹션을 참조하세요.  
  
 `desiredFormat`  
 원하는 픽셀 형식 및 새 알파 모드 렌더 대상, 또는 NULL입니다. 픽셀 형식을 DXGI_FORMAT_UNKNOWN로 설정 된 경우 또는이 매개 변수가 null 이면 원래 렌더링 대상으로 새 렌더링 대상에 같은 픽셀 형식을 사용 합니다. 알파 모드 D2D1_ALPHA_MODE_UNKNOWN 나이 매개 변수는 NULL을 하는 경우 새 렌더링 대상의 알파 모드 D2D1_ALPHA_MODE_PREMULTIPLIED 기본값이 됩니다. 지원 되는 픽셀 형식에 대 한 내용은 지원 되는 픽셀 형식 및 알파 모드를 참조 하십시오.  
  
 `options`  
 새 렌더링 대상 GDI와 호환 해야 하는지 여부를 지정 하는 값입니다.  
  
### <a name="return-value"></a>반환 값  
 메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환합니다.  
  
##  <a name="crendertarget"></a>  CRenderTarget::CRenderTarget  
 CRenderTarget 개체를 만듭니다.  
  
```  
CRenderTarget();
```  
  
##  <a name="destroy"></a>  CRenderTarget::Destroy  
 하나 이상의 리소스를 삭제합니다.  
  
```  
BOOL Destroy(BOOL bDeleteResources = TRUE);
```  
  
### <a name="parameters"></a>매개 변수  
 `bDeleteResources`  
 BDeleteResources 결과가 TRUE 이면 m_lstResources에 있는 리소스를 모두 자동으로 제거 됩니다.  
  
### <a name="return-value"></a>반환 값  
 메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환  
  
##  <a name="detach"></a>  CRenderTarget::Detach  
 렌더링 대상 인터페이스 개체에서 분리  
  
```  
ID2D1RenderTarget* Detach ();
```  
  
### <a name="return-value"></a>반환 값  
 대상 인터페이스를 렌더링 하는 분리 된에 대 한 포인터입니다.  
  
##  <a name="drawbitmap"></a>  CRenderTarget::DrawBitmap  
 지정된 된 IDWriteTextLayout 개체에서 설명 된 서식 있는 텍스트를 그립니다.  
  
```  
void DrawBitmap(
    CD2DBitmap* pBitmap,  
    const CD2DRectF& rectDest,  
    float fOpacity = 1.0,  
    D2D1_BITMAP_INTERPOLATION_MODE interpolationMode = D2D1_BITMAP_INTERPOLATION_MODE_LINEAR,  
    const CD2DRectF* pRectSrc = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 `pBitmap`  
 렌더링 하는 비트맵입니다.  
  
 `rectDest`  
 크기 및 위치 비트맵을 그리면 영역의 렌더링 대상의 좌표 공간에서 장치 독립적 픽셀 단위로. 사각형 잘 정렬 되지 않은 경우 아무 것도 그려지지, 있지만 렌더링 대상의 오류 상태에 들어가지 않습니다.  
  
 `fOpacity`  
 비트맵;에 적용 하는 데 사용할 불투명도 값을 지정 하는 0.0 f에서 1.0 f 까지의 사이의 값 비트맵의 콘텐츠의 알파 값에 대해이 값을 곱합니다.  
  
 `interpolationMode`  
 비트맵을 크기 조정 또는 그리기 작업으로 회전 하는 경우 사용 하는 보간 모드입니다.  
  
 `pRectSrc`  
 크기와 위치를 그릴 비트맵 내에서 영역의 비트맵의 좌표 공간에서 장치 독립적 픽셀 단위로 합니다.  
  
##  <a name="drawellipse"></a>  CRenderTarget::DrawEllipse  
 지정 된 선 스타일을 사용 하 여 지정된 된 타원의 윤곽선을 그립니다.  
  
```  
void DrawEllipse(
    const CD2DEllipse& ellipse,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 `ellipse`  
 위치 및 장치 독립적 픽셀에서을 그리려면 타원의 반지름입니다.  
  
 `pBrush`  
 타원의 개요를 그리는 데 사용 되는 브러시입니다.  
  
 `fStrokeWidth`  
 타원의 선의 두께입니다. 선의 가운데 타원의 개요에 표시 됩니다.  
  
 `strokeStyle`  
 타원의 윤곽선 또는 단색 스트로크를 그리는 데 NULL에 적용할 선의 스타일입니다.  
  
##  <a name="drawgeometry"></a>  CRenderTarget::DrawGeometry  
 지정 된 선 스타일을 사용 하 여 지정 된 기 하 도형의 윤곽선을 그립니다.  
  
```  
void DrawGeometry(
    CD2DGeometry* pGeometry,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 `pGeometry`  
 그릴 도형을 합니다.  
  
 `pBrush`  
 기 하 도형의 스트로크를 그리는 데 사용 되는 브러시입니다.  
  
 `fStrokeWidth`  
 기 하 도형의 선의 두께입니다. 선의 가운데 기 하 도형의 윤곽선에 표시 됩니다.  
  
 `strokeStyle`  
 기 하 도형의 윤곽선 또는 단색 스트로크를 그리는 데 NULL에 적용할 선의 스타일입니다.  
  
##  <a name="drawglyphrun"></a>  CRenderTarget::DrawGlyphRun  
 지정 된 문자 모양을 그립니다.  
  
```  
void DrawGlyphRun(
    const CD2DPointF& ptBaseLineOrigin,  
    const DWRITE_GLYPH_RUN& glyphRun,  
    CD2DBrush* pForegroundBrush,  
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```  
  
### <a name="parameters"></a>매개 변수  
 `ptBaseLineOrigin`  
 장치 독립적 픽셀은 문자 모양 기준의 원본입니다.  
  
 `glyphRun`  
 렌더링 하는 문자 모양입니다.  
  
 `pForegroundBrush`  
 지정 된 문자 모양을 그리는 데 사용 되는 브러시입니다.  
  
 `measuringMode`  
 포맷 될 때 텍스트를 측정 하 문자 모양 메트릭을 사용 하는 방법을 나타내는 값입니다. 기본값은 DWRITE_MEASURING_MODE_NATURAL 합니다.  
  
##  <a name="drawline"></a>  CRenderTarget::DrawLine  
 지정 된 선 스타일을 사용 하 여 지정 된 점 사이의 선을 그립니다.  
  
```  
void DrawLine(
    const CD2DPointF& ptFrom,  
    const CD2DPointF& ptTo,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 `ptFrom`  
 장치 독립적 픽셀 단위로 선의 시작점입니다.  
  
 `ptTo`  
 장치 독립적 픽셀 단위로 선의 끝점입니다.  
  
 `pBrush`  
 선의 스트로크를 그리는 데 사용 되는 브러시입니다.  
  
 `fStrokeWidth`  
 선의 두께 지정 하는 0.0 f 보다 크거나 같은 값입니다. 이 매개 변수를 지정 하지 않으면 1.0 f로 기본값입니다. 선의 가운데 줄에 표시 됩니다.  
  
 `strokeStyle`  
 그림판을 또는 NULL을 실선이 표시를 그리는 선의 스타일입니다.  
  
##  <a name="drawrectangle"></a>  CRenderTarget::DrawRectangle  
 지정 된 크기 및 선 스타일 들어 있는 사각형의 윤곽선을 그립니다.  
  
```  
void DrawRectangle(
    const CD2DRectF& rect,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 `rect`  
 장치 독립적 픽셀에 그릴 사각형의 크기  
  
 `pBrush`  
 사각형의 스트로크를 그리는 데 사용 되는 브러시  
  
 `fStrokeWidth`  
 사각형의 스트로크 너비를 지정 하는 0.0 f 보다 크거나 같은 값입니다. 선의 가운데 사각형의 개요에 표시 됩니다.  
  
 `strokeStyle`  
 그림판 또는 NULL 단색 스트로크를 그리는 선의 스타일입니다.  
  
##  <a name="drawroundedrectangle"></a>  CRenderTarget::DrawRoundedRectangle  
 지정 된 선 스타일을 사용 하 여 지정된 된 모퉁이가 둥근된 사각형의 윤곽선을 그립니다.  
  
```  
void DrawRoundedRectangle(
    const CD2DRoundedRect& rectRounded,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 `rectRounded`  
 장치 독립적 픽셀에서을 그리려면 모퉁이가 둥근된 사각형의 크기입니다.  
  
 `pBrush`  
 모퉁이가 둥근된 사각형의 개요를 그리는 데 사용 되는 브러시입니다.  
  
 `fStrokeWidth`  
 모퉁이가 둥근된 사각형의 스트로크 너비입니다. 선의 가운데 모퉁이가 둥근된 사각형 윤곽선에 표시 됩니다. 기본값은 1.0 f.  
  
 `strokeStyle`  
 모퉁이가 둥근된 사각형의 선 또는 단색 스트로크를 그리는 데 NULL의 스타일입니다. 기본값은 NULL입니다.  
  
##  <a name="drawtext"></a>  CRenderTarget::DrawText  
 IDWriteTextFormat 개체에서 제공 된 형식 정보를 사용 하 여 지정된 된 텍스트를 그립니다.  
  
```  
void DrawText(
    const CString& strText,  
    const CD2DRectF& rect,  
    CD2DBrush* pForegroundBrush,  
    CD2DTextFormat* textFormat = NULL,  
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE,  
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```  
  
### <a name="parameters"></a>매개 변수  
 `strText`  
 그릴 유니코드 문자 배열에 대 한 포인터입니다.  
  
 `rect`  
 텍스트를 그리는 영역 위치와 크기입니다.  
  
 `pForegroundBrush`  
 텍스트를 그리는 데 사용 되는 브러시입니다.  
  
 `textFormat`  
 서식의 텍스트를 그릴, 글꼴, 글꼴 크기 및 흐름 방향을 같은 세부 사항을 설명 하는 개체입니다.  
  
 `options`  
 픽셀 경계에 텍스트 맞춰야 하는지 여부 및 텍스트 레이아웃 사각형에 맞게 잘림을 있는지 여부를 나타내는 값입니다. 기본값은 D2D1_DRAW_TEXT_OPTIONS_NONE 픽셀 경계에 맞춰야 하 텍스트가 레이아웃 사각형에 맞게 잘림을 나타냅니다.  
  
 `measuringMode`  
 포맷 될 때 텍스트를 측정 하 문자 모양 메트릭을 사용 하는 방법을 나타내는 값입니다. 기본값은 DWRITE_MEASURING_MODE_NATURAL 합니다.  
  
##  <a name="drawtextlayout"></a>  CRenderTarget::DrawTextLayout  
 지정된 된 IDWriteTextLayout 개체에서 설명 된 서식 있는 텍스트를 그립니다.  
  
```  
void DrawTextLayout(
    const CD2DPointF& ptOrigin,  
    CD2DTextLayout* textLayout,  
    CD2DBrush* pBrushForeground,  
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE);
```  
  
### <a name="parameters"></a>매개 변수  
 `ptOrigin`  
 장치 독립적 픽셀, textLayout으로 설명 하는 텍스트의 왼쪽 위 모서리를 그릴는 점입니다.  
  
 `textLayout`  
 그릴 서식 있는 텍스트입니다. ID2D1Resource에서 상속 되지 않는 모든 그리기 효과 무시 됩니다. 브러시 않는 ID2D1Resource에서 상속 하는 그리기 효과가 없으면이 메서드가 실패 하 고 렌더링 대상의 오류 상태에 배치 됩니다.  
  
 `pBrushForeground`  
 그리기 효과 (IDWriteTextLayout::SetDrawingEffect 메서드에 의해 지정 됨)로 연결 된 브러시를 아직 포함 되지 않은 textLayout에 텍스트를 그리는 데 사용 되는 브러시입니다.  
  
 `options`  
 픽셀 경계에 텍스트 맞춰야 하는지 여부 및 텍스트 레이아웃 사각형에 맞게 잘림을 있는지 여부를 나타내는 값입니다. 기본값은 D2D1_DRAW_TEXT_OPTIONS_NONE 픽셀 경계에 맞춰야 하 텍스트가 레이아웃 사각형에 맞게 잘림을 나타냅니다.  
  
##  <a name="enddraw"></a>  CRenderTarget::EndDraw  
 렌더링 대상에 대 한 그리기 작업을 종료 하 고 현재 오류 상태와 연결 된 태그를 나타냅니다.  
  
```  
HRESULT EndDraw();
```  
  
### <a name="return-value"></a>반환 값  
 메서드가 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 HRESULT 오류 코드를 반환합니다.  
  
##  <a name="fillellipse"></a>  CRenderTarget::FillEllipse  
 지정된 된 타원의 내부를 칠합니다.  
  
```  
void FillEllipse(
    const CD2DEllipse& ellipse,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>매개 변수  
 `ellipse`  
 위치 및 장치 독립적 픽셀을 그리는 타원의 반지름입니다.  
  
 `pBrush`  
 타원의 내부를 그리는 데 사용 되는 브러시입니다.  
  
##  <a name="fillgeometry"></a>  CRenderTarget::FillGeometry  
 지정 된 기 하 도형의 내부를 칠합니다.  
  
```  
void FillGeometry(
    CD2DGeometry* pGeometry,  
    CD2DBrush* pBrush,  
    CD2DBrush* pOpacityBrush = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 `pGeometry`  
 그리는 geometry 합니다.  
  
 `pBrush`  
 기 하 도형을 그리는 데 사용 되는 브러시의 내부입니다.  
  
 `pOpacityBrush`  
 불투명 마스크; 기 하 도형에 적용 하려면 NULL 불투명도 마스크가 없는입니다. 불투명 마스크 (opacityBrush 매개 변수)를 지정 하는 경우 브러시 D2D1_EXTEND_MODE_CLAMP로 설정 하는 해당 x 및 y 확장 모드를 가진 ID2D1BitmapBrush 이어야 합니다. 자세한 내용은 설명 섹션을 참조하세요.  
  
##  <a name="fillmesh"></a>  CRenderTarget::FillMesh  
 지정된 된 메시의 내부를 칠합니다.  
  
```  
void FillMesh(
    CD2DMesh* pMesh,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>매개 변수  
 `pMesh`  
 그리는 데 사용 되는 메시 합니다.  
  
 `pBrush`  
 메시를 그리는 데 사용 되는 브러시입니다.  
  
##  <a name="fillopacitymask"></a>  CRenderTarget::FillOpacityMask  
 브러시에 지정한 비트맵에서 설명 된 불투명 마스크를 적용 하 고 해당 브러시를 사용 하 여 렌더링 대상의 영역을 그리는 합니다.  
  
```  
void FillOpacityMask(
    CD2DBitmap* pOpacityMask,  
    CD2DBrush* pBrush,  
    D2D1_OPACITY_MASK_CONTENT content,  
    const CD2DRectF& rectDest,  
    const CD2DRectF& rectSrc);
```  
  
### <a name="parameters"></a>매개 변수  
 `pOpacityMask`  
 위치 및 장치 독립적 픽셀을 그리는 타원의 반지름입니다.  
  
 `pBrush`  
 DestinationRectangle로 지정 된 렌더링 대상의 영역을 그리는 데 사용 되는 브러시입니다.  
  
 `content`  
 불투명 마스크 콘텐츠의 형식을 포함합니다. 값은 불투명 마스크 혼합 됩니다 색 공간을 확인 하려면 사용 됩니다.  
  
 `rectDest`  
 장치 독립적 픽셀 그릴 렌더링 대상의 영역입니다.  
  
 `rectSrc`  
 불투명 마스크 (장치 독립적 픽셀)로 사용할 비트맵의 영역입니다.  
  
##  <a name="fillrectangle"></a>  CRenderTarget::FillRectangle  
 지정된 된 사각형의 내부를 칠합니다.  
  
```  
void FillRectangle(
    const CD2DRectF& rect,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>매개 변수  
 `rect`  
 장치 독립적 픽셀 단위로 그릴 사각형의 차원입니다.  
  
 `pBrush`  
 사각형을 그리는 데 사용 되는 브러시의 내부입니다.  
  
##  <a name="fillroundedrectangle"></a>  CRenderTarget::FillRoundedRectangle  
 지정된 된 모퉁이가 둥근된 사각형의 내부를 칠합니다.  
  
```  
void FillRoundedRectangle(
    const CD2DRoundedRect& rectRounded,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>매개 변수  
 `rectRounded`  
 장치 독립적 픽셀 단위로 그리는 데 모퉁이가 둥근된 사각형의 크기입니다.  
  
 `pBrush`  
 모퉁이가 둥근된 사각형의 내부를 그리는 데 사용 되는 브러시입니다.  
  
##  <a name="flush"></a>  CRenderTarget::Flush  
 모든 보류 중인 그리기 명령을 실행합니다.  
  
```  
void Flush(
    D2D1_TAG* tag1 = NULL,  
    D2D1_TAG* tag2 = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 `tag1`  
 그리기를 발생 시킨 오류 또는 0 오류가 있는 경우 작업에 대 한 태그를 포함 합니다. 이 매개 변수는 초기화되지 않은 상태로 전달됩니다.  
  
 `tag2`  
 그리기를 발생 시킨 오류 또는 0 오류가 있는 경우 작업에 대 한 태그를 포함 합니다. 이 매개 변수는 초기화되지 않은 상태로 전달됩니다.  
  
##  <a name="getantialiasmode"></a>  CRenderTarget::GetAntialiasMode  
 텍스트가 아닌 그리기 작업에 대 한 현재 앨리어싱 사용 안 함 모드를 검색합니다.  
  
```  
D2D1_ANTIALIAS_MODE GetAntialiasMode() const;  
```  
  
### <a name="return-value"></a>반환 값  
 텍스트가 아닌 그리기 작업에 대 한 현재 앨리어싱 사용 안 함 모드입니다.  
  
##  <a name="getdpi"></a>  CRenderTarget::GetDpi  
 렌더링 대상의 dpi (인치당 도트) 반환  
  
```  
CD2DSizeF GetDpi() const;  
```  
  
### <a name="return-value"></a>반환 값  
 렌더링 대상의 dpi (인치당 도트).  
  
##  <a name="getmaximumbitmapsize"></a>  CRenderTarget::GetMaximumBitmapSize  
 렌더링 대상에서 지 원하는 한 비트맵 차원의의 장치 독립적 단위 (픽셀)의 최대 크기를 가져옵니다.  
  
```  
UINT32 GetMaximumBitmapSize() const;  
```  
  
### <a name="return-value"></a>반환 값  
 렌더링 대상에서 지 원하는 한 비트맵 차원의 픽셀 단위로 최대 크기  
  
##  <a name="getpixelformat"></a>  CRenderTarget::GetPixelFormat  
 렌더링 대상의 픽셀 형식 및 알파 모드 검색  
  
```  
D2D1_PIXEL_FORMAT GetPixelFormat() const;  
```  
  
### <a name="return-value"></a>반환 값  
 렌더링 대상의 픽셀 형식 및 알파 모드  
  
##  <a name="getpixelsize"></a>  CRenderTarget::GetPixelSize  
 렌더링 대상의 크기 (장치 픽셀)를 반환  
  
```  
CD2DSizeU GetPixelSize() const;  
```  
  
### <a name="return-value"></a>반환 값  
 장치 픽셀 단위로 렌더링 대상의 크기  
  
##  <a name="getrendertarget"></a>  CRenderTarget::GetRenderTarget  
 반환 ID2D1RenderTarget 인터페이스  
  
```  
ID2D1RenderTarget* GetRenderTarget();
```  
  
### <a name="return-value"></a>반환 값  
 ID2D1RenderTarget 인터페이스 또는 개체가 아직 초기화 되지 않은 경우에 NULL 포인터입니다.  
  
##  <a name="getsize"></a>  CRenderTarget::GetSize  
 장치 독립적 픽셀 단위로 렌더링 대상의 크기를 반환합니다.  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>반환 값  
 장치 독립적 픽셀 단위로 렌더링 대상의 현재 크기  
  
##  <a name="gettags"></a>  CRenderTarget::GetTags  
 후속 그리기 작업에 대 한 레이블을 가져옵니다.  
  
```  
void GetTags(
    D2D1_TAG* tag1 = NULL,  
    D2D1_TAG* tag2 = NULL) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 `tag1`  
 후속 그리기 작업에 대 한 첫 번째 레이블을 포함합니다. 이 매개 변수는 초기화되지 않은 상태로 전달됩니다. NULL을 지정 하는 경우이 매개 변수 값이 없는 검색 됩니다.  
  
 `tag2`  
 후속 그리기 작업에 대 한 두 번째 레이블을 포함합니다. 이 매개 변수는 초기화되지 않은 상태로 전달됩니다. NULL을 지정 하는 경우이 매개 변수 값이 없는 검색 됩니다.  
  
##  <a name="gettextantialiasmode"></a>  CRenderTarget::GetTextAntialiasMode  
 텍스트 및 문자 모양 그리기 작업에 대 한 현재 앨리어싱 사용 안 함 모드를 가져옵니다.  
  
```  
D2D1_TEXT_ANTIALIAS_MODE GetTextAntialiasMode() const;  
```  
  
### <a name="return-value"></a>반환 값  
 텍스트 및 문자 모양 그리기 작업에 대 한 현재 앨리어싱 사용 안 함 모드입니다.  
  
##  <a name="gettextrenderingparams"></a>  CRenderTarget::GetTextRenderingParams  
 렌더링 대상의 현재 텍스트 렌더링 옵션을 검색합니다.  
  
```  
void GetTextRenderingParams(IDWriteRenderingParams** textRenderingParams);
```  
  
### <a name="parameters"></a>매개 변수  
 `textRenderingParams`  
 이 메서드가 반환 될 때 렌더링 대상에 대 한 포인터의 주소 textRenderingParamscontains의 현재 텍스트 렌더링 옵션입니다.  
  
##  <a name="gettransform"></a>  CRenderTarget::GetTransform  
 기존 변환을 바꾸는 렌더링 대상으로 지정된 된 변환을 적용 합니다. 이후의 모든 그리기 작업은 변환 된 공간에서 발생 합니다.  
  
```  
void GetTransform(D2D1_MATRIX_3X2_F* transform);
```  
  
### <a name="parameters"></a>매개 변수  
 `transform`  
 렌더링 대상에 적용할 변환입니다.  
  
##  <a name="issupported"></a>  CRenderTarget::IsSupported  
 렌더링 대상이 지정된 된 속성을 지원 하는지 여부를 나타냅니다.  
  
```  
BOOL IsSupported(const D2D1_RENDER_TARGET_PROPERTIES& renderTargetProperties) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 `renderTargetProperties`  
 테스트 하려면 렌더링 대상 속성  
  
### <a name="return-value"></a>반환 값  
 이 렌더링 대상;에서 지정 된 렌더링 대상 속성 지 원하는 경우 TRUE입니다. 그렇지 않으면 FALSE  
  
##  <a name="isvalid"></a>  CRenderTarget::IsValid  
 리소스 유효성 검사  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>반환 값  
 리소스 올바르면 TRUE입니다. 그렇지 않으면 FALSE입니다.  
  
##  <a name="m_lstresources"></a>  CRenderTarget::m_lstResources  
 목록 CD2DResource 개체에 대 한 포인터입니다.  
  
```  
CObList m_lstResources;  
```  
  
##  <a name="m_prendertarget"></a>  CRenderTarget::m_pRenderTarget  
 ID2D1RenderTarget 개체에 대 한 포인터입니다.  
  
```  
ID2D1RenderTarget* m_pRenderTarget;  
```  
  
##  <a name="m_ptextformatdefault"></a>  CRenderTarget::m_pTextFormatDefault  
 기본 텍스트 서식을 포함 하는 CD2DTextFormat 개체에 대 한 포인터입니다.  
  
```  
CD2DTextFormat* m_pTextFormatDefault;  
```  
  
##  <a name="operator_id2d1rendertarget_star"></a>  CRenderTarget::operator ID2D1RenderTarget *  
 반환 ID2D1RenderTarget 인터페이스  
  
```  
operator ID2D1RenderTarget*();
```   
  
### <a name="return-value"></a>반환 값  
 ID2D1RenderTarget 인터페이스 또는 개체가 아직 초기화 되지 않은 경우에 NULL 포인터입니다.  
  
##  <a name="popaxisalignedclip"></a>  CRenderTarget::PopAxisAlignedClip  
 마지막 축에 맞춰진 클립 렌더링 대상에서 제거합니다. 이 메서드가 호출 되 면 클립은 더 이상 다음 그리기 작업에 적용 됩니다.  
  
```  
void PopAxisAlignedClip();
```  
  
##  <a name="poplayer"></a>  CRenderTarget::PopLayer  
 마지막 PushLayer 변수로 지정 된 계층에 그리기 작업 리디렉션을 중지를 호출 합니다.  
  
```  
void PopLayer();
```  
  
##  <a name="pushaxisalignedclip"></a>  CRenderTarget::PushAxisAlignedClip  
 마지막 축에 맞춰진 클립 렌더링 대상에서 제거합니다. 이 메서드가 호출 되 면 클립은 더 이상 다음 그리기 작업에 적용 됩니다.  
  
```  
void PushAxisAlignedClip(
    const CD2DRectF& rectClip,  
    D2D1_ANTIALIAS_MODE mode = D2D1_ANTIALIAS_MODE_PER_PRIMITIVE);
```  
  
### <a name="parameters"></a>매개 변수  
 `rectClip`  
 크기와 장치 독립적 픽셀 단위로 클리핑 영역 위치입니다.  
  
 `mode`  
 장면 내용으로 클립을 혼합 하는 하위 픽셀 경계 클립 영역이의 가장자리를 그리는 데 사용 하는 앨리어싱 사용 안 함 모드입니다. 혼합 PopAxisAlignedClip 메서드를 호출 하 고 계층 내 각 기본 형식에 적용 되지 않습니다 때 수행 됩니다.  
  
##  <a name="pushlayer"></a>  CRenderTarget::PushLayer  
 PopLayer를 호출할 때까지 이후의 모든 그리기 작업을 받을 수 있도록 렌더링 대상으로 지정 된 계층을 추가 합니다.  
  
```  
void PushLayer(
    const D2D1_LAYER_PARAMETERS& layerParameters,  
    CD2DLayer& layer);
```  
  
### <a name="parameters"></a>매개 변수  
 `layerParameters`  
 콘텐츠 경계, 기하학적 마스크, 불투명도, 불투명 마스크 및 앤티 앨리어싱 계층의 옵션입니다.  
  
 `layer`  
 후속 그리기 작업을 수신 하는 계층입니다.  
  
##  <a name="restoredrawingstate"></a>  CRenderTarget::RestoreDrawingState  
 지정 된 ID2D1DrawingStateBlock의 렌더링 대상의 그리기 상태를 설정합니다.  
  
```  
void RestoreDrawingState(ID2D1DrawingStateBlock& drawingStateBlock);
```  
  
### <a name="parameters"></a>매개 변수  
 `drawingStateBlock`  
 렌더링 대상의 그리기 새 상태입니다.  
  
##  <a name="savedrawingstate"></a>  CRenderTarget::SaveDrawingState  
 지정 된 ID2D1DrawingStateBlock를 현재 그리기 상태를 저장합니다.  
  
```  
void SaveDrawingState(ID2D1DrawingStateBlock& drawingStateBlock) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 `drawingStateBlock`  
 이 메서드가 반환 될 때 렌더링 대상의 현재 그리기 상태를 포함 합니다. 이 매개 변수를 메서드에 전달 하기 전에 초기화 되어야 합니다.  
  
##  <a name="setantialiasmode"></a>  CRenderTarget::SetAntialiasMode  
 렌더링 대상의 앨리어싱 사용 안 함 모드를 설정합니다. 앤티 앨리어싱 모드 이후의 모든 그리기 작업, 텍스트 및 문자 모양 그리기 작업에 적용 됩니다.  
  
```  
void SetAntialiasMode(D2D1_ANTIALIAS_MODE antialiasMode);
```  
  
### <a name="parameters"></a>매개 변수  
 `antialiasMode`  
 앤티 앨리어싱 모드 향후 그리기 작업입니다.  
  
##  <a name="setdpi"></a>  CRenderTarget::SetDpi  
 렌더링 대상의 (DPI) 인치당 도트를 설정합니다.  
  
```  
void SetDpi(const CD2DSizeF& sizeDPI);
```  
  
### <a name="parameters"></a>매개 변수  
 `sizeDPI`  
 렌더링 대상의 가로/수직 Dpi를 지정 하는 0 보다 크거나 같은 값입니다.  
  
##  <a name="settags"></a>  CRenderTarget::SetTags  
 후속 그리기 작업에 대 한 레이블을 지정합니다.  
  
```  
void SetTags(
    D2D1_TAG tag1,  
    D2D1_TAG tag2);
```  
  
### <a name="parameters"></a>매개 변수  
 `tag1`  
 다음 그리기 작업에 적용 하도록 레이블을 합니다.  
  
 `tag2`  
 다음 그리기 작업에 적용 하도록 레이블을 합니다.  
  
##  <a name="settextantialiasmode"></a>  CRenderTarget::SetTextAntialiasMode  
 후속 텍스트와 문자 모양 그리기 작업에 사용할 앨리어싱 사용 안 함 모드를 지정 합니다.  
  
```  
void SetTextAntialiasMode(D2D1_TEXT_ANTIALIAS_MODE textAntialiasMode);
```  
  
### <a name="parameters"></a>매개 변수  
 `textAntialiasMode`  
 후속 텍스트와 문자 모양 그리기 작업에 사용할 앨리어싱 사용 안 함 모드입니다.  
  
##  <a name="settextrenderingparams"></a>  CRenderTarget::SetTextRenderingParams  
 모든 후속 텍스트와 문자 모양 그리기 작업에 적용할 텍스트 렌더링 옵션을 지정 합니다.  
  
```  
void SetTextRenderingParams(IDWriteRenderingParams* textRenderingParams = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 `textRenderingParams`  
 모든 후속 텍스트와 문자 모양 그리기 작업;에 적용할 텍스트 렌더링 옵션 NULL을 현재 텍스트 렌더링 옵션의 선택을 취소 합니다.  
  
##  <a name="settransform"></a>  CRenderTarget::SetTransform  
 기존 변환을 바꾸는 렌더링 대상으로 지정된 된 변환을 적용 합니다. 이후의 모든 그리기 작업은 변환 된 공간에서 발생 합니다.  
  
```  
void SetTransform(const D2D1_MATRIX_3X2_F* transform);  
void SetTransform(const D2D1_MATRIX_3X2_F& transform);
```  
  
### <a name="parameters"></a>매개 변수  
 `transform`  
 렌더링 대상에 적용할 변환입니다.  
  
##  <a name="verifyresource"></a>  CRenderTarget::VerifyResource  
 CD2DResource 개체 validity; 확인 존재 하지 않은 경우 해당 개체를 만듭니다.  
  
```  
BOOL VerifyResource(CD2DResource* pResource);
```  
  
### <a name="parameters"></a>매개 변수  
 `pResource`  
 CD2DResource 개체에 대 한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 TRUE는 유효한; 경우 개체 그렇지 않으면 FALSE입니다.  
  
## <a name="see-also"></a>참고 항목  
 [클래스](../../mfc/reference/mfc-classes.md)
