---
description: '자세한 정보: CMFCImageEditorDialog 클래스'
title: CMFCImageEditorDialog 클래스
ms.date: 11/19/2018
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
ms.openlocfilehash: 6c25cf4a1a8d0cc5852049a06c3a140cbb00a118
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265391"
---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog 클래스

`CMFCImageEditorDialog`클래스는 이미지 편집기 대화 상자를 지원 합니다.

## <a name="syntax"></a>구문

```
class CMFCImageEditorDialog : public CDialogEx
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCImageEditorDialog:: CMFCImageEditorDialog](#cmfcimageeditordialog)|`CMFCImageEditorDialog` 개체를 생성합니다.|

## <a name="remarks"></a>설명

`CMFCImageEditorDialog`클래스는 다음을 포함 하는 대화 상자를 제공 합니다.

- 이미지의 개별 픽셀을 수정 하는 데 사용 하는 그림 영역입니다.

- 그림 영역에서 픽셀을 수정 하는 그리기 도구입니다.

- 그리기 도구에서 사용 하는 색을 지정 하는 색상표입니다.

- 편집의 효과를 표시 하는 미리 보기 영역입니다.

다음 그림에서는 이미지 편집기 대화 상자를 보여 줍니다.

![CMFCImageEditorDialog 대화 상자](../../mfc/reference/media/imageedit.png "CMFCImageEditorDialog 대화 상자")

개체를 사용 하는 한 가지 방법은 `CMFCImageEditorDialog` 편집할 이미지를 전달 하는 것입니다 `CBitmap` . 이미지 편집 영역의 크기가 제한 되어 있고 논리적 픽셀 크기가 영역에 맞게 조정 되어 있으므로 큰 이미지를 만들지 마세요. 메서드를 호출 `DoModal` 하 여 모달 대화 상자를 시작 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afximageeditordialog

## <a name="cmfcimageeditordialogcmfcimageeditordialog"></a><a name="cmfcimageeditordialog"></a> CMFCImageEditorDialog:: CMFCImageEditorDialog

`CMFCImageEditorDialog` 개체를 생성합니다.

```
CMFCImageEditorDialog(
    CBitmap* pBitmap,
    CWnd* pParent=NULL,
    int nBitsPixel=-1);
```

### <a name="parameters"></a>매개 변수

*pBitmap*<br/>
이미지에 대 한 포인터입니다.

*pParent*<br/>
현재 이미지 편집기 대화 상자의 부모 창에 대 한 포인터입니다.

*nBitsPixel*<br/>
색 농도가 라고도 하는 단일 픽셀의 색을 나타내는 데 사용 되는 비트 수입니다.  *NBitsPixel* 매개 변수가-1 이면 *pbitmap* 매개 변수로 지정 된 이미지에서 색 농도가 파생 됩니다. 기본값은 -1입니다.

### <a name="return-value"></a>반환 값

이미지를 수정 하려면 이미지 포인터를 생성자에 게 전달 `CMFCImageEditorDialog` 합니다. 그런 다음 메서드를 호출 `DoModal` 하 여 모달 대화 상자를 엽니다. `DoModal`메서드가 반환 될 때 비트맵에는 새 이미지가 포함 됩니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

다음 예제에서는 클래스의 개체를 생성 하는 방법을 보여 줍니다 `CMFCImageEditorDialog` . 이 예제는 [새 컨트롤 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)
