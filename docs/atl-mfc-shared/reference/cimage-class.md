---
description: '자세히 알아보기: CImage 클래스'
title: CImage 클래스
ms.date: 08/19/2019
f1_keywords:
- CImage
- ATLIMAGE/ATL::CImage
- ATLIMAGE/ATL::CImage::CImage
- ATLIMAGE/ATL::CImage::AlphaBlend
- ATLIMAGE/ATL::CImage::Attach
- ATLIMAGE/ATL::CImage::BitBlt
- ATLIMAGE/ATL::CImage::Create
- ATLIMAGE/ATL::CImage::CreateEx
- ATLIMAGE/ATL::CImage::Destroy
- ATLIMAGE/ATL::CImage::Detach
- ATLIMAGE/ATL::CImage::Draw
- ATLIMAGE/ATL::CImage::GetBits
- ATLIMAGE/ATL::CImage::GetBPP
- ATLIMAGE/ATL::CImage::GetColorTable
- ATLIMAGE/ATL::CImage::GetDC
- ATLIMAGE/ATL::CImage::GetExporterFilterString
- ATLIMAGE/ATL::CImage::GetHeight
- ATLIMAGE/ATL::CImage::GetImporterFilterString
- ATLIMAGE/ATL::CImage::GetMaxColorTableEntries
- ATLIMAGE/ATL::CImage::GetPitch
- ATLIMAGE/ATL::CImage::GetPixel
- ATLIMAGE/ATL::CImage::GetPixelAddress
- ATLIMAGE/ATL::CImage::GetTransparentColor
- ATLIMAGE/ATL::CImage::GetWidth
- ATLIMAGE/ATL::CImage::IsDIBSection
- ATLIMAGE/ATL::CImage::IsIndexed
- ATLIMAGE/ATL::CImage::IsNull
- ATLIMAGE/ATL::CImage::IsTransparencySupported
- ATLIMAGE/ATL::CImage::Load
- ATLIMAGE/ATL::CImage::LoadFromResource
- ATLIMAGE/ATL::CImage::MaskBlt
- ATLIMAGE/ATL::CImage::PlgBlt
- ATLIMAGE/ATL::CImage::ReleaseDC
- ATLIMAGE/ATL::CImage::ReleaseGDIPlus
- ATLIMAGE/ATL::CImage::Save
- ATLIMAGE/ATL::CImage::SetColorTable
- ATLIMAGE/ATL::CImage::SetPixel
- ATLIMAGE/ATL::CImage::SetPixelIndexed
- ATLIMAGE/ATL::CImage::SetPixelRGB
- ATLIMAGE/ATL::CImage::SetTransparentColor
- ATLIMAGE/ATL::CImage::StretchBlt
- ATLIMAGE/ATL::CImage::TransparentBlt
helpviewer_keywords:
- jpeg files
- bitmaps [C++], ATL and MFC support for
- images [C++], ATL and MFC support for
- gif files, ATL and MFC support
- .gif files, ATL and MFC support
- PNG files, ATL and MFC support
- CImage class
- transparent color
ms.assetid: 52861e3d-bf7e-481f-a240-90e88f76c490
ms.openlocfilehash: a094aecfae57a678f306d00e0998247000361822
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166828"
---
# <a name="cimage-class"></a>CImage 클래스

