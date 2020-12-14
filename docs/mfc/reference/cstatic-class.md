---
description: '자세히 알아보기: CStatic 클래스'
title: CStatic 클래스
ms.date: 11/04/2016
f1_keywords:
- CStatic
- AFXWIN/CStatic
- AFXWIN/CStatic::CStatic
- AFXWIN/CStatic::Create
- AFXWIN/CStatic::DrawItem
- AFXWIN/CStatic::GetBitmap
- AFXWIN/CStatic::GetCursor
- AFXWIN/CStatic::GetEnhMetaFile
- AFXWIN/CStatic::GetIcon
- AFXWIN/CStatic::SetBitmap
- AFXWIN/CStatic::SetCursor
- AFXWIN/CStatic::SetEnhMetaFile
- AFXWIN/CStatic::SetIcon
helpviewer_keywords:
- CStatic [MFC], CStatic
- CStatic [MFC], Create
- CStatic [MFC], DrawItem
- CStatic [MFC], GetBitmap
- CStatic [MFC], GetCursor
- CStatic [MFC], GetEnhMetaFile
- CStatic [MFC], GetIcon
- CStatic [MFC], SetBitmap
- CStatic [MFC], SetCursor
- CStatic [MFC], SetEnhMetaFile
- CStatic [MFC], SetIcon
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
ms.openlocfilehash: fa151382cc1342151e937662781a625739e82bd3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342662"
---
# <a name="cstatic-class"></a>CStatic 클래스

