---
description: '자세한 정보: CMFCImagePaintArea:: IMAGE_EDIT_MODE 열거형'
title: CMFCImagePaintArea::IMAGE_EDIT_MODE 열거형
ms.date: 11/04/2016
f1_keywords:
- IMAGE_EDIT_MODE Enumeration
helpviewer_keywords:
- IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
ms.openlocfilehash: f28880d108be8fb4f2b14ede1a3cbd3c7dac9f2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265326"
---
# <a name="cmfcimagepaintareaimage_edit_mode-enumeration"></a>CMFCImagePaintArea::IMAGE_EDIT_MODE 열거형

이미지 편집기 대화 상자에서 이미지를 수정 하는 데 사용 하는 그리기 모드를 지정 합니다.

## <a name="syntax"></a>구문

```
enum IMAGE_EDIT_MODE
{
    IMAGE_EDIT_MODE_PEN = 0,
    IMAGE_EDIT_MODE_FILL,
    IMAGE_EDIT_MODE_LINE,
    IMAGE_EDIT_MODE_RECT,
    IMAGE_EDIT_MODE_ELLIPSE,
    IMAGE_EDIT_MODE_COLOR
};
```

## <a name="members"></a>멤버

|Name|설명|
|-|-|
|IMAGE_EDIT_MODE_PEN|개별 픽셀을 그리는 데 사용 됩니다.|
|IMAGE_EDIT_MODE_FILL|현재 커서 위치에 있는 색을 포함 하는 모든 인접 영역을 채우는 데 사용 됩니다.|
|IMAGE_EDIT_MODE_LINE|선을 그리는 데 사용 됩니다.|
|IMAGE_EDIT_MODE_RECT|사각형을 그리는 데 사용 됩니다.|
|IMAGE_EDIT_MODE_ELLIPSE|타원을 그리는 데 사용 됩니다.|
|IMAGE_EDIT_MODE_COLOR|현재 커서 위치의 색으로 현재 색을 설정 하는 데 사용 됩니다.|

### <a name="remarks"></a>설명

`CMFCImagePaintArea`및 `CMFCImageEditorDialog` 클래스는이 열거형을 사용 하 여 현재 그리기 모드를 설정 합니다. 그리기 모드와 현재 색은 이미지 편집기 대화 상자에서 그림 영역을 수정 하는 데 사용 됩니다. 및에 대 한 자세한 내용은 `CMFCImagePaintArea` `CMFCImageEditorDialog` [Cmfcimagepaintarea 클래스](../../mfc/reference/cmfcimagepaintarea-class.md) 및 [cmfcimageeditordialog 클래스](../../mfc/reference/cmfcimageeditordialog-class.md)를 참조 하세요.

IMAGE_EDIT_MODE_COLOR 그리기 모드를 사용 하 여 이미지에서 색을 선택 하는 경우 프레임 워크는 현재 그리기 모드를 IMAGE_EDIT_MODE_PEN 설정 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** afximagepaintarea

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImagePaintArea 클래스](../../mfc/reference/cmfcimagepaintarea-class.md)<br/>
[CMFCImageEditorDialog 클래스](../../mfc/reference/cmfcimageeditordialog-class.md)
