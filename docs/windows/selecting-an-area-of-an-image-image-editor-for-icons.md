---
title: '방법: 이미지 편집'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
- Image editor [C++], flipping and rotating images
- images [C++], flipping
- images [C++], rotating
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
- size [C++], images
- images [C++], cropping
- images [C++], extending
- Image editor [C++], cropping or extending images
- Image editor [C++], shrinking and stretching images
- images [C++], stretching
- images [C++], shrinking
- bitmaps [C++], shrinking
- bitmaps [C++], stretching
- Image editor [C++], editing images
- images [C++], editing
- images [C++], properties
- Image editor [C++], Properties window
- Properties window, image editor
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
ms.openlocfilehash: ecfd69594c05c210743e0c22c804a4713a8229ef
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509636"
---
# <a name="how-to-edit-an-image"></a>방법: 이미지 편집

선택 도구를 사용 하 여 잘라내기, 복사, 지우기, 크기 조정, 반전 또는 이동 하려는 이미지 영역을 정의할 수 있습니다. **사각형 선택** 도구를 사용 하 여 이미지의 사각형 영역을 정의 하 고 선택할 수 있습니다. 불규칙 한 **선택** 도구를 사용 하면 잘라내기, 복사 또는 기타 작업에 대해 선택 하려는 영역에 대 한 자유 곡선 윤곽선을 그릴 수 있습니다.

> [!NOTE]
> [이미지 편집기 도구 모음](./image-editor-for-icons.md) 에 있는 **사각형 선택** 및 **불규칙 한 선택** 도구를 참조 하거나 **이미지 편집기** 도구 모음의 각 단추와 관련 된 도구 설명을 봅니다.

선택 영역에서 사용자 지정 브러시를 만들 수도 있습니다. 자세한 내용은 [사용자 지정 브러시 만들기](./using-a-drawing-tool-image-editor-for-icons.md)를 참조 하세요.

## <a name="how-to"></a>방법

이미지를 편집 하려면 다음을 참조 하세요.

### <a name="to-select-an-image"></a>이미지를 선택 하려면

1. **이미지 편집기** 도구 모음을 사용 하거나 메뉴 **이미지**도구로 이동 하 여  >  **Tools** 원하는 선택 도구를 선택 합니다.

1. 선택 하려는 이미지 영역의 한 모퉁이로 삽입 지점을 이동 합니다. 이미지 위에 삽입 지점이 있을 때 십자 모양이 표시 됩니다.

1. 선택 하려는 영역의 반대쪽 모서리로 삽입 지점을 끕니다. 사각형은 선택할 픽셀을 보여 줍니다. 사각형의 사각형 내에 있는 모든 픽셀은 선택 영역에 포함 됩니다.

1. 마우스 단추를 놓습니다. 선택 영역 테두리는 선택한 영역을 둘러쌉니다.

#### <a name="to-select-an-entire-image"></a>전체 이미지를 선택 하려면

현재 선택 영역 외부에서 이미지를 선택 합니다. 선택 테두리가 포커스를 변경 하 고 다시 전체 이미지를 포함 합니다.

### <a name="to-edit-parts-of-an-image"></a>이미지의 일부를 편집 하려면

선택 영역이 전체 이미지 또는 단지 일부 인지 여부에 관계 없이 [선택 영역](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)에서 잘라내기, 복사, 지우기 및 이동 등의 표준 편집 작업을 수행할 수 있습니다. **이미지 편집기** 는 **windows 클립보드**를 사용 하기 때문에 **이미지 편집기** 와 windows 용 다른 응용 프로그램 간에 이미지를 전송할 수 있습니다.

뿐만 아니라 전체 이미지를 포함 하거나 일부만 포함 하 든 선택 항목의 크기를 조정할 수 있습니다.

#### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>현재 선택 영역을 잘라내어 클립보드로 이동 하려면

메뉴 잘라내기 **편집**으로 이동  >  **Cut**합니다.

#### <a name="to-copy-the-selection"></a>선택 영역을 복사 하려면

