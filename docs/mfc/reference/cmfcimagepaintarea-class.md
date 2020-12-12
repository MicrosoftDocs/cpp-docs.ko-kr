---
description: '자세한 정보: CMFCImagePaintArea 클래스'
title: CMFCImagePaintArea 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::GetMode
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetBitmap
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetColor
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetMode
helpviewer_keywords:
- CMFCImagePaintArea [MFC], CMFCImagePaintArea
- CMFCImagePaintArea [MFC], GetMode
- CMFCImagePaintArea [MFC], SetBitmap
- CMFCImagePaintArea [MFC], SetColor
- CMFCImagePaintArea [MFC], SetMode
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
ms.openlocfilehash: c12a85c05686dcde24560b5ecc69cc68de07aa48
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265352"
---
# <a name="cmfcimagepaintarea-class"></a>CMFCImagePaintArea 클래스

이미지 편집기 대화 상자에서 이미지를 수정 하는 데 사용할 수 있는 그림 영역을 제공 합니다.

## <a name="syntax"></a>구문

```
class CMFCImagePaintArea : public CButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|-|-|
|[CMFCImagePaintArea:: CMFCImagePaintArea](#cmfcimagepaintarea)|`CMFCImagePaintArea` 개체를 생성합니다.|
|`CMFCImagePaintArea::~CMFCImagePaintArea`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|-|-|
|[CMFCImagePaintArea:: GetMode](#getmode)|현재 그리기 모드를 검색 합니다.|
|[CMFCImagePaintArea:: SetBitmap](#setbitmap)|그림 영역에 대 한 비트맵 이미지를 설정 합니다.|
|[CMFCImagePaintArea:: SetColor](#setcolor)|현재 그리기 색을 설정 합니다.|
|[CMFCImagePaintArea:: SetMode](#setmode)|현재 그리기 모드를 설정 합니다.|

### <a name="remarks"></a>설명

이 클래스는 사용자 코드에서 직접 사용할 수 없습니다.

프레임 워크는이 클래스를 사용 하 여 이미지 편집기 대화 상자에서 그림 영역을 표시 합니다. 이미지 편집기 대화 상자에 대 한 자세한 내용은 [Cmfcimageeditordialog 클래스](../../mfc/reference/cmfcimageeditordialog-class.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 클래스의 개체를 생성 하 고 `CMFCImagePaintArea` , 현재 그리기 색을 설정 하 고, 현재 그리기 모드를 설정 하 고, 그림 영역에 대 한 비트맵 이미지를 설정 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afximagepaintarea

## <a name="cmfcimagepaintareacmfcimagepaintarea"></a><a name="cmfcimagepaintarea"></a> CMFCImagePaintArea:: CMFCImagePaintArea

`CMFCImagePaintArea` 개체를 생성합니다.

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>매개 변수

*pParentDlg*\
진행 이미지 편집기의 부모인 대화 상자에 대 한 포인터입니다.

## <a name="cmfcimagepaintareagetmode"></a><a name="getmode"></a> CMFCImagePaintArea:: GetMode

현재 그리기 모드를 검색 합니다.

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>반환 값

현재 그리기 모드를 지정 하는 [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) 값입니다.

## <a name="cmfcimagepaintareasetbitmap"></a><a name="setbitmap"></a> CMFCImagePaintArea:: SetBitmap

그림 영역에 대 한 비트맵 이미지를 설정 합니다.

```cpp
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>매개 변수

*pBitmap*\
진행 표시할 새 비트맵 이미지입니다.

### <a name="remarks"></a>설명

*Pbitmap* 이 NULL 인 경우이 메서드는 수정 가능한 그리기 영역의 크기를 0으로 설정 합니다. 그렇지 않은 경우 수정 가능한 그리기 영역의 크기를 제공 된 비트맵 이미지의 크기로 설정 합니다.

## <a name="cmfcimagepaintareasetcolor"></a><a name="setcolor"></a> CMFCImagePaintArea:: SetColor

현재 그리기 색을 설정 합니다.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>매개 변수

*색*\
진행 새 그리기 색입니다.

### <a name="remarks"></a>설명

이미지 편집기 색상표 표시줄 또는 색 선택에서 색을 선택 하면 프레임 워크에서이 메서드를 호출 하 여 현재 그리기 색을 업데이트 합니다. 초기 그리기 색은 black (COLORREF 값 0)입니다.

그리기 색은 IMAGE_EDIT_MODE_COLOR를 제외 하 고 모든 그리기 모드에 대해 이미지 편집기 대화 상자에서 사용 됩니다. 그리기 모드에 대 한 자세한 내용은 [Cmfcimagepaintarea:: IMAGE_EDIT_MODE 열거형](cmfcimagepaintarea-image-edit-mode-enumeration.md)을 참조 하세요.

## <a name="cmfcimagepaintareasetmode"></a><a name="setmode"></a> CMFCImagePaintArea:: SetMode

현재 그리기 모드를 설정 합니다.

```cpp
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>매개 변수

*모드가*\
진행 현재 그리기 모드를 지정 하는 [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) 값입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog 클래스](../../mfc/reference/cmfcimageeditordialog-class.md)
