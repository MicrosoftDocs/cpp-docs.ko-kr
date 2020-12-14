---
description: '자세히 알아보기: 회색 및 디더링된 비트맵 함수'
title: 회색 및 디더링된 비트맵 함수
ms.date: 11/19/2018
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
helpviewer_keywords:
- gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
ms.openlocfilehash: 20391f0ee7227827e1d9d6e18c2379be1fd43612
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219735"
---
# <a name="gray-and-dithered-bitmap-functions"></a>회색 및 디더링된 비트맵 함수

**회색 비트맵 함수**

MFC는 비트맵이 비활성화된 컨트롤의 모양을 갖도록 하기 위한 두 가지 함수를 제공합니다.

![회색 아이콘 버전 및 기존 아이콘 버전 비교](../../mfc/reference/media/vcgraybitmap.gif "회색 아이콘 버전 및 기존 아이콘 버전 비교")

|Name|설명|
|-|-|
|[AfxDrawGrayBitmap](#afxdrawgraybitmap)|비트맵의 회색 버전을 그립니다.|
|[AfxGetGrayBitmap](#afxgetgraybitmap)|비트맵의 회색 버전을 복사합니다.|

**디더링된 비트맵 함수**

MFC는 비트맵의 배경을 디더링된 패턴으로 바꾸기 위한 두 가지 함수도 제공합니다.

![디더링된 아이콘 버전 및 기존 아이콘 버전 비교](../../mfc/reference/media/vcditheredbitmap.gif "디더링된 아이콘 버전 및 기존 아이콘 버전 비교")

|Name|설명|
|-|-|
|[AfxDrawDitheredBitmap](#afxdrawditheredbitmap)|디더링된 배경을 사용하여 비트맵을 그립니다.|
|[AfxGetDitheredBitmap](#afxgetditheredbitmap)|디더링된 배경을 사용하여 비트맵을 복사합니다.|

## <a name="afxdrawgraybitmap"></a><a name="afxdrawgraybitmap"></a> AfxDrawGrayBitmap

비트맵의 회색 버전을 그립니다.

```cpp
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF crBackground);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
대상 DC를 가리킵니다.

*x*<br/>
대상 x 좌표입니다.

*y*<br/>
대상 y 좌표입니다.

*.Rsrc*<br/>
소스 비트맵입니다.

*crBackground*<br/>
새 배경색(일반적으로 회색, 예: COLOR_MENU)입니다.

### <a name="remarks"></a>설명

`AfxDrawGrayBitmap` 으로 그린 비트맵은 비활성화된 컨트롤의 모양을 갖습니다.

![회색 아이콘 버전 및 기존 아이콘 버전 비교](../../mfc/reference/media/vcgraybitmap.gif "회색 아이콘 버전 및 기존 아이콘 버전 비교")

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="afxgetgraybitmap"></a><a name="afxgetgraybitmap"></a> AfxGetGrayBitmap

비트맵의 회색 버전을 복사합니다.

```cpp
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF crBackground);
```

### <a name="parameters"></a>매개 변수

*.Rsrc*<br/>
소스 비트맵입니다.

*pDest*<br/>
대상 비트맵입니다.

*crBackground*<br/>
새 배경색(일반적으로 회색, 예: COLOR_MENU)입니다.

### <a name="remarks"></a>설명

`AfxGetGrayBitmap` 로 복사한 비트맵은 비활성화된 컨트롤의 모양을 갖습니다.

![회색 아이콘 버전 및 기존 아이콘 버전 비교](../../mfc/reference/media/vcgraybitmap.gif "회색 아이콘 버전 및 기존 아이콘 버전 비교")

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="afxdrawditheredbitmap"></a><a name="afxdrawditheredbitmap"></a> AfxDrawDitheredBitmap

비트맵을 그린 후 해당 배경을 디더링된 (검사기) 패턴으로 바꿉니다.

```cpp
void AFXAPI AfxDrawDitheredBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
대상 DC를 가리킵니다.

*x*<br/>
대상 x 좌표입니다.

*y*<br/>
대상 y 좌표입니다.

*.Rsrc*<br/>
소스 비트맵입니다.

*cr1*<br/>
일반적으로 흰색 두 가지 디더링 색 중 하나입니다.

*cr2*<br/>
다른 디더링 색 (보통 연한 회색 (COLOR_MENU))입니다.

### <a name="remarks"></a>설명

원본 비트맵이 비트맵 배경을 대체 하는 2 색 (*cr1* 및 *cr2*) 바둑판 패턴을 사용 하 여 대상 DC에 그려집니다. 소스 비트맵의 배경은 흰색 픽셀로 정의 되 고 모든 픽셀은 비트맵의 왼쪽 위 모퉁이에 있는 픽셀의 색과 일치 합니다.

![디더링된 아이콘 버전 및 기존 아이콘 버전 비교](../../mfc/reference/media/vcditheredbitmap.gif "디더링된 아이콘 버전 및 기존 아이콘 버전 비교")

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="afxgetditheredbitmap"></a><a name="afxgetditheredbitmap"></a> AfxGetDitheredBitmap

비트맵을 복사 하 여 배경을 디더링된 (검사기) 패턴으로 바꿉니다.

```cpp
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>매개 변수

*.Rsrc*<br/>
소스 비트맵입니다.

*pDest*<br/>
대상 비트맵입니다.

*cr1*<br/>
일반적으로 흰색 두 가지 디더링 색 중 하나입니다.

*cr2*<br/>
다른 디더링 색 (보통 연한 회색 (COLOR_MENU))입니다.

### <a name="remarks"></a>설명

원본 비트맵의 배경을 바꾸는 두 색 (*cr1* 및 *cr2*) 바둑판 패턴을 사용 하 여 원본 비트맵을 대상 비트맵에 복사 합니다. 소스 비트맵의 배경은 흰색 픽셀로 정의 되 고 모든 픽셀은 비트맵의 왼쪽 위 모퉁이에 있는 픽셀의 색과 일치 합니다.

![디더링된 아이콘 버전 및 기존 아이콘 버전 비교](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