1. 포인터를 선택 영역 테두리 안에 배치 하거나 크기 조정 핸들을 제외한 모든 위치에 배치 합니다.

1. **Ctrl** 키를 누른 채 선택 영역을 새 위치로 끕니다. 원래 선택 영역은 변경 되지 않습니다.

1. 선택 영역을 현재 위치의 이미지에 복사 하려면 선택 커서 바깥쪽을 선택 합니다.

#### <a name="to-paste-the-clipboard-contents-into-an-image"></a>클립보드 내용을 이미지에 붙여넣으려면

1. 메뉴 **편집**  >  **붙여넣기**로 이동 합니다.

   선택 테두리로 둘러싸인 클립보드 내용이 창의 왼쪽 위 모퉁이에 표시 됩니다.

1. 선택 영역 테두리 안에 포인터를 놓고 이미지를 이미지의 원하는 위치로 끕니다.

1. 이미지를 새 위치에 고정 하려면 선택 테두리 외부를 선택 합니다.

#### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>클립보드로 이동 하지 않고 현재 선택 영역을 삭제 하려면

메뉴 **편집**  >  **삭제**로 이동 합니다.

   선택 영역의 원래 영역이 현재 배경색으로 채워집니다.

> [!NOTE]
> **리소스 뷰** 창에서 마우스 오른쪽 단추를 클릭 하 여 **잘라내기**, **복사**, **붙여넣기**및 **삭제** 명령에 액세스할 수 있습니다.

#### <a name="to-move-the-selection"></a>선택 영역을 이동 하려면

1. 포인터를 선택 영역 테두리 안에 배치 하거나 크기 조정 핸들을 제외한 모든 위치에 배치 합니다.

1. 선택 영역을 새 위치로 끕니다.

1. 이미지의 선택 영역을 새 위치에 고정 하려면 선택 영역 테두리 바깥쪽을 선택 합니다.

선택 항목을 사용 하 여 그리는 방법에 대 한 자세한 내용은 [사용자 지정 브러시 만들기](./using-a-drawing-tool-image-editor-for-icons.md)를 참조 하세요.

### <a name="to-flip-an-image"></a>이미지를 대칭 이동 하려면

이미지를 대칭 이동 하거나 회전 하 여 원래 이미지의 미러 이미지를 만들거나, 이미지를 뒤집어 두거나, 한 번에 오른쪽 90도로 이미지를 회전할 수 있습니다.

- 이미지를 가로로 대칭 이동 하려면 (미러 이미지) 메뉴 **이미지로**  >  **가로 대칭**이동으로 이동 합니다.

- 이미지를 상하로 대칭 이동 하려면 (대칭 이동) 메뉴 **이미지**  >  **상하 대칭**이동으로 이동 합니다.

- 90도 이미지를 회전 하려면 메뉴 **이미지**  >  **회전 90도**로 이동 합니다.

   > [!NOTE]
   > 이러한 명령에 [액셀러레이터 키 (바로 가기 키)](../windows/accelerator-keys-image-editor-for-icons.md) 를 사용 하거나 바로 가기 메뉴 ( **이미지 편집기**에서 이미지 외부 선택)에서 명령에 액세스할 수도 있습니다.

### <a name="to-resize-an-image"></a>이미지의 크기를 조정하려면

이미지의 크기를 조정 하는 동안 이미지 **편집기** 의 동작은 전체 이미지를 [선택](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) 했는지 아니면 일부를 선택 했는지에 따라 달라 집니다.

선택 영역에 이미지의 일부만 포함 되어 있는 경우 **이미지 편집기** 는 픽셀의 행 또는 열을 삭제 하 고 빈 영역을 현재 배경색으로 채워 선택을 축소 합니다. 또한 픽셀의 행 또는 열을 복제 하 여 선택 영역을 늘릴 수 있습니다.

선택 영역에 전체 이미지가 포함 되어 있으면 이미지 **편집기** 에서 이미지를 축소 하 고 확대 하거나 자르거나 확장 합니다.