`CImage` JPEG, GIF, BMP 및 PNG (이동식 네트워크 그래픽) 형식으로 이미지를 로드 하 고 저장 하는 기능을 포함 하 여 향상 된 비트맵 지원 기능을 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CImage
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CImage:: CImage](#cimage)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CImage:: AlphaBlend](#alphablend)|투명 또는 반투명 픽셀의 비트맵이 표시 됩니다.|
|[CImage::Attach](#attach)|HBITMAP을 개체에 연결 `CImage` 합니다. 비 DIB 섹션 비트맵 또는 DIB 섹션 비트맵과 함께 사용할 수 있습니다.|
|[CImage::BitBlt](#bitblt)|소스 장치 컨텍스트에서이 현재 장치 컨텍스트로 비트맵을 복사 합니다.|
|[CImage::Create](#create)|DIB 섹션 비트맵을 만들어 이전에 생성 된 개체에 연결 `CImage` 합니다.|
|[CImage:: CreateEx](#createex)|추가 매개 변수를 사용 하 여 DIB 섹션 비트맵을 만들고 이전에 생성 된 개체에 연결 `CImage` 합니다.|
|[CImage::Destroy](#destroy)|개체에서 비트맵을 분리 `CImage` 하 고 비트맵을 소멸 시킵니다.|
|[CImage::D etach](#detach)|개체에서 비트맵을 분리 `CImage` 합니다.|
|[CImage: 원시:D](#draw)|소스 사각형의 비트맵을 대상 사각형에 복사 합니다. `Draw` 필요한 경우 대상 사각형의 크기에 맞게 비트맵을 늘이거나 압축 하 고 알파 혼합 및 투명 색을 처리 합니다.|
|[CImage::GetBits](#getbits)|비트맵의 실제 픽셀 값에 대 한 포인터를 검색 합니다.|
|[CImage::GetBPP](#getbpp)|픽셀당 비트 수를 검색 합니다.|
|[CImage::GetColorTable](#getcolortable)|색 테이블의 항목 범위에서 빨간색, 녹색, 파란색 (RGB) 색 값을 검색 합니다.|
|[CImage:: GetDC](#getdc)|현재 비트맵이 선택 된 장치 컨텍스트를 검색 합니다.|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|사용 가능한 이미지 형식과 해당 설명을 찾습니다.|
|[CImage:: Myfont.getheight](#getheight)|현재 이미지의 높이 (픽셀)를 검색 합니다.|
|[CImage:: GetImporterFilterString](#getimporterfilterstring)|사용 가능한 이미지 형식과 해당 설명을 찾습니다.|
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|색 테이블의 최대 항목 수를 검색 합니다.|
|[CImage:: GetPitch](#getpitch)|현재 이미지의 피치 (바이트)를 검색 합니다.|
|[CImage:: GetPixel](#getpixel)|*X* 및 *y* 로 지정 된 픽셀의 색을 검색 합니다.|
|[CImage::GetPixelAddress](#getpixeladdress)|지정 된 픽셀의 주소를 검색 합니다.|
|[CImage::GetTransparentColor](#gettransparentcolor)|색 테이블에서 투명 색의 위치를 검색 합니다.|
|[CImage::GetWidth](#getwidth)|현재 이미지의 너비 (픽셀)를 검색 합니다.|
|[CImage::IsDIBSection](#isdibsection)|연결 된 비트맵이 DIB 섹션 인지 여부를 확인 합니다.|
|[CImage::IsIndexed](#isindexed)|비트맵의 색이 인덱싱된 색상표에 매핑되는지 여부를 나타냅니다.|
|[CImage::IsNull](#isnull)|원본 비트맵이 현재 로드 되어 있는지 여부를 나타냅니다.|
|[CImage:: IsTransparencySupported](#istransparencysupported)|응용 프로그램이 투명 비트맵을 지원 하는지 여부를 나타냅니다.|
|[CImage::Load](#load)|지정 된 파일에서 이미지를 로드 합니다.|
|[CImage::LoadFromResource](#loadfromresource)|지정 된 리소스에서 이미지를 로드 합니다.|
|[CImage::MaskBlt](#maskblt)|지정 된 마스크와 래스터 연산을 사용 하 여 소스 및 대상 비트맵의 색 데이터를 결합 합니다.|
|[CImage::PlgBlt](#plgblt)|원본 장치 컨텍스트의 사각형에서 대상 장치 컨텍스트의 평행 사변형으로 비트 블록 전송을 수행 합니다.|
|[CImage::ReleaseDC](#releasedc)|[CImage:: GetDC](#getdc)를 사용 하 여 검색 된 장치 컨텍스트를 해제 합니다.|
|[CImage::ReleaseGDIPlus](#releasegdiplus)|GDI +에서 사용 하는 리소스를 해제 합니다. 전역 개체에 의해 생성 된 리소스를 해제 하려면를 호출 해야 합니다 `CImage` .|
|[CImage::Save](#save)|이미지를 지정 된 형식으로 저장 합니다. `Save` 이미지 옵션을 지정할 수 없습니다.|
|[CImage::SetColorTable](#setcolortable)|DIB 섹션의 색상표에 있는 항목 범위에서 빨간색, 녹색, 파랑 RGB 색 값을 설정 합니다.|
|[CImage::SetPixel](#setpixel)|지정 된 좌표의 픽셀을 지정 된 색으로 설정 합니다.|
|[CImage::SetPixelIndexed](#setpixelindexed)|지정 된 좌표의 픽셀을 색상표의 지정 된 인덱스에 있는 색으로 설정 합니다.|
|[CImage:: SetPixelRGB](#setpixelrgb)|지정 된 좌표의 픽셀을 지정 된 빨강, 녹색, 파랑 (RGB) 값으로 설정 합니다.|
|[CImage::SetTransparentColor](#settransparentcolor)|투명 하 게 처리할 색의 인덱스를 설정 합니다. 색상표에서 한 색만 투명 할 수 있습니다.|
|[CImage:: StretchBlt](#stretchblt)|소스 사각형의 비트맵을 대상 사각형으로 복사 하 고, 필요한 경우 대상 사각형의 크기에 맞게 비트맵을 늘이거나 압축 합니다.|
|[CImage::TransparentBlt](#transparentblt)|투명 색을 사용 하는 비트맵을 소스 장치 컨텍스트에서이 현재 장치 컨텍스트에 복사 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CImage:: operator HBITMAP](#operator_hbitmap)|개체에 연결 된 Windows 핸들을 반환 합니다 `CImage` .|

## <a name="remarks"></a>설명

`CImage` DIB (장치 독립적 비트맵) 섹션이 아닌 비트맵을 사용 합니다. 그러나 DIB 섹션 에서만 [Create](#create) 또는 [CImage:: Load](#load) 를 사용할 수 있습니다. Attach를 사용 하 여 비 DIB 섹션 비트맵을 개체에 연결할 수 `CImage` 있지만 [](#attach) `CImage` dib 섹션 비트맵만 지 원하는 다음 메서드를 사용할 수 없습니다.

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

연결 된 비트맵이 DIB 섹션 인지 확인 하려면 [IsDibSection](#isdibsection)를 호출 합니다.

> [!NOTE]
> Visual Studio .NET 2003에서이 클래스는 생성 된 개체 수의 수를 유지 `CImage` 합니다. 개수가 0이 될 때마다 함수가 `GdiplusShutdown` 자동으로 호출 되어 GDI +에서 사용 하는 리소스를 해제 합니다. 이렇게 하면 `CImage` dll에 의해 직접 또는 간접적으로 만들어진 모든 개체가 항상 제대로 소멸 되며 `GdiplusShutdown` 에서 호출 되지 않습니다 `DllMain` .

> [!NOTE]
> `CImage`DLL에는 전역 개체를 사용 하지 않는 것이 좋습니다. DLL에서 전역 개체를 사용 해야 하는 경우에는 `CImage` [CImage:: ReleaseGDIPlus](#releasegdiplus) 를 호출 하 여 gdi +에서 사용 하는 리소스를 명시적으로 해제 합니다.

`CImage` 새 [CDC](../../mfc/reference/cdc-class.md)로 선택할 수 없습니다. `CImage` 이미지에 대 한 자체 HDC를 만듭니다. HBITMAP는 한 번에 하나의 HDC로만 선택할 수 있기 때문에와 연결 된 HBITMAP를 `CImage` 다른 hdc로 선택할 수 없습니다. CDC가 필요한 경우에서 HDC를 검색 `CImage` 하 고 [cdc:: fromhandle](../../mfc/reference/cdc-class.md#fromhandle)에 제공 합니다.

## <a name="examples"></a>예제

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

MFC 프로젝트에서를 사용 하는 경우 `CImage` 프로젝트에서 [cbitmap](../../mfc/reference/cbitmap-class.md) 개체에 대 한 포인터를 필요로 하는 멤버 함수를 확인 합니다. `CImage` [CMenu:: appendmenu](../../mfc/reference/cmenu-class.md#appendmenu)와 같이 이러한 함수와 함께를 사용 하려는 경우 [Cbitmap:: fromhandle](../../mfc/reference/cbitmap-class.md#fromhandle)을 사용 하 여 HBITMAP에 전달 `CImage` 하 고 반환 된를 사용 합니다 `CBitmap*` .

```cpp
void CMyDlg::OnRButtonDown(UINT nFlags, CPoint point)
{
    UNREFERENCED_PARAMETER(nFlags);

    CBitmap* pBitmap = CBitmap::FromHandle(m_myImage);
    m_pmenuPop->AppendMenu(0, ID_BMPCOMMAND, pBitmap);
    ClientToScreen(&point);
    m_pmenuPop->TrackPopupMenu(TPM_RIGHTBUTTON | TPM_LEFTALIGN, point.x,
    point.y, this);
}
```

`CImage`를 통해 DIB 섹션의 실제 비트에 액세스할 수 있습니다. `CImage`이전에 WIN32 HBITMAP 또는 DIB 섹션을 사용한 모든 위치에서 개체를 사용할 수 있습니다.

는 `CImage` MFC 또는 ATL에서 사용할 수 있습니다.

> [!NOTE]
> 를 사용 하 여 프로젝트를 만드는 경우 `CImage` atlimage를 `CString` 포함 하기 전에 를 정의 해야 합니다. 프로젝트에서 MFC를 사용 하지 않고 ATL을 사용 하는 경우 *atlimage* 를 *포함 하기 전에* 프로젝트를 포함 합니다. 프로젝트에서 MFC를 사용 하는 경우 (또는 MFC를 지 원하는 ATL 프로젝트인 경우)에는 *atlimage* 를 포함 하기 전에 *afxstr* 를 포함 합니다.
>
> 마찬가지로 *atlimpl* 을 포함 하기 전에 *atlimage* 를 포함 해야 합니다. 이를 쉽게 수행 하려면 *atlimage* (Visual Studio 2017 및 이전 버전의 *stdafx.h* )에를 포함 *합니다.*

## <a name="requirements"></a>요구 사항

**헤더:** atlimage

## <a name="cimagealphablend"></a><a name="alphablend"></a> CImage:: AlphaBlend

투명 또는 반투명 픽셀의 비트맵이 표시 됩니다.

```
BOOL AlphaBlend(
    HDC hDestDC,
    int xDest,
    int yDest,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
    HDC hDestDC,
    const POINT& pointDest,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER);

BOOL AlphaBlend(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER);
```

### <a name="parameters"></a>매개 변수

*hDestDC*<br/>
대상 장치 컨텍스트에 대 한 핸들입니다.

*xDest*<br/>
대상 사각형의 왼쪽 위 모퉁이에 대 한 x 좌표 (논리 단위)입니다.

*yDest*<br/>
대상 사각형의 왼쪽 위 모퉁이에 대 한 y 좌표 (논리 단위)입니다.

*bSrcAlpha*<br/>
전체 소스 비트맵에 사용할 알파 투명도 값입니다. 기본 0xff (255)는 이미지가 불투명 하 고 픽셀 별 알파 값만 사용 하려는 것으로 가정 합니다.

*bBlendOp*<br/>
원본 및 대상 비트맵의 알파 혼합 함수, 전체 소스 비트맵에 적용 되는 전역 알파 값 및 원본 비트맵의 형식 정보입니다. 원본 및 대상 blend 함수는 현재 AC_SRC_OVER으로 제한 되어 있습니다.

*pointDest*<br/>
대상 사각형의 왼쪽 위 모퉁이를 식별 하는 [점](/windows/win32/api/windef/ns-windef-point) 구조 (논리 단위)에 대 한 참조입니다.

*nDestWidth*<br/>
대상 사각형의 너비 (논리 단위)입니다.

*nDestHeight*<br/>
대상 사각형의 높이 (논리 단위)입니다.

*xSrc*<br/>
소스 사각형의 왼쪽 위 모퉁이에 대 한 논리 x 좌표입니다.

*ySrc*<br/>
소스 사각형의 왼쪽 위 모퉁이에 대 한 논리 y 좌표입니다.

*nSrcWidth*<br/>
소스 사각형의 너비 (논리 단위)입니다.

*nSrcHeight*<br/>
소스 사각형의 높이 (논리 단위)입니다.

*rectDest*<br/>
대상을 식별 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*rectSrc*<br/>
소스를 식별 하는 구조체에 대 한 참조 `RECT` 입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

알파 혼합 비트맵은 픽셀 단위의 색 혼합을 지원 합니다.

*Bblendop* 가 기본값 AC_SRC_OVER로 설정 된 경우 원본 비트맵은 원본 픽셀의 알파 값을 기준으로 대상 비트맵 위에 배치 됩니다.

## <a name="cimageattach"></a><a name="attach"></a> CImage:: Attach

*HBitmap* 을 개체에 연결 `CImage` 합니다.

```cpp
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>매개 변수

*hBitmap*<br/>
HBITMAP에 대 한 핸들입니다.

*eOrientation*<br/>
비트맵의 방향을 지정 합니다. 다음 중 하나일 수 있습니다.

- 비트맵의 방향은 운영 체제에 의해 결정 DIBOR_DEFAULT.

- 비트맵의 줄이 역순으로 DIBOR_BOTTOMUP 합니다. 이렇게 하면 [cimage:: GetBits](#getbits) 에서 비트맵 버퍼 끝 근처에 포인터를 반환 하 고 [Cimage:: getpitch](#getpitch) 는 음수를 반환 합니다.

- 비트맵의 줄이 위쪽에서 아래쪽 순서로 DIBOR_TOPDOWN 합니다. 이렇게 하면 [cimage:: GetBits](#getbits) 가 비트맵 버퍼의 첫 번째 바이트에 대 한 포인터를 반환 하 고 [Cimage:: getpitch](#getpitch) 는 양수를 반환 합니다.

### <a name="remarks"></a>설명

비트맵은 비 DIB 섹션 비트맵 또는 DIB 섹션 비트맵 일 수 있습니다. DIB 섹션 비트맵과 함께 사용할 수 있는 메서드 목록은 [IsDIBSection](#isdibsection) 를 참조 하세요.

## <a name="cimagebitblt"></a><a name="bitblt"></a> CImage:: BitBlt

소스 장치 컨텍스트에서이 현재 장치 컨텍스트로 비트맵을 복사 합니다.

```
BOOL BitBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    const POINT& pointDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const POINT& pointSrc,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>매개 변수

*hDestDC*<br/>
대상 HDC입니다.

*xDest*<br/>
대상 사각형의 왼쪽 위 모퉁이에 대 한 논리 x 좌표입니다.

*yDest*<br/>
대상 사각형의 왼쪽 위 모퉁이에 대 한 논리 y 좌표입니다.

*dwROP*<br/>
수행할 래스터 작업입니다. 래스터 작업 코드는 소스, 대상 및 패턴 (현재 선택 된 브러시에서 정의 됨)을 결합 하 여 대상을 구성 하는 방법을 정확 하 게 정의 합니다. 다른 래스터 작업 코드와 해당 설명에 대 한 목록은 Windows SDK의 [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) 를 참조 하세요.

*pointDest*<br/>
대상 사각형의 왼쪽 위 모퉁이를 나타내는 [점](/windows/win32/api/windef/ns-windef-point) 구조입니다.

*nDestWidth*<br/>
대상 사각형의 너비 (논리 단위)입니다.

*nDestHeight*<br/>
대상 사각형의 높이 (논리 단위)입니다.

*xSrc*<br/>
소스 사각형의 왼쪽 위 모퉁이에 대 한 논리 x 좌표입니다.

*ySrc*<br/>
소스 사각형의 왼쪽 위 모퉁이에 대 한 논리 y 좌표입니다.

*rectDest*<br/>
대상 사각형을 나타내는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체입니다.

*pointSrc*<br/>
`POINT`소스 사각형의 왼쪽 위 모퉁이를 나타내는 구조체입니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK에서 [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) 을 참조 하세요.

## <a name="cimagecimage"></a><a name="cimage"></a> CImage:: CImage

`CImage` 개체를 생성합니다.

```
CImage() throw();
```

### <a name="remarks"></a>설명

개체를 생성 한 후 [Create](#create), [Load](#load), [LoadFromResource](#loadfromresource)또는 [attach](#attach) 를 호출 하 여 개체에 비트맵을 연결 합니다.

**참고** Visual Studio에서이 클래스는 생성 된 개체 수의 수를 유지 `CImage` 합니다. 개수가 0이 될 때마다 함수가 `GdiplusShutdown` 자동으로 호출 되어 GDI +에서 사용 하는 리소스를 해제 합니다. 이렇게 하면 `CImage` dll에 의해 직접 또는 간접적으로 만들어진 모든 개체가 항상 제대로 소멸 되며 `GdiplusShutdown` DllMain에서 호출 되지 않습니다.

`CImage`DLL에는 전역 개체를 사용 하지 않는 것이 좋습니다. DLL에서 전역 개체를 사용 해야 하는 경우에는 `CImage` [CImage:: ReleaseGDIPlus](#releasegdiplus) 를 호출 하 여 gdi +에서 사용 하는 리소스를 명시적으로 해제 합니다.

## <a name="cimagecreate"></a><a name="create"></a> CImage:: Create

비트맵을 만들어 `CImage` 이전에 생성 된 개체에 연결 `CImage` 합니다.

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>매개 변수

*nWidth*<br/>
비트맵의 너비 `CImage` (픽셀)입니다.

*nHeight*<br/>
비트맵의 높이 `CImage` (픽셀)입니다. *Nheight* 가 양수인 경우 비트맵이 상향식 DIB이 고 원점이 왼쪽 아래 모퉁이입니다. *Nheight* 가 음수 이면 비트맵은 하향식 DIB이 고 원점은 왼쪽 위 모퉁이입니다.

*nBPP*<br/>
비트맵의 픽셀 당 비트 수입니다. 일반적으로 4, 8, 16, 24 또는 32입니다. 단색 비트맵 또는 마스크의 경우 1 일 수 있습니다.

*dwFlags*<br/>
비트맵 개체에 알파 채널이 있는지 여부를 지정 합니다. 는 다음 값 중 0 개 이상의 조합일 수 있습니다.

- *createAlphaChannel* *NBPP* 가 32이 고 *eCompression* 가 BI_RGB 경우에만 사용할 수 있습니다. 지정 된 경우 생성 된 이미지는 각 픽셀에 대 한 알파 (투명도) 값이 각 픽셀의 네 번째 바이트 (알파 32 비트 이미지에서 사용 되지 않음)에 저장 됩니다. 이 알파 채널은 [CImage:: AlphaBlend](#alphablend)를 호출할 때 자동으로 사용 됩니다.

> [!NOTE]
> [CImage::D raw](#draw)호출에서 알파 채널이 있는 이미지는 자동으로 대상에 알파 혼합 됩니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

## <a name="cimagecreateex"></a><a name="createex"></a> CImage:: CreateEx

비트맵을 만들어 `CImage` 이전에 생성 된 개체에 연결 `CImage` 합니다.

```
BOOL CreateEx(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD eCompression,
    const DWORD* pdwBitmasks = NULL,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>매개 변수

*nWidth*<br/>
비트맵의 너비 `CImage` (픽셀)입니다.

*nHeight*<br/>
비트맵의 높이 `CImage` (픽셀)입니다. *Nheight* 가 양수인 경우 비트맵이 상향식 DIB이 고 원점이 왼쪽 아래 모퉁이입니다. *Nheight* 가 음수 이면 비트맵은 하향식 DIB이 고 원점은 왼쪽 위 모퉁이입니다.

*nBPP*<br/>
비트맵의 픽셀 당 비트 수입니다. 일반적으로 4, 8, 16, 24 또는 32입니다. 단색 비트맵 또는 마스크의 경우 1 일 수 있습니다.

*eCompression*<br/>
압축 된 상향식 비트맵의 압축 유형을 지정 합니다 (하향식 Dib는 압축할 수 없음). 다음 값 중 하나일 수 있습니다.

- 포맷이 압축 되지 BI_RGB 합니다. 를 호출할 때이 값 `CImage::CreateEx` 을 지정 하는 것은를 호출 하는 것과 같습니다 `CImage::Create` .

- 형식은 압축 되지 않으며, 색 테이블은 각 픽셀의 빨강, 녹색 및 파랑 구성 요소를 각각 지정 하는 세 가지 DWORD 색 마스크로 구성 됩니다. BI_BITFIELDS 16 비트 및 32-bpp 비트맵과 함께 사용 하는 경우 유효 합니다.

*pdwBitfields*<br/>
*ECompression* 가 BI_BITFIELDS로 설정 된 경우에만 사용 되 고, 그렇지 않으면 NULL 이어야 합니다. 각각 색의 빨강, 녹색 및 파랑 구성 요소에 사용 되는 각 픽셀의 비트를 지정 하는 3 개의 DWORD 비트 마스크 배열에 대 한 포인터입니다. 비트 필드에 대 한 제한 사항에 대 한 자세한 내용은 Windows SDK [BITMAPINFOHEADER](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader) 를 참조 하세요.

*dwFlags*<br/>
비트맵 개체에 알파 채널이 있는지 여부를 지정 합니다. 는 다음 값 중 0 개 이상의 조합일 수 있습니다.

- *createAlphaChannel* *NBPP* 가 32이 고 *eCompression* 가 BI_RGB 경우에만 사용할 수 있습니다. 지정 된 경우 생성 된 이미지는 각 픽셀에 대 한 알파 (투명도) 값이 각 픽셀의 네 번째 바이트 (알파 32 비트 이미지에서 사용 되지 않음)에 저장 됩니다. 이 알파 채널은 [CImage:: AlphaBlend](#alphablend)를 호출할 때 자동으로 사용 됩니다.

   > [!NOTE]
   > [CImage::D raw](#draw)호출에서 알파 채널이 있는 이미지는 자동으로 대상에 알파 혼합 됩니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="example"></a>예제

다음 예제에서는 16 비트를 사용 하 여 각 픽셀을 인코딩하여 100x100 픽셀 비트맵을 만듭니다. 지정 된 16 비트 픽셀에서 bits 0-3는 빨강 구성 요소를 인코딩하고, bits 4-7 인코드 녹색을 인코딩하고, bits 8-11를 인코딩합니다. 나머지 4 비트는 사용 되지 않습니다.

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

## <a name="cimagedestroy"></a><a name="destroy"></a> CImage::D estroy

개체에서 비트맵을 분리 `CImage` 하 고 비트맵을 소멸 시킵니다.

```cpp
void Destroy() throw();
```

## <a name="cimagedetach"></a><a name="detach"></a> CImage::D etach

개체에서 비트맵을 분리 `CImage` 합니다.

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>반환 값

분리 된 비트맵에 대 한 핸들 이거나, 비트맵이 연결 되지 않은 경우 NULL입니다.

## <a name="cimagedraw"></a><a name="draw"></a> CImage: 원시:D

소스 장치 컨텍스트에서 현재 장치 컨텍스트로 비트맵을 복사 합니다.

```
BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight) const throw();

BOOL Draw(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc) const throw();

BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest) const throw();

BOOL Draw(
    HDC hDestDC,
    const POINT& pointDest) const throw();

BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight) const throw();

BOOL Draw(
    HDC hDestDC,
    const RECT& rectDest) const throw();
```

### <a name="parameters"></a>매개 변수

*hDestDC*<br/>
대상 장치 컨텍스트에 대 한 핸들입니다.

*xDest*<br/>
대상 사각형의 왼쪽 위 모퉁이에 대 한 x 좌표 (논리 단위)입니다.

*yDest*<br/>
대상 사각형의 왼쪽 위 모퉁이에 대 한 y 좌표 (논리 단위)입니다.

*nDestWidth*<br/>
대상 사각형의 너비 (논리 단위)입니다.

*nDestHeight*<br/>
대상 사각형의 높이 (논리 단위)입니다.

*xSrc*<br/>
소스 사각형의 왼쪽 위 모퉁이에 대 한 x 좌표 (논리 단위)입니다.

*ySrc*<br/>
소스 사각형의 왼쪽 위 모퉁이에 대 한 y 좌표 (논리 단위)입니다.

*nSrcWidth*<br/>
소스 사각형의 너비 (논리 단위)입니다.

*nSrcHeight*<br/>
소스 사각형의 높이 (논리 단위)입니다.

*rectDest*<br/>
대상을 식별 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*rectSrc*<br/>
소스를 식별 하는 구조체에 대 한 참조 `RECT` 입니다.

*pointDest*<br/>
대상 사각형의 왼쪽 위 모퉁이를 식별 하는 [점](/windows/win32/api/windef/ns-windef-point) 구조 (논리 단위)에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`Draw` 이미지에 투명 한 색 또는 알파 채널이 포함 되어 있지 않으면 [StretchBlt](#stretchblt)와 동일한 작업을 수행 합니다. 이 경우는 `Draw` 필요에 따라 [TransparentBlt](#transparentblt) 또는 [AlphaBlend](#alphablend) 와 동일한 작업을 수행 합니다.

`Draw`소스 사각형을 지정 하지 않는 버전의 경우 전체 원본 이미지가 기본 이미지입니다. `Draw`대상 사각형의 크기를 지정 하지 않는 버전의 경우 원본 이미지의 크기가 기본값이 며 스트레치 또는 축소가 발생 하지 않습니다.

## <a name="cimagegetbits"></a><a name="getbits"></a> CImage:: GetBits

비트맵에서 지정 된 픽셀의 실제 비트 값에 대 한 포인터를 검색 합니다.

```cpp
void* GetBits() throw();
```

### <a name="return-value"></a>반환 값

비트맵 버퍼에 대 한 포인터입니다. 비트맵이 상향식 DIB 인 경우 포인터는 버퍼의 끝 부분을 가리킵니다. 비트맵이 하향식 DIB 인 경우 포인터는 버퍼의 첫 번째 바이트를 가리킵니다.

### <a name="remarks"></a>설명

[Getpitch](#getpitch)에서 반환 하는 값과 함께이 포인터를 사용 하 여 이미지에서 개별 픽셀을 찾고 변경할 수 있습니다.

> [!NOTE]
> 이 메서드는 DIB 섹션 비트맵만 지원 합니다. 따라서 개체의 픽셀 (예를 들어, `CImage` DIB 섹션의 픽셀)에 액세스 합니다. 반환 된 포인터는 위치의 픽셀 (0, 0)을 가리킵니다.

## <a name="cimagegetbpp"></a><a name="getbpp"></a> CImage:: GetBPP

픽셀 당 비트 값을 검색 합니다.

```
int GetBPP() const throw();
```

### <a name="return-value"></a>반환 값

픽셀당 비트 수입니다.

### <a name="remarks"></a>설명

이 값은 각 픽셀 및 비트맵의 최대 색 수를 정의 하는 비트 수를 결정 합니다.

픽셀당 비트 수는 일반적으로 1, 4, 8, 16, 24 또는 32입니다. `biBitCount`이 값에 대 한 자세한 내용은 Windows SDK의 [BITMAPINFOHEADER](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader) 멤버를 참조 하십시오.

## <a name="cimagegetcolortable"></a><a name="getcolortable"></a> CImage:: GetColorTable

DIB 섹션의 색상표에 있는 항목 범위에서 빨간색, 녹색, 파란색 (RGB) 색 값을 검색 합니다.

```cpp
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>매개 변수

*iFirstColor*<br/>
검색할 첫 번째 항목의 색 테이블 인덱스입니다.

*nColors*<br/>
검색할 색 테이블 항목의 수입니다.

*prgbColors*<br/>
색 테이블 항목을 검색할 [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) 구조체의 배열에 대 한 포인터입니다.

## <a name="cimagegetdc"></a><a name="getdc"></a> CImage:: GetDC

현재 선택 된 이미지가 있는 장치 컨텍스트를 검색 합니다.

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>반환 값

디바이스 컨텍스트에 대한 핸들입니다.

### <a name="remarks"></a>설명

에 대 한 각 호출에 `GetDC` 는 [releasedc](#releasedc)에 대 한 후속 호출이 있어야 합니다.

## <a name="cimagegetexporterfilterstring"></a><a name="getexporterfilterstring"></a> CImage:: GetExporterFilterString

이미지를 저장 하는 데 사용할 수 있는 이미지 형식을 찾습니다.

```
static HRESULT GetExporterFilterString(
    CSimpleString& strExporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultSave,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>매개 변수

*strExporters*<br/>
`CSimpleString` 개체에 대한 참조입니다. 참조 **주의** 에 대 한 자세한 내용은 합니다.

*aguidFileTypes*<br/>
문자열의 파일 형식 중 하나에 해당 하는 각 요소를 포함 하는 Guid의 배열입니다. 아래 *pszAllFilesDescription* 의 예제에서 *aguidFileTypes*[0]은 GUID_NULL 되며 나머지 배열 값은 현재 운영 체제에서 지 원하는 이미지 파일 형식입니다.

> [!NOTE]
> 상수에 대 한 전체 목록은 Windows SDK의 **이미지 파일 형식 상수** 를 참조 하십시오.

*pszAllFilesDescription*<br/>
이 매개 변수가 NULL이 아닌 경우 필터 문자열은 목록의 시작 부분에 하나의 추가 필터를 포함 합니다. 이 필터는 해당 설명에 대해 *pszAllFilesDescription* 의 현재 값을 포함 하 고, 목록의 다른 내보내기에서 지 원하는 확장명의 파일을 허용 합니다.

예를 들어:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
목록에서 제외할 파일 형식을 지정 하는 비트 플래그 집합입니다. 허용 되는 플래그는 다음과 같습니다.

- `excludeGIF` = 0x01은 GIF 파일을 제외 합니다.

- `excludeBMP` = 0x02 BMP (Windows 비트맵) 파일을 제외 합니다.

- `excludeEMF` = 0x04는 EMF (확장 메타 파일) 파일을 제외 합니다.

- `excludeWMF` = 0x08 WMF (Windows 메타 파일) 파일을 제외 합니다.

- `excludeJPEG` = 0x10은 JPEG 파일을 제외 합니다.

- `excludePNG` = 0x20은 PNG 파일을 제외 합니다.

- `excludeTIFF` = 0x40 TIFF 파일을 제외 합니다.

- `excludeIcon` = 0x80은 ICO (Windows 아이콘) 파일을 제외 합니다.

- `excludeOther` = 0x80000000 위에 나열 되지 않은 다른 모든 파일 형식을 제외 합니다.

- `excludeDefaultLoad` = 0 로드의 경우 모든 파일 형식이 기본적으로 포함 됩니다.

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` 저장 시 이러한 파일은 일반적으로 특별 한 요구 사항이 있으므로 기본적으로 제외 됩니다.

*chSeparator*<br/>
이미지 형식 사이에 사용 되는 구분 기호입니다. 참조 **주의** 에 대 한 자세한 내용은 합니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

결과 서식 문자열을 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) 개체에 전달 하 여 파일 다른 이름으로 저장 대화 상자에서 사용 가능한 이미지 형식의 파일 확장명을 노출할 수 있습니다.

*StrExporter* 매개 변수 형식은 다음과 같습니다.

파일 description0&#124;\* ext0&#124;filedescription1&#124;. \* ext1&#124; ... 파일 설명 *n*&#124;\* . ext *n*&#124;&#124;

여기서 ' &#124; '는로 지정 된 구분 문자입니다 `chSeparator` . 예를 들어:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

이 문자열을 MFC 개체에 전달 하는 경우 기본 구분 기호 ' &#124; '를 사용 합니다 `CFileDialog` . 일반 파일 저장 대화 상자에이 문자열을 전달 하는 경우 null 구분 기호 ' \ 0 '을 사용 합니다.

## <a name="cimagegetheight"></a><a name="getheight"></a> CImage:: Myfont.getheight

이미지의 높이 (픽셀)를 검색 합니다.

```
int GetHeight() const throw();
```

### <a name="return-value"></a>반환 값

이미지의 높이 (픽셀)입니다.

## <a name="cimagegetimporterfilterstring"></a><a name="getimporterfilterstring"></a> CImage:: GetImporterFilterString

이미지를 로드 하는 데 사용할 수 있는 이미지 형식을 찾습니다.

```
static HRESULT GetImporterFilterString(
    CSimpleString& strImporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultLoad,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>매개 변수

*strImporters*<br/>
`CSimpleString` 개체에 대한 참조입니다. 참조 **주의** 에 대 한 자세한 내용은 합니다.

*aguidFileTypes*<br/>
문자열의 파일 형식 중 하나에 해당 하는 각 요소를 포함 하는 Guid의 배열입니다. 아래 *pszAllFilesDescription* 의 예제에서 *aguidFileTypes*[0]은 나머지 배열 값을 사용 하 여 GUID_NULL 됩니다. 현재 운영 체제에서 지 원하는 이미지 파일 형식입니다.

> [!NOTE]
> 상수에 대 한 전체 목록은 Windows SDK의 **이미지 파일 형식 상수** 를 참조 하십시오.

*pszAllFilesDescription*<br/>
이 매개 변수가 NULL이 아닌 경우 필터 문자열은 목록의 시작 부분에 하나의 추가 필터를 포함 합니다. 이 필터는 해당 설명에 대해 *pszAllFilesDescription* 의 현재 값을 포함 하 고, 목록의 다른 내보내기에서 지 원하는 확장명의 파일을 허용 합니다.

예를 들어:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
목록에서 제외할 파일 형식을 지정 하는 비트 플래그 집합입니다. 허용 되는 플래그는 다음과 같습니다.

- `excludeGIF` = 0x01은 GIF 파일을 제외 합니다.

- `excludeBMP` = 0x02 BMP (Windows 비트맵) 파일을 제외 합니다.

- `excludeEMF` = 0x04는 EMF (확장 메타 파일) 파일을 제외 합니다.

- `excludeWMF` = 0x08 WMF (Windows 메타 파일) 파일을 제외 합니다.

- `excludeJPEG` = 0x10은 JPEG 파일을 제외 합니다.

- `excludePNG` = 0x20은 PNG 파일을 제외 합니다.

- `excludeTIFF` = 0x40 TIFF 파일을 제외 합니다.

- `excludeIcon` = 0x80은 ICO (Windows 아이콘) 파일을 제외 합니다.

- `excludeOther` = 0x80000000 위에 나열 되지 않은 다른 모든 파일 형식을 제외 합니다.

- `excludeDefaultLoad` = 0 로드의 경우 모든 파일 형식이 기본적으로 포함 됩니다.

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` 저장 시 이러한 파일은 일반적으로 특별 한 요구 사항이 있으므로 기본적으로 제외 됩니다.

*chSeparator*<br/>
이미지 형식 사이에 사용 되는 구분 기호입니다. 참조 **주의** 에 대 한 자세한 내용은 합니다.

### <a name="remarks"></a>설명

결과 서식 문자열을 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) 개체에 전달 하 여 **파일 열기** 대화 상자에서 사용 가능한 이미지 형식의 파일 확장명을 노출할 수 있습니다.

*StrImporter* 매개 변수 형식은 다음과 같습니다.

파일 description0&#124;\* ext0&#124;filedescription1&#124;. \* ext1&#124; ... 파일 설명 *n*&#124;\* . ext *n*&#124;&#124;

여기서 ' &#124; '는 *chseparator* 로 지정 된 구분 문자입니다. 예를 들어:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

이 문자열을 MFC 개체에 전달 하는 경우 기본 구분 기호 ' &#124; '를 사용 합니다 `CFileDialog` . 일반 **파일 열기** 대화 상자에이 문자열을 전달 하는 경우 null 구분 기호 ' \ 0 '을 사용 합니다.

## <a name="cimagegetmaxcolortableentries"></a><a name="getmaxcolortableentries"></a> CImage:: GetMaxColorTableEntries

색 테이블의 최대 항목 수를 검색 합니다.

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>반환 값

색 테이블의 항목 수입니다.

### <a name="remarks"></a>설명

이 메서드는 DIB 섹션 비트맵만 지원 합니다.

## <a name="cimagegetpitch"></a><a name="getpitch"></a> CImage:: GetPitch

이미지의 피치를 검색 합니다.

```
int GetPitch() const throw();
```

### <a name="return-value"></a>반환 값

이미지의 피치입니다. 반환 값이 음수 이면 비트맵이 상향식 DIB이 고 원점이 왼쪽 아래 모퉁이입니다. 반환 값이 양수인 경우 비트맵은 하향식 DIB이 고 원점은 왼쪽 위 모퉁이입니다.

### <a name="remarks"></a>설명

피치는 하나의 비트맵 줄의 시작을 나타내는 두 메모리 주소와 다음 비트맵 줄의 시작 부분을 나타내는 거리 (바이트)입니다. 피치는 바이트 단위로 측정 되기 때문에 이미지의 피치는 픽셀 형식을 결정 하는 데 도움이 됩니다. 피치에는 비트맵을 위해 예약 된 추가 메모리가 포함 될 수도 있습니다.

[GetBits](#getbits)와 함께 `GetPitch`을 사용하여 이미지의 개별 픽셀을 찾습니다.

> [!NOTE]
> 이 메서드는 DIB 섹션 비트맵만 지원 합니다.

## <a name="cimagegetpixel"></a><a name="getpixel"></a> CImage:: GetPixel

*X* 및 *y* 로 지정 된 위치에서 픽셀의 색을 검색 합니다.

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>매개 변수

*x*<br/>
픽셀의 x 좌표입니다.

*y*<br/>
픽셀의 y 좌표입니다.

### <a name="return-value"></a>반환 값

픽셀의 빨강, 녹색, 파랑 (RGB) 값입니다. 픽셀이 현재 클리핑 영역 외부에 있는 경우 반환 값은 CLR_INVALID입니다.

## <a name="cimagegetpixeladdress"></a><a name="getpixeladdress"></a> CImage:: GetPixelAddress

픽셀의 정확한 주소를 검색 합니다.

```cpp
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>매개 변수

*x*<br/>
픽셀의 x 좌표입니다.

*y*<br/>
픽셀의 y 좌표입니다.

### <a name="remarks"></a>설명

주소는 픽셀의 좌표, 비트맵의 피치 및 픽셀당 비트 수에 따라 결정 됩니다.

픽셀당 8 비트 미만의 형식에 대해이 메서드는 픽셀을 포함 하는 바이트의 주소를 반환 합니다. 예를 들어 이미지 형식에 픽셀당 4 비트가 있으면는 `GetPixelAddress` 바이트의 첫 번째 픽셀의 주소를 반환 하 고 바이트 당 2 픽셀에 대해 계산 해야 합니다.

> [!NOTE]
> 이 메서드는 DIB 섹션 비트맵만 지원 합니다.

## <a name="cimagegettransparentcolor"></a><a name="gettransparentcolor"></a> CImage:: GetTransparentColor

색상표에서 투명 한 색의 인덱싱된 위치를 검색 합니다.

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>반환 값

투명 한 색의 인덱스입니다.

## <a name="cimagegetwidth"></a><a name="getwidth"></a> CImage:: GetWidth

이미지의 너비 (픽셀)를 검색 합니다.

```
int GetWidth() const throw();
```

### <a name="return-value"></a>반환 값

비트맵의 너비 (픽셀)입니다.

## <a name="cimageisdibsection"></a><a name="isdibsection"></a> CImage:: IsDIBSection

연결 된 비트맵이 DIB 섹션 인지 여부를 확인 합니다.

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>반환 값

연결 된 비트맵이 DIB 섹션이 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

비트맵이 DIB 섹션이 아닌 경우에는 `CImage` dib 섹션 비트맵만 지 원하는 다음 메서드를 사용할 수 없습니다.

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

## <a name="cimageisindexed"></a><a name="isindexed"></a> CImage:: IsIndexed

비트맵의 픽셀이 색상표에 매핑되는지 여부를 확인 합니다.

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>반환 값

인덱싱된 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 비트맵이 8 비트 (256 색) 이하인 경우에만 TRUE를 반환 합니다.

> [!NOTE]
> 이 메서드는 DIB 섹션 비트맵만 지원 합니다.

## <a name="cimageisnull"></a><a name="isnull"></a> CImage:: IsNull

비트맵이 현재 로드 되어 있는지 여부를 확인 합니다.

```
bool IsNull() const throw();
```

### <a name="remarks"></a>설명

현재 비트맵이 로드 되어 있지 않으면이 메서드는 TRUE를 반환 합니다. 그렇지 않으면 FALSE입니다.

## <a name="cimageistransparencysupported"></a><a name="istransparencysupported"></a> CImage:: IsTransparencySupported

응용 프로그램이 투명 비트맵을 지원 하는지 여부를 나타냅니다.

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>반환 값

현재 플랫폼이 투명성을 지 원하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

반환 값이 0이 아니고 투명성이 지원 되는 경우 [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt)또는 [Draw](#draw) 를 호출 하면 투명 색이 처리 됩니다.

## <a name="cimageload"></a><a name="load"></a> CImage:: Load

이미지를 로드합니다.

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>매개 변수

*pszFileName*<br/>
로드할 이미지 파일의 이름을 포함 하는 문자열에 대 한 포인터입니다.

*pStream*<br/>
로드할 이미지 파일의 이름이 포함 된 스트림에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

*PszFileName* 또는 *pstream* 에 의해 지정 된 이미지를 로드 합니다.

유효한 이미지 형식은 BMP, GIF, JPEG, PNG 및 TIFF입니다.

## <a name="cimageloadfromresource"></a><a name="loadfromresource"></a> CImage:: LoadFromResource

비트맵 리소스에서 이미지를 로드 합니다.

```cpp
void LoadFromResource(
    HINSTANCE hInstance,
    LPCTSTR pszResourceName) throw();

void LoadFromResource(
    HINSTANCE hInstance,
    UINT nIDResource) throw();
```

### <a name="parameters"></a>매개 변수

*hInstance*<br/>
로드할 이미지를 포함 하는 모듈의 인스턴스에 대 한 핸들입니다.

*pszResourceName*<br/>
로드할 이미지를 포함 하는 리소스의 이름을 포함 하는 문자열에 대 한 포인터입니다.

*nIDResource*<br/>
로드할 리소스의 ID입니다.

### <a name="remarks"></a>설명

리소스는 비트맵 형식 이어야 합니다.

## <a name="cimagemaskblt"></a><a name="maskblt"></a> CImage:: MaskBlt

지정 된 마스크와 래스터 연산을 사용 하 여 소스 및 대상 비트맵의 색 데이터를 결합 합니다.

```
BOOL MaskBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    HBITMAP hbmMask,
    int xMask,
    int yMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const POINT& pointSrc,
    HBITMAP hbmMask,
    const POINT& pointMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    HBITMAP hbmMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    const POINT& pointDest,
    HBITMAP hbmMask,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>매개 변수

*hDestDC*<br/>
실행 파일이 리소스를 포함 하는 모듈에 대 한 핸들입니다.

*xDest*<br/>
대상 사각형의 왼쪽 위 모퉁이에 대 한 x 좌표 (논리 단위)입니다.

*yDest*<br/>
대상 사각형의 왼쪽 위 모퉁이에 대 한 y 좌표 (논리 단위)입니다.

*nDestWidth*<br/>
대상 사각형 및 원본 비트맵의 너비 (논리 단위)입니다.

*nDestHeight*<br/>
대상 사각형 및 원본 비트맵의 높이 (논리 단위)입니다.

*xSrc*<br/>
원본 비트맵의 왼쪽 위 모퉁이에 대 한 논리 x 좌표입니다.

*ySrc*<br/>
원본 비트맵의 왼쪽 위 모퉁이에 대 한 논리 y 좌표입니다.

*hbmMask*<br/>
원본 장치 컨텍스트의 색 비트맵과 결합 된 단색 마스크 비트맵에 대 한 핸들입니다.

*xMask*<br/>
*HbmMask* 매개 변수로 지정 된 마스크 비트맵의 가로 픽셀 오프셋입니다.

*yMask*<br/>
*HbmMask* 매개 변수로 지정 된 마스크 비트맵의 세로 픽셀 오프셋입니다.

*dwROP*<br/>
원본 및 대상 데이터의 조합을 제어 하기 위해 메서드에서 사용 하는 전경 및 배경 3 진 래스터 연산 코드를 모두 지정 합니다. 백그라운드 래스터 작업 코드는이 값의 상위 단어에 대 한 상위 바이트에 저장 됩니다. 전경 래스터 작업 코드는이 값의 상위 단어의 하위 바이트에 저장 됩니다. 이 값의 하위 단어는 무시 되 고 0 이어야 합니다. 이 메서드의 컨텍스트에서 전경 및 배경에 대 한 자세한 내용은 Windows SDK을 참조 `MaskBlt` 하세요. 일반적인 래스터 작업 코드 목록은 `BitBlt` Windows SDK에서을 참조 하세요.

*rectDest*<br/>
대상을 식별 하는 구조체에 대 한 참조 `RECT` 입니다.

*pointSrc*<br/>
`POINT`소스 사각형의 왼쪽 위 모퉁이를 나타내는 구조체입니다.

*pointMask*<br/>
`POINT`마스크 비트맵의 왼쪽 위 모퉁이를 나타내는 구조체입니다.

*pointDest*<br/>
`POINT`대상 사각형의 왼쪽 위 모퉁이 (논리 단위)를 식별 하는 구조체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 방법은 Windows NT 버전 4.0 이상에만 적용 됩니다.

## <a name="cimageoperator-hbitmap"></a><a name="operator_hbitmap"></a> CImage:: operator HBITMAP

이 연산자를 사용 하 여 개체의 연결 된 Windows GDI 핸들을 가져옵니다 `CImage` . 이 연산자는 HBITMAP 개체의 직접 사용을 지 원하는 캐스팅 연산자입니다.

## <a name="cimageplgblt"></a><a name="plgblt"></a> CImage::P lgBlt

원본 장치 컨텍스트의 사각형에서 대상 장치 컨텍스트의 평행 사변형으로 비트 블록 전송을 수행 합니다.

```
BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    HBITMAP hbmMask = NULL) const throw();

BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    HBITMAP hbmMask = NULL,
    int xMask = 0,
    int yMask = 0) const throw();

BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    const RECT& rectSrc,
    HBITMAP hbmMask = NULL,
    const POINT& pointMask = CPoint(0, 0)) const throw();
```

### <a name="parameters"></a>매개 변수

*hDestDC*<br/>
대상 장치 컨텍스트에 대 한 핸들입니다.

*pPoints*<br/>
논리적 공간에서 대상 평행 사변형의 3 모퉁이를 식별 하는 세 점의 배열에 대 한 포인터입니다. 소스 사각형의 왼쪽 위 모퉁이는이 배열의 첫 번째 요소, 오른쪽 위 모퉁이를이 배열의 두 번째 점, 왼쪽 아래 모퉁이를 세 번째 점으로 매핑합니다. 소스 사각형의 오른쪽 아래 모퉁이는 평행 사변형의 네 번째 점에 매핑됩니다.

*hbmMask*<br/>
소스 사각형의 색을 마스킹하는 데 사용 되는 선택적 단색 비트맵에 대 한 핸들입니다.

*xSrc*<br/>
소스 사각형의 왼쪽 위 모퉁이에 대 한 x 좌표 (논리 단위)입니다.

*ySrc*<br/>
소스 사각형의 왼쪽 위 모퉁이에 대 한 y 좌표 (논리 단위)입니다.

*nSrcWidth*<br/>
소스 사각형의 너비 (논리 단위)입니다.

*nSrcHeight*<br/>
소스 사각형의 높이 (논리 단위)입니다.

*xMask*<br/>
단색 비트맵의 왼쪽 위 모퉁이에 대 한 x 좌표입니다.

*yMask*<br/>
단색 비트맵의 왼쪽 위 모퉁이에 대 한 y-좌표입니다.

*rectSrc*<br/>
소스 사각형의 좌표를 지정 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*pointMask*<br/>
마스크 비트맵의 왼쪽 위 모퉁이를 나타내는 [점](/windows/win32/api/windef/ns-windef-point) 구조입니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*HbmMask* 가 유효한 단색 비트맵을 식별 하는 경우는 `PlgBit` 이 비트맵을 사용 하 여 소스 사각형에서 색 데이터의 비트를 마스킹 합니다.

이 방법은 Windows NT 버전 4.0 이상에만 적용 됩니다. 자세한 내용은 Windows SDK의 [PlgBlt](/windows/win32/api/wingdi/nf-wingdi-plgblt) 를 참조 하세요.

## <a name="cimagereleasedc"></a><a name="releasedc"></a> CImage:: ReleaseDC

장치 컨텍스트를 해제 합니다.

```cpp
void ReleaseDC() const throw();
```

### <a name="remarks"></a>설명

한 번에 하나의 비트맵만 장치 컨텍스트로 선택할 수 있기 때문에 `ReleaseDC` [GetDC](#getdc)에 대 한 각 호출에 대해를 호출 해야 합니다.

## <a name="cimagereleasegdiplus"></a><a name="releasegdiplus"></a> CImage:: ReleaseGDIPlus

GDI +에서 사용 하는 리소스를 해제 합니다.

```cpp
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>설명

전역 개체에 의해 할당 된 리소스를 해제 하려면이 메서드를 호출 해야 합니다 `CImage` . [Cimage:: cimage](#cimage)를 참조 하세요.

## <a name="cimagesave"></a><a name="save"></a> CImage:: Save

이미지를 디스크의 지정 된 스트림이나 파일에 저장 합니다.

```
HRESULT Save(
    IStream* pStream,
    REFGUID guidFileType) const throw();

HRESULT Save(
    LPCTSTR pszFileName,
    REFGUID guidFileType = GUID_NULL) const throw();
```

### <a name="parameters"></a>매개 변수

*pStream*<br/>
파일 이미지 데이터를 포함 하는 COM IStream 개체에 대 한 포인터입니다.

*pszFileName*<br/>
이미지의 파일 이름에 대 한 포인터입니다.

*guidFileType*<br/>
이미지를 저장할 파일 형식입니다. 다음 중 하나일 수 있습니다.

- `ImageFormatBMP` 압축 되지 않은 비트맵 이미지입니다.

- `ImageFormatPNG` PNG (이동식 네트워크 그래픽) 압축 이미지입니다.

- `ImageFormatJPEG` JPEG 압축 이미지입니다.

- `ImageFormatGIF` GIF 압축 이미지입니다.

> [!NOTE]
> 상수에 대 한 전체 목록은 Windows SDK의 **이미지 파일 형식 상수** 를 참조 하십시오.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

지정 된 이름 및 형식을 사용 하 여 이미지를 저장 하려면이 함수를 호출 합니다. *GuidFileType* 매개 변수가 포함 되지 않은 경우 파일 이름 파일 확장명이 이미지 형식을 결정 하는 데 사용 됩니다. 확장을 제공 하지 않으면 이미지가 BMP 형식으로 저장 됩니다.

## <a name="cimagesetcolortable"></a><a name="setcolortable"></a> CImage:: SetColorTable

DIB 섹션의 색상표에 있는 항목 범위에 대 한 빨강, 녹색, 파랑 (RGB) 색 값을 설정 합니다.

```cpp
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>매개 변수

*iFirstColor*<br/>
설정할 첫 번째 항목의 색 테이블 인덱스입니다.

*nColors*<br/>
설정할 색 테이블 항목의 수입니다.

*prgbColors*<br/>
색 테이블 항목을 설정 하는 [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) 구조체의 배열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는 DIB 섹션 비트맵만 지원 합니다.

## <a name="cimagesetpixel"></a><a name="setpixel"></a> CImage:: SetPixel

비트맵의 지정 된 위치에 있는 픽셀의 색을 설정 합니다.

```cpp
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>매개 변수

*x*<br/>
설정할 픽셀의 가로 위치입니다.

*y*<br/>
설정할 픽셀의 세로 위치입니다.

*color*<br/>
픽셀을 설정 하는 색입니다.

### <a name="remarks"></a>설명

픽셀 좌표가 선택한 클리핑 영역 외부에 있으면이 메서드는 실패 합니다.

## <a name="cimagesetpixelindexed"></a><a name="setpixelindexed"></a> CImage:: SetPixelIndexed

픽셀 색을 색상표의 *Iindex* 에 있는 색으로 설정 합니다.

```cpp
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>매개 변수

*x*<br/>
설정할 픽셀의 가로 위치입니다.

*y*<br/>
설정할 픽셀의 세로 위치입니다.

*iIndex*<br/>
색상표에 있는 색의 인덱스입니다.

## <a name="cimagesetpixelrgb"></a><a name="setpixelrgb"></a> CImage:: SetPixelRGB

*X* 및 *y* 로 지정 된 위치의 픽셀을 빨간색, 녹색, 파랑 (RGB) 이미지의 *r*, *g* 및 *b* 로 표시 되는 색으로 설정 합니다.

```cpp
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>매개 변수

*x*<br/>
설정할 픽셀의 가로 위치입니다.

*y*<br/>
설정할 픽셀의 세로 위치입니다.

*r*<br/>
빨간색의 농도입니다.

*g*<br/>
녹색 색의 농도입니다.

*b*<br/>
파란색의 농도입니다.

### <a name="remarks"></a>설명

빨강, 녹색 및 파랑 매개 변수는 각각 0에서 255 사이의 숫자로 표시 됩니다. 세 개의 매개 변수를 모두 0으로 설정 하면 전체 결과 색이 검정색이 됩니다. 세 매개 변수를 모두 255로 설정 하는 경우 결합 된 결과 색은 흰색입니다.

## <a name="cimagesettransparentcolor"></a><a name="settransparentcolor"></a> CImage:: SetTransparentColor

지정 된 인덱스 위치의 색을 투명 하 게 설정 합니다.

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>매개 변수

*iTransparentColor*<br/>
투명 하 게 설정할 색의 색인 (색상표)입니다. -1 인 경우 색이 투명으로 설정 되지 않습니다.

### <a name="return-value"></a>반환 값

이전에 투명 하 게 설정 된 색의 인덱스입니다.

## <a name="cimagestretchblt"></a><a name="stretchblt"></a> CImage:: StretchBlt

소스 장치 컨텍스트에서이 현재 장치 컨텍스트로 비트맵을 복사 합니다.

```
BOOL StretchBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    const RECT& rectDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>매개 변수

*hDestDC*<br/>
대상 장치 컨텍스트에 대 한 핸들입니다.

*xDest*<br/>
대상 사각형의 왼쪽 위 모퉁이에 대 한 x 좌표 (논리 단위)입니다.

*yDest*<br/>
대상 사각형의 왼쪽 위 모퉁이에 대 한 y 좌표 (논리 단위)입니다.

*nDestWidth*<br/>
대상 사각형의 너비 (논리 단위)입니다.

*nDestHeight*<br/>
대상 사각형의 높이 (논리 단위)입니다.

*dwROP*<br/>
수행할 래스터 작업입니다. 래스터 작업 코드는 소스, 대상 및 패턴 (현재 선택 된 브러시에서 정의 됨)을 결합 하 여 대상을 구성 하는 방법을 정확 하 게 정의 합니다. 다른 래스터 작업 코드와 해당 설명에 대 한 목록은 Windows SDK의 [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) 를 참조 하세요.

*rectDest*<br/>
대상을 식별 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*xSrc*<br/>
소스 사각형의 왼쪽 위 모퉁이에 대 한 x 좌표 (논리 단위)입니다.

*ySrc*<br/>
소스 사각형의 왼쪽 위 모퉁이에 대 한 y 좌표 (논리 단위)입니다.

*nSrcWidth*<br/>
소스 사각형의 너비 (논리 단위)입니다.

*nSrcHeight*<br/>
소스 사각형의 높이 (논리 단위)입니다.

*rectSrc*<br/>
소스를 식별 하는 구조체에 대 한 참조 `RECT` 입니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK에서 [StretchBlt](/windows/win32/api/wingdi/nf-wingdi-stretchblt) 을 참조 하세요.

## <a name="cimagetransparentblt"></a><a name="transparentblt"></a> CImage:: TransparentBlt

소스 장치 컨텍스트에서이 현재 장치 컨텍스트로 비트맵을 복사 합니다.

```
BOOL TransparentBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    const RECT& rectDest,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    UINT crTransparent = CLR_INVALID) const throw();
```

### <a name="parameters"></a>매개 변수

*hDestDC*<br/>
대상 장치 컨텍스트에 대 한 핸들입니다.

*xDest*<br/>
대상 사각형의 왼쪽 위 모퉁이에 대 한 x 좌표 (논리 단위)입니다.

*yDest*<br/>
대상 사각형의 왼쪽 위 모퉁이에 대 한 y 좌표 (논리 단위)입니다.

*nDestWidth*<br/>
대상 사각형의 너비 (논리 단위)입니다.

*nDestHeight*<br/>
대상 사각형의 높이 (논리 단위)입니다.

*crTransparent*<br/>
투명 하 게 처리할 소스 비트맵의 색입니다. 기본적으로 CLR_INVALID는 이미지의 투명 한 색으로 설정 된 색을 사용 해야 함을 나타냅니다.

*rectDest*<br/>
대상을 식별 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*xSrc*<br/>
소스 사각형의 왼쪽 위 모퉁이에 대 한 x 좌표 (논리 단위)입니다.

*ySrc*<br/>
소스 사각형의 왼쪽 위 모퉁이에 대 한 y 좌표 (논리 단위)입니다.

*nSrcWidth*<br/>
소스 사각형의 너비 (논리 단위)입니다.

*nSrcHeight*<br/>
소스 사각형의 높이 (논리 단위)입니다.

*rectSrc*<br/>
소스를 식별 하는 구조체에 대 한 참조 `RECT` 입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

`TransparentBlt` 는 픽셀당 4 비트 및 픽셀당 8 비트의 원본 비트맵에 대해 지원 됩니다. [CImage:: AlphaBlend](#alphablend) 를 사용 하 여 투명도가 있는 32 비트 픽셀의 비트맵을 지정 합니다.

### <a name="example"></a>예제

```cpp
// Performs a transparent blit from the source image to the destination
// image using the images' current transparency settings
BOOL TransparentBlt(CImage* pSrcImage, CImage* pDstImage,
       int xDest, int yDest, int nDestWidth, int nDestHeight)
{
    HDC hDstDC = NULL;
    BOOL bResult;

    if(pSrcImage == NULL || pDstImage == NULL)
    {
        // Invalid parameter
        return FALSE;
    }

    // Obtain a DC to the destination image
    hDstDC = pDstImage->GetDC();
    // Perform the blit
    bResult = pSrcImage->TransparentBlt(hDstDC, xDest, yDest, nDestWidth, nDestHeight);

    // Release the destination DC
    pDstImage->ReleaseDC();

    return bResult;
}
```

## <a name="see-also"></a>참고 항목

[MMXSwarm 샘플](../../overview/visual-cpp-samples.md)<br/>
[SimpleImage 샘플](../../overview/visual-cpp-samples.md)<br/>
[장치 독립적 비트맵](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[ATL COM 데스크톱 구성 요소](../../atl/atl-com-desktop-components.md)<br/>
[장치 독립적 비트맵](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