Windows 정적 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CStatic : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CStatic:: CStatic](#cstatic)|`CStatic` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CStatic:: Create](#create)|Windows 정적 컨트롤을 만들고이를 개체에 연결 `CStatic` 합니다.|
|[CStatic::D rawItem](#drawitem)|소유자가 그린 정적 컨트롤을 그리려면를 재정의 합니다.|
|[CStatic:: GetBitmap](#getbitmap)|[Setbitmap](#setbitmap)을 사용 하 여 이전에 설정한 비트맵의 핸들을 검색 합니다.|
|[CStatic:: GetCursor](#getcursor)|[Setcursor](#setcursor)를 사용 하 여 이전에 설정 된 커서 이미지의 핸들을 검색 합니다.|
|[CStatic:: GetEnhMetaFile](#getenhmetafile)|[SetEnhMetaFile](#setenhmetafile)를 사용 하 여 이전에 설정한 확장 메타 파일의 핸들을 검색 합니다.|
|[CStatic:: GetIcon](#geticon)|[Seticon](#seticon)으로 이전에 설정 된 아이콘의 핸들을 검색 합니다.|
|[CStatic:: SetBitmap](#setbitmap)|정적 컨트롤에 표시할 비트맵을 지정 합니다.|
|[CStatic:: SetCursor](#setcursor)|정적 컨트롤에 표시할 커서 이미지를 지정 합니다.|
|[CStatic:: SetEnhMetaFile](#setenhmetafile)|정적 컨트롤에 표시 되는 향상 된 메타 파일을 지정 합니다.|
|[CStatic:: SetIcon](#seticon)|정적 컨트롤에 표시 되는 아이콘을 지정 합니다.|

## <a name="remarks"></a>설명

정적 컨트롤은 텍스트 문자열, 상자, 사각형, 아이콘, 커서, 비트맵 또는 확장 메타 파일을 표시 합니다. 이 클래스를 사용 하 여 다른 컨트롤의 레이블을 지정할 수 있습니다. 정적 컨트롤은 일반적으로 입력을 사용 하지 않으며 출력을 제공 하지 않습니다. 그러나 SS_NOTIFY 스타일을 사용 하 여 만든 경우 마우스 클릭의 부모에 게 알릴 수 있습니다.

두 단계로 정적 컨트롤을 만듭니다. 먼저 생성자를 호출 하 여 개체를 생성 `CStatic` 한 다음 [create](#create) member 함수를 호출 하 여 정적 컨트롤을 만들고이를 개체에 연결 `CStatic` 합니다.

대화 상자 `CStatic` 내에서 개체를 만드는 경우 (대화 상자 리소스를 통해) `CStatic` 사용자가 대화 상자를 닫으면 개체가 자동으로 소멸 됩니다.

`CStatic`창 내에서 개체를 만드는 경우 해당 개체를 삭제 해야 할 수도 있습니다. `CStatic`창 내에서 스택에 만들어진 개체는 자동으로 삭제 됩니다. `CStatic`함수를 사용 하 여 힙에서 개체를 만드는 경우 **`new`** **`delete`** 개체에 대해를 호출 하 여 작업이 완료 되 면 개체를 삭제 해야 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cstaticcreate"></a><a name="create"></a> CStatic:: Create

Windows 정적 컨트롤을 만들고이를 개체에 연결 `CStatic` 합니다.

```
virtual BOOL Create(
    LPCTSTR lpszText,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID = 0xffff);
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
컨트롤에 놓을 텍스트를 지정 합니다. NULL 이면 텍스트가 표시 되지 않습니다.

*dwStyle*<br/>
정적 컨트롤의 창 스타일을 지정 합니다. 컨트롤에 [정적 컨트롤 스타일](../../mfc/reference/styles-used-by-mfc.md#static-styles) 의 조합을 적용 합니다.

*rect*<br/>
정적 컨트롤의 위치와 크기를 지정 합니다. 구조 또는 개체 중 하나일 수 있습니다 `RECT` `CRect` .

*pParentWnd*<br/>
`CStatic`부모 창 (일반적으로 개체)을 지정 합니다 `CDialog` . NULL이 아니어야 합니다.

*nID*<br/>
정적 컨트롤의 컨트롤 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CStatic`두 단계로 개체를 생성 합니다. 먼저 생성자 `CStatic` 를 호출한 다음을 호출 하 여 `Create` Windows 정적 컨트롤을 만들고이를 개체에 연결 `CStatic` 합니다.

정적 컨트롤에 다음 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles) 을 적용 합니다.

- 항상 WS_CHILD

- WS_VISIBLE 일반적으로

- WS_DISABLED 거의 없음

정적 컨트롤에서 비트맵, 커서, 아이콘 또는 메타 파일을 표시 하려면 다음 [정적 스타일](../../mfc/reference/styles-used-by-mfc.md#static-styles)중 하나를 적용 해야 합니다.

- 비트맵에이 스타일을 사용 SS_BITMAP 합니다.

- 커서 및 아이콘에이 스타일을 사용할 SS_ICON.

- 향상 된 메타 파일에이 스타일을 사용할 SS_ENHMETAFILE.

커서, 비트맵 또는 아이콘의 경우 다음 스타일을 사용할 수도 있습니다.

- 를 사용 하 여 정적 컨트롤의 이미지를 가운데에 맞춥니다. SS_CENTERIMAGE

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

## <a name="cstaticcstatic"></a><a name="cstatic"></a> CStatic:: CStatic

`CStatic` 개체를 생성합니다.

```
CStatic();
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

## <a name="cstaticdrawitem"></a><a name="drawitem"></a> CStatic::D rawItem

소유자가 그린 정적 컨트롤을 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>매개 변수

*lpDrawItemStruct*<br/>
[Drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) 구조체에 대 한 포인터입니다. 구조체에는 그릴 항목에 대 한 정보와 필요한 그리기 형식이 포함 되어 있습니다.

### <a name="remarks"></a>설명

소유자가 그린 개체에 대 한 그리기를 구현 하려면이 함수를 재정의 합니다 `CStatic` (컨트롤에 스타일 SS_OWNERDRAW 있음).

## <a name="cstaticgetbitmap"></a><a name="getbitmap"></a> CStatic:: GetBitmap

이전에 [Setbitmap](#setbitmap)을 사용 하 여 설정 된 비트맵의 핸들을 가져옵니다 `CStatic` .

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>반환 값

현재 비트맵에 대 한 핸들 이거나, 비트맵이 설정 되지 않은 경우 NULL입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticgetcursor"></a><a name="getcursor"></a> CStatic:: GetCursor

이전에 [Setcursor](#setcursor)를 사용 하 여 설정 된 커서의 핸들을 가져옵니다 `CStatic` .

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>반환 값

현재 커서에 대 한 핸들 이거나, 커서가 설정 되지 않은 경우 NULL입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticgetenhmetafile"></a><a name="getenhmetafile"></a> CStatic:: GetEnhMetaFile

에 연결 된, 이전에 [SetEnhMetafile](#setenhmetafile)를 사용 하 여 설정한 확장 메타 파일의 핸들을 가져옵니다 `CStatic` .

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>반환 값

현재 향상 된 메타 파일에 대 한 핸들 이거나, 확장 메타 파일이 설정 되지 않은 경우 NULL입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticgeticon"></a><a name="geticon"></a> CStatic:: GetIcon

이전에 [Seticon](#seticon)을 사용 하 여 설정 된 아이콘의 핸들을 가져옵니다 `CStatic` .

```
HICON GetIcon() const;
```

### <a name="return-value"></a>반환 값

현재 아이콘에 대 한 핸들 이거나, 아이콘이 설정 되지 않은 경우 NULL입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="cstaticsetbitmap"></a><a name="setbitmap"></a> CStatic:: SetBitmap

새 비트맵을 정적 컨트롤에 연결 합니다.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>매개 변수

*hBitmap*<br/>
정적 컨트롤에 그릴 비트맵의 핸들입니다.

### <a name="return-value"></a>반환 값

이전에 정적 컨트롤과 연결 된 비트맵의 핸들 이거나, 정적 컨트롤과 연결 된 비트맵이 없으면 NULL입니다.

### <a name="remarks"></a>설명

비트맵이 자동으로 정적 컨트롤에 그려집니다. 기본적으로 왼쪽 위 모퉁이에 그려지고 정적 컨트롤의 크기가 비트맵 크기에 맞게 조정 됩니다.

다음과 같은 다양 한 창과 정적 컨트롤 스타일을 사용할 수 있습니다.

- 비트맵에는이 스타일을 항상 사용 SS_BITMAP 합니다.

- 를 사용 하 여 정적 컨트롤의 이미지를 가운데에 맞춥니다. SS_CENTERIMAGE 이미지가 정적 컨트롤 보다 큰 경우에는 잘립니다. 정적 컨트롤 보다 작은 경우 이미지 주위의 빈 공간은 비트맵의 왼쪽 위 모퉁이에 있는 픽셀의 색으로 채워집니다.

- MFC는 `CBitmap` Win32 함수를 호출 하는 것이 아니라 비트맵 이미지를 사용 하 여 더 많은 작업을 수행 해야 하는 경우 사용할 수 있는 클래스를 제공 합니다 `LoadBitmap` . `CBitmap`한 종류의 GDI 개체를 포함 하는는 `CStatic` `CWnd` 그래픽 개체를 정적 컨트롤로 표시 하는 데 사용 되는 클래스인와 협력 하는 데 주로 사용 됩니다.

`CImage` 는 DIB (장치 독립적 비트맵)를 더 쉽게 사용할 수 있게 해 주는 ATL/MFC 클래스입니다. 자세한 내용은 [CImage 클래스](../../atl-mfc-shared/reference/cimage-class.md)를 참조 하세요.

- 일반적인 사용법은 `CStatic::SetBitmap` 또는 개체의 HBITMAP 연산자에 의해 반환 되는 GDI 개체를 제공 하는 것입니다 `CBitmap` `CImage` . 이 작업을 수행 하는 코드는 다음 줄과 유사 합니다.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```

다음 예에서는 힙에 두 개의 개체를 만듭니다 `CStatic` . 그런 다음를 사용 하 여 시스템 비트맵이 있는 하나를 로드 하 `CBitmap::LoadOEMBitmap` 고를 사용 하 여 파일에서 다른를 로드 `CImage::Load` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticsetcursor"></a><a name="setcursor"></a> CStatic:: SetCursor

새 커서 이미지를 정적 컨트롤과 연결 합니다.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>매개 변수

*hCursor*<br/>
정적 컨트롤에 그릴 커서의 핸들입니다.

### <a name="return-value"></a>반환 값

정적 컨트롤에 이전에 연결 된 커서의 핸들 이거나, 정적 컨트롤과 연결 된 커서가 없으면 NULL입니다.

### <a name="remarks"></a>설명

커서가 자동으로 정적 컨트롤에 그려집니다. 기본적으로 왼쪽 위 모퉁이에 그려지고 정적 컨트롤의 크기가 커서의 크기로 조정 됩니다.

다음을 포함 하 여 다양 한 창 및 정적 컨트롤 스타일을 사용할 수 있습니다.

- 커서 및 아이콘에는이 스타일을 항상 사용 SS_ICON 합니다.

- 정적 컨트롤에서 가운데 맞춤을 사용 SS_CENTERIMAGE 합니다. 이미지가 정적 컨트롤 보다 큰 경우에는 잘립니다. 정적 컨트롤 보다 작은 경우 이미지 주위의 빈 공간은 정적 컨트롤의 배경색으로 채워집니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticsetenhmetafile"></a><a name="setenhmetafile"></a> CStatic:: SetEnhMetaFile

새 확장 메타 파일 이미지를 정적 컨트롤과 연결 합니다.

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>매개 변수

*hMetaFile 파일*<br/>
정적 컨트롤에 그릴 향상 된 메타 파일의 핸들입니다.

### <a name="return-value"></a>반환 값

정적 컨트롤에 이전에 연결 된 확장 메타 파일의 핸들 이거나, 정적 컨트롤과 연결 된 확장 메타 파일이 없으면 NULL입니다.

### <a name="remarks"></a>설명

향상 된 메타 파일은 정적 컨트롤에 자동으로 그려집니다. 향상 된 메타 파일은 정적 컨트롤의 크기에 맞게 크기가 조정 됩니다.

다음을 포함 하 여 다양 한 창 및 정적 컨트롤 스타일을 사용할 수 있습니다.

- 확장 된 메타 파일에는이 스타일을 항상 사용 SS_ENHMETAFILE 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticseticon"></a><a name="seticon"></a> CStatic:: SetIcon

새 아이콘 이미지를 정적 컨트롤과 연결 합니다.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>매개 변수

*hIcon*<br/>
정적 컨트롤에 그릴 아이콘의 핸들입니다.

### <a name="return-value"></a>반환 값

정적 컨트롤에 이전에 연결 된 아이콘의 핸들 이거나, 정적 컨트롤과 연결 된 아이콘이 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

이 아이콘은 정적 컨트롤에 자동으로 그려집니다. 기본적으로 왼쪽 위 모퉁이에 그려지고 정적 컨트롤의 크기가 아이콘 크기로 조정 됩니다.

다음을 포함 하 여 다양 한 창 및 정적 컨트롤 스타일을 사용할 수 있습니다.

- 커서 및 아이콘에는이 스타일을 항상 사용 SS_ICON 합니다.

- 정적 컨트롤에서 가운데 맞춤을 사용 SS_CENTERIMAGE 합니다. 이미지가 정적 컨트롤 보다 큰 경우에는 잘립니다. 정적 컨트롤 보다 작은 경우 이미지 주위의 빈 공간은 정적 컨트롤의 배경색으로 채워집니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>참고 항목

[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[CButton 클래스](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 클래스](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit 클래스](../../mfc/reference/cedit-class.md)<br/>
[CListBox 클래스](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 클래스](../../mfc/reference/cscrollbar-class.md)<br/>
[CDialog 클래스](../../mfc/reference/cdialog-class.md)