이미지 크기를 조정 하는 데는 크기 조정 핸들과 [속성 창](/visualstudio/ide/reference/properties-window)의 두 가지 메커니즘이 있습니다. 크기 조정 핸들을 끌어 이미지의 전체 또는 일부의 크기를 변경 합니다. 끌 수 있는 크기 조정 핸들은 실선으로 표시 됩니다. 비어 있는 핸들은 끌 수 없습니다. **속성** 창을 사용 하 여 선택한 부분이 아니라 전체 이미지만 크기를 조정할 수 있습니다.

![비트맵의 핸들 크기 조정](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
크기 조정 핸들

> [!NOTE]
> [그리드 설정 대화 상자](./image-editor-for-icons.md)에서 **바둑판식 모눈** 옵션을 선택한 경우 크기 조정은 다음 타일 눈금선에 맞춰집니다. **픽셀 그리드** 옵션만 선택한 경우 (기본 설정) 크기 조정은 다음 사용 가능한 픽셀에 맞춰집니다.

#### <a name="to-resize-an-entire-image-using-the-properties-window"></a>속성 창을 사용 하 여 전체 이미지의 크기를 조정 하려면

1. 속성을 변경 하려는 이미지를 엽니다.

1. [속성 창](/visualstudio/ide/reference/properties-window)의 **너비** 및 **높이** 상자에 원하는 차원을 입력 합니다.

   이미지의 크기를 높이는 경우 이미지 **편집기** 는 이미지를 오른쪽, 아래쪽 또는 양쪽으로 확장 하 고 새 영역을 현재 배경색으로 채웁니다. 이미지가 늘어나지 않습니다.

   이미지 크기를 단축 하는 경우 **이미지 편집기** 는 오른쪽 가장자리나 아래쪽 가장자리 또는 둘 다에서 이미지를 잘라냅니다.

   > [!NOTE]
   > **너비** 및 **높이** 속성을 사용 하 여 일부 선택 영역의 크기를 조정 하지 않고 전체 이미지만 크기를 조정할 수 있습니다.

#### <a name="to-crop-or-extend-an-entire-image"></a>전체 이미지를 자르거나 확장 하려면

1. 전체 이미지를 선택 합니다.

   현재 이미지의 일부를 선택 하 고 전체 이미지를 선택 하려면 현재 선택 테두리 외부에 있는 이미지의 아무 곳 이나 선택 합니다.

1. 이미지가 올바른 크기가 될 때까지 크기 조정 핸들을 끕니다.

일반적으로 **이미지 편집기** 는 크기 조정 핸들을 이동 하 여 크기를 조정할 때 이미지를 자르거나 확대 합니다. **Shift** 키를 누른 상태에서 크기 조정 핸들을 이동 하면 **이미지 편집기** 가 이미지를 축소 하거나 확장 합니다.

#### <a name="to-shrink-or-stretch-an-entire-image"></a>전체 이미지를 축소 하거나 확장 하려면

1. 전체 이미지를 선택 합니다.

   현재 이미지의 일부를 선택 하 고 전체 이미지를 선택 하려면 현재 선택 테두리 외부에 있는 이미지의 아무 곳 이나 선택 합니다.

1. **Shift** 키를 누른 상태에서 이미지가 올바른 크기가 될 때까지 크기 조정 핸들을 끕니다.

#### <a name="to-shrink-or-stretch-part-of-an-image"></a>이미지의 일부를 축소 또는 스트레치 하려면

1. 크기를 조정 하려는 이미지의 파트를 선택 합니다. 자세한 내용은 [이미지 영역 선택](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)을 참조 하세요.

1. 크기 조정 핸들 중 하나를 선택 하는 것이 올바른 크기가 될 때까지 끕니다.

### <a name="to-edit-an-image-outside-of-a-project"></a>프로젝트 외부에서 이미지를 편집 하려면

모든 그래픽 응용 프로그램에서와 마찬가지로 개발 환경에서 이미지를 열고 편집할 수 있습니다. 예를 들어 독립 실행형 편집용 비트맵을 열 수 있습니다. 사용할 이미지는 Visual Studio 프로젝트에 포함 되지 않아도 됩니다.

1. 메뉴 **파일**  >  **열기**로 이동 합니다.

1. **파일 형식** 상자에서 **모든 파일**을 선택 합니다.

1. 편집 하려는 이미지를 찾아서 엽니다.

### <a name="to-change-image-properties"></a>이미지 속성을 변경 하려면

[속성 창](/visualstudio/ide/reference/properties-window)를 사용 하 여 이미지의 속성을 설정 하거나 수정할 수 있습니다.

1. **이미지 편집기**에서 이미지를 엽니다.

1. **속성** 창에서 이미지의 속성을 변경 하거나 모든 속성을 변경 합니다.

   |속성|설명|
   |--------------|-----------------|
   |**색**|이미지에 대 한 색 구성표를 지정 합니다. **단색**, **16**또는 **256**또는 **트루 색**을 선택 합니다.<br/><br/>16 색 색상표를 사용 하 여 이미지를 이미 그린 경우 **단색** 을 선택 하면 이미지의 색에 대해 검정과 흰색이 대체 됩니다. 대비는 항상 유지 되지 않습니다. 예를 들어 빨간색 및 녹색의 인접 영역은 모두 검정색으로 변환 됩니다.|
   |**Filename**|이미지 파일의 이름을 지정 합니다.<br/><br/>기본적으로 Visual Studio는 기본 리소스 식별자 (IDB_BITMAP1)에서 처음 4 개 문자 ("IDB_")를 제거 하 고 적절 한 확장을 추가 하 여 만든 기본 파일 이름을 할당 합니다. 이 예에서는 이미지의 파일 이름을 *BITMAP1.bmp*합니다. *MYBITMAP1.bmp*이름을 바꿀 수 있습니다.|
   |**높이**|이미지의 높이 (픽셀)를 설정 합니다. 기본값은 48입니다.<br/><br/>이미지를 자르거나 빈 공간이 기존 이미지 아래에 추가 됩니다.|
   |**ID**|리소스의 식별자를 설정 합니다.<br/><br/>이미지의 경우 기본적으로 Microsoft Visual Studio는 IDB_BITMAP1, IDB_BITMAP2 등의 시리즈에서 사용 가능한 다음 식별자를 할당 합니다. 아이콘 및 커서에도 비슷한 이름이 사용 됩니다.|
   |**색상표**|색 속성을 변경 합니다.<br/><br/>색을 두 번 클릭 하 여 선택 하 고 [사용자 지정 색 선택 대화 상자](./image-editor-for-icons.md)를 표시 합니다. 해당 하는 텍스트 상자에 RGB 또는 HSL 값을 입력 하 여 색을 정의 합니다.|
   |**SaveCompressed**|이미지가 압축 된 형식 인지 여부를 나타냅니다. 이 속성은 읽기 전용입니다.<br/><br/>Visual Studio에서는 이미지를 압축 된 형식으로 저장할 수 없으므로 Visual Studio에서 만든 모든 이미지에 대해이 속성은 **False**입니다. 다른 프로그램에서 만든 압축 된 이미지를 Visual Studio에서 여는 경우이 속성은 **True**가 됩니다. Visual Studio를 사용 하 여 압축 된 이미지를 저장 하면 압축 되지 않으며이 속성은 **False**로 다시 돌아갑니다.|
   |**Width**|이미지의 너비 (픽셀)를 설정 합니다. 비트맵의 기본값은 48입니다.<br/><br/>이미지를 자르거나 빈 공간이 기존 이미지의 오른쪽에 추가 됩니다.|

## <a name="requirements"></a>요구 사항

없음

## <a name="see-also"></a>참고 항목

[아이콘에 대 한 이미지 편집기](../windows/image-editor-for-icons.md)<br/>
[방법: 아이콘 또는 다른 이미지 만들기](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[방법: 그리기 도구 사용](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[방법: 색 작업](../windows/working-with-color-image-editor-for-icons.md)<br/>
[액셀러레이터 키](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
