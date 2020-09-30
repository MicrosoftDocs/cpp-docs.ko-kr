---
title: '방법: 아이콘 또는 다른 이미지 만들기'
ms.date: 02/15/2019
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resources [C++], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
- cursors [C++], creating
- image resources [C++], display devices
- icons [C++], creating
- cursors [C++], types
- icons [C++]
- Image editor [C++], icons and cursors
- cursors [C++]
- display devices [C++], creating icons for
- cursors [C++], hot spots
- icons [C++], types
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
- New Device Image command
- display devices [C++], adding images
- cursors [C++], adding
- icons, adding
- display devices [C++], copying images
- cursors [C++], copying
- icons, copying
- cursors [C++], deleting
- display devices [C++], deleting device image
- icons, erasing
- icons, deleting
- cursors [C++], undoing changes
- icons, undoing changes
- cursors [C++], screen regions
- inverse colors [C++], device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices [C++], transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects [C++], transparent images
- icons [C++], screen regions
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
- cursors [C++], hot spots
- hot spots
- .gif files [C++], saving bitmaps as
- jpg files [C++], saving bitmaps as
- jpeg files [C++], saving bitmaps as
- .jpg files [C++], saving bitmaps as
- Image editor [C++], converting image formats
- gif files [C++], saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files [C++], saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
- images [C++], stand-alone editing
- Image editor [C++], converting image formats
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
ms.openlocfilehash: bbaa008d8dac74588fc15bfebbc7cb2611260349
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504563"
---
# <a name="how-to-create-an-icon-or-other-image"></a>방법: 아이콘 또는 다른 이미지 만들기

새 이미지, 비트맵, 아이콘, 커서 또는 도구 모음을 만든 다음 **이미지 편집기** 를 사용 하 여 모양을 사용자 지정할 수 있습니다. [리소스 템플릿](./how-to-create-a-resource-script-file.md)뒤에 새 비트맵 패턴을 만들 수도 있습니다.

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>아이콘과 커서: 디스플레이 장치용 이미지 리소스

아이콘 및 커서는 다양한 유형의 디스플레이 디바이스에 맞는 다양한 크기 및 색 구성표의 여러 이미지를 포함할 수 있는 그래픽 리소스입니다. 커서에는 Windows에서 해당 위치를 추적 하는 데 사용 하는 위치인 핫 스폿이 있습니다. 비트맵 및 기타 이미지와 마찬가지로 아이콘과 커서는 모두 **이미지 편집기**를 사용 하 여 생성 및 편집 됩니다.

새 아이콘 또는 커서를 만들 때 **이미지 편집기** 는 먼저 표준 형식의 이미지를 만듭니다. 이미지는 처음에 투명한 화면 색상으로 채워집니다. 이미지가 커서 인 경우 핫 스폿은 좌표가 있는 왼쪽 위 모퉁이입니다 `0,0` .

기본적으로 **이미지 편집기** 는 다음 표에 표시 된 장치에 대 한 추가 이미지 만들기를 지원 합니다. **사용자 지정 이미지** 대화 상자에 너비, 높이 및 색상 수 매개 변수를 입력 하 여 다른 장치용 이미지를 만들 수 있습니다.

|색|너비(픽셀)|높이(픽셀)|
|-----------|----------------------|-----------------------|
|단색|16|16|
|단색|32|32|
|단색|48|48|
|단색|64|64|
|단색|96|96|
|16|16|16|
|16|32|32|
|16|64|64|
|16|48|48|
|16|96|96|
|256|16|16|
|256|32|32|
|256|48|48|
|256|64|64|
|256|96|96|

### <a name="create-a-device-image-icon-or-cursor"></a>장치 이미지 만들기 (아이콘 또는 커서)

새 아이콘 또는 커서 리소스를 만들 때 **이미지 편집기** 는 먼저 특정 스타일 (32 × 32, 아이콘의 경우 16 색, 아이콘의 경우 16 색, 32 × 32의 경우 단색)으로 이미지를 만듭니다. 그런 다음 다른 크기와 스타일의 이미지를 초기 아이콘이 나 커서에 추가 하 고 필요에 따라 다양 한 디스플레이 장치에 대 한 각 추가 이미지를 편집할 수 있습니다. 기존 이미지 형식 또는 그래픽 프로그램에서 만든 비트맵에서 잘라내기 및 붙여넣기 작업을 사용 하 여 이미지를 편집할 수도 있습니다.

[이미지 편집기](../windows/image-editor-for-icons.md)에서 아이콘이 나 커서 리소스를 열면 현재 디스플레이 장치에 가장 가깝게 일치 하는 이미지가 기본적으로 열립니다.

> [!NOTE]
> 프로젝트에 .rc 파일이 아직 없는 경우 [새 리소스 스크립트 파일 만들기](../windows/how-to-create-a-resource-script-file.md)를 참조 하세요.

**새 &lt; 장치 &gt; 이미지 유형** 대화 상자를 사용 하 여 지정 된 유형의 새 장치 이미지를 만들 수 있습니다. **새 \<Device> 이미지** 대화 상자를 열려면 메뉴 **이미지**  >  **새 이미지 형식**으로 이동 합니다. 여기에 포함 된 속성은 **대상 이미지 형식** 및 **사용자 지정**입니다.

**대상 이미지 유형** 속성은 열려는 이미지 유형을 선택 하는 사용 가능한 이미지 유형을 나열 합니다.

:::row:::
   :::column span="":::
      16 x 16, 16 색 \
      32 x 32, 16 색 \
      48 x 48, 16 색 \
      64 x 64, 16 색 \
      96 x 96, 16 색
   :::column-end:::
   :::column span="":::
      16 x 16, 256 색 \
      32 x 32, 256 색 \
      48 x 48, 256 색 \
      64 x 64, 256 색 \
      96 x 96, 256 색
   :::column-end:::
   :::column span="":::
      16 x 16, 단색 \
      32 x 32, 단색 \
      48 x 48, 단색 \
      64 x 64, 단색 \
      96 x 96, 단색
   :::column-end:::
:::row-end:::

> [!NOTE]
> 모든 기존 이미지는이 목록에 표시 되지 않습니다.

사용자 **지정 속성은** 사용자 지정 크기와 색 수를 사용 하 여 새 이미지를 만들 수 있는 **사용자 지정 이미지** 대화 상자를 엽니다.

**사용자 지정 이미지** 대화 상자를 사용 하 여 사용자 지정 크기와 색 수를 사용 하 여 새 이미지를 만들 수 있습니다. 포함 되는 속성은 다음과 같습니다.

|속성|설명|
|---|---|
|**Width**|사용자 지정 이미지의 너비 (1-512, 2048의 제한)를 입력할 수 있는 공간을 제공 합니다.|
|**높이**|사용자 지정 이미지의 높이를 픽셀 단위로 입력할 수 있는 공간을 제공 합니다 (1-512, 제한인 2048).|
|**색**|사용자 지정 이미지에 대 한 색 수를 선택할 수 있는 공간 (2, 16 또는 256)을 제공 합니다.|

** &lt; 장치 &gt; 이미지 열기** 대화 상자를 사용 하 여 c + + 프로젝트에서 장치 이미지를 열 수 있습니다. 현재 리소스 (현재 리소스의 일부인 이미지)의 기존 장치 이미지를 나열 합니다. 포함 되는 속성은 다음과 같습니다.

|속성|설명|
|---|---|
|**현재 이미지**|리소스에 포함 된 이미지를 나열 합니다. 열려는 이미지 형식을 선택 합니다.|

#### <a name="to-create-a-new-icon-or-cursor"></a>새 아이콘 또는 커서를 만들려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 *.rc* 파일을 마우스 오른쪽 단추로 클릭 한 다음 **리소스 삽입**을 선택 합니다. *.Rc* 파일에 커서와 같은 기존 이미지 리소스가 이미 있는 경우 **커서** 폴더를 마우스 오른쪽 단추로 클릭 하 고 **커서 삽입**을 선택할 수 있습니다.

1. [리소스 삽입 대화 상자](./how-to-create-a-resource-script-file.md)에서 **아이콘** 또는 **커서** 를 선택 하 고 **새로 만들기**를 선택 합니다. 아이콘의 경우이 작업은 32 × 32, 16 색 아이콘을 사용 하 여 아이콘 리소스를 만듭니다. 커서의 경우 32 × 32, 단색 (2 색) 이미지가 만들어집니다.

   **+** **리소스 삽입** 대화 상자에서 이미지 리소스 형식 옆에 더하기 기호 ()가 표시 되 면 도구 모음 템플릿을 사용할 수 있음을 의미 합니다. 더하기 기호를 선택 하 여 템플릿 목록을 확장 하 고, 템플릿을 선택 하 고, **새로 만들기**를 선택 합니다.

### <a name="to-add-an-image-for-a-different-display-device"></a>다른 디스플레이 장치용 이미지를 추가 하려면

1. 메뉴 **이미지**  >  **새 장치 이미지**로 이동 하거나, **이미지 편집기** 창에서 마우스 오른쪽 단추를 클릭 하 고 **새 장치 이미지**를 선택 합니다.

1. 추가 하려는 이미지의 형식을 선택 합니다. **사용자 지정** 을 선택 하 여 기본 목록에서 사용할 수 없는 크기의 아이콘을 만들 수도 있습니다.

### <a name="to-copy-a-device-image"></a>장치 이미지를 복사 하려면

1. 메뉴 **이미지**  >  **장치 이미지 열기** 로 이동 하 고 현재 이미지 목록에서 이미지를 선택 합니다. 예를 들어 32 × 32, 16 색 버전의 아이콘을 선택 합니다.

1. 현재 표시 된 아이콘 이미지를 복사 합니다 (**Ctrl** + **C**).

1. 다른 **이미지 편집기** 창에서 다른 아이콘 이미지를 엽니다. 예를 들어 아이콘의 16 × 16, 16 색 버전을 엽니다.

1. 아이콘 이미지 (**Ctrl** + **V**)를 한 **이미지 편집기** 창에서 다른 이미지 편집기 창에 붙여 넣습니다. 더 큰 크기를 더 작은 크기로 붙여 넣는 경우 아이콘 핸들을 사용 하 여 이미지의 크기를 조정할 수 있습니다.

### <a name="to-delete-a-device-image"></a>장치 이미지를 삭제 하려면

아이콘 이미지가 **이미지 편집기**에 표시 되는 동안 메뉴 **이미지**  >  **장치 이미지 삭제**로 이동 합니다. 리소스에서 마지막 아이콘 이미지를 삭제 하면 리소스도 삭제 됩니다.

> [!NOTE]
> **Del** 키를 누르면 아이콘에 그려진 이미지와 색이 삭제 되지만 아이콘은 그대로 유지 되 고 이제 다시 디자인할 수 있습니다. 실수로 **Del** 키를 누르면 **Ctrl** + **Z** 를 눌러 작업을 실행 취소 합니다.

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>장치 이미지에서 투명 한 영역 또는 반전 영역을 만들려면

[이미지 편집기](../windows/image-editor-for-icons.md)에서 초기 아이콘이 나 커서 이미지에는 투명 한 특성이 있습니다. 아이콘 및 커서 이미지는 사각형 이지만 이미지의 일부는 투명 하 고 화면의 기본 이미지는 아이콘이 나 커서를 통해 표시 되기 때문에 많은 부분이 나타나지 않습니다. 아이콘을 끌면 이미지 일부가 반전 된 색으로 나타날 수 있습니다. [색 창](./image-editor-for-icons.md)에서 화면 색과 반전색을 설정 하 여이 효과를 만듭니다.

아이콘 및 커서에 적용 하는 화면색 및 반전색은 파생 된 이미지를 모양 및 색으로 지정 하거나 역 영역을 할당 합니다. 색은 해당 특성이 있는 이미지의 일부를 표시 합니다. 편집에서 화면색 및 반전색 특성을 나타내는 색을 변경할 수 있습니다. 이러한 변경 내용은 응용 프로그램의 아이콘이 나 커서의 모양에 영향을 주지 않습니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정 또는 버전에 따라 **도움말**에 설명된 것과 다를 수 있습니다. 설정을 변경 하려면 메뉴 **도구**  >  **설정 가져오기 및 내보내기**로 이동 합니다. 자세한 내용은 [Visual Studio IDE 개인 설정](/visualstudio/ide/personalizing-the-visual-studio-ide)을 참조하세요.

#### <a name="to-create-transparent-or-inverse-regions"></a>투명 한 영역 또는 반전 영역을 만들려면

1. **색** 창에서 선택기 **화면색** 또는 **반전색**을 선택 합니다.

1. 그리기 도구를 사용 하 여 이미지에 화면 또는 반전색을 적용 합니다. 그리기 도구에 대 한 자세한 내용은 [그리기 도구 사용](using-a-drawing-tool-image-editor-for-icons.md)을 참조 하세요.

#### <a name="to-change-the-screen-or-inverse-color"></a>화면 또는 반전 색을 변경 하려면

1. **화면 색** 선택기 나 **반전색** 선택기 중 하나를 선택 합니다.

1. **색 창의 색 색상표에서** **색을** 선택 합니다.

   다른 선택기에 대해 보충 색이 자동으로 할당 됩니다.

   > [!TIP]
   > **화면색** 또는 **반전색** 선택기를 두 번 클릭 하면 [사용자 지정 색 선택 대화 상자가](./image-editor-for-icons.md) 나타납니다.

### <a name="use-the-256-color-palette"></a>256 색상표 사용

**이미지 편집기**를 사용 하 여 아이콘 및 커서를 선택할 수 있는 256 색상표를 사용 하 여 큰 크기 (64 × 64)로 크기를 지정할 수 있습니다. 리소스를 만든 후에는 장치 이미지 스타일이 선택 됩니다.

#### <a name="to-create-a-256-color-icon-or-cursor"></a>256 색 아이콘 또는 커서를 만들려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 *.rc* 파일을 마우스 오른쪽 단추로 클릭 한 다음 **리소스 삽입**을 선택 합니다. *.Rc* 파일에 커서와 같은 기존 이미지 리소스가 이미 있는 경우 **커서** 폴더를 마우스 오른쪽 단추로 클릭 하 고 **커서 삽입**을 선택할 수 있습니다.

1. [리소스 삽입 대화 상자](./how-to-create-a-resource-script-file.md)에서 **아이콘** 또는 **커서** 를 선택 하 고 **새로 만들기**를 선택 합니다.

1. 메뉴 **이미지**  >  **새 장치 이미지** 로 이동 하 여 원하는 256 색 이미지 스타일을 선택 합니다.

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>크게 아이콘의 256 색상표에서 색을 선택 하려면

256 색상표에서 선택 항목을 그리려면 [색 창의](./image-editor-for-icons.md) **색 색상표에서 색을** 선택 해야 합니다.

1. 크게 아이콘이 나 커서를 선택 하거나 새로운 크게 아이콘이 나 커서를 만듭니다.

1. **색** 창의 **색** 색상표에 표시 되는 256 색에서 색을 선택 합니다.

   선택한 색은 **색** 창의 **색** 색상표에서 현재 색이 됩니다.

   > [!NOTE]
   > 256 색 이미지에 사용 되는 초기 색상표는 Windows API에서 반환 된 색상표와 일치 합니다 `CreateHalftonePalette` . Windows 셸에 사용 되는 모든 아이콘은 색상표 인식 중에 깜빡임을 방지 하기 위해이 색상표를 사용 해야 합니다.

### <a name="to-set-a-cursors-hot-spot"></a>커서의 핫 스폿을 설정 하려면

커서의 핫 스폿은 Windows에서 커서 위치를 추적 하는 지점입니다. 기본적으로 핫 스폿은 좌표를 사용 하 여 커서의 왼쪽 위 모퉁이로 설정 됩니다 `0,0` . [속성 창](/visualstudio/ide/reference/properties-window)의 **Hotspot** 속성은 핫 스폿 좌표를 표시합니다.

1. [이미지 편집기 도구 모음](./image-editor-for-icons.md)에서 **핫스폿 설정** 도구를 선택 합니다.

1. 커서의 핫 스폿으로 할당할 픽셀을 선택 합니다.

   **속성** 창의 **핫스폿** 속성은 새 좌표를 표시 합니다.

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>비트맵을 만들어 .gif 또는 .jpeg로 저장 하려면

비트맵을 만들 때 비트맵 형식 (.bmp)으로 이미지가 만들어집니다. 그러나 이미지를 GIF 또는 JPEG 나 다른 그래픽 형식으로 저장할 수 있습니다.

> [!NOTE]
> 이 프로세스는 아이콘 및 커서에는 적용 되지 않습니다.

1. 메뉴 **파일**  >  **열기**로 이동한 다음 **파일**을 선택 합니다.

1. **새 파일 대화 상자**에서 **Visual C++** 폴더를 선택한 다음, **템플릿** 상자에서 **비트맵 파일 (.bmp)** 을 선택 하 고 **열기**를 선택 합니다.

   비트맵이 **이미지 편집기**에서 열립니다.

1. 필요에 따라 새 비트맵을 변경 합니다.

1. 비트맵을 **이미지 편집기**에서 연 상태에서 메뉴 **파일**파일  >  ** *이름*.bmp로**이동 합니다.

1. 다른 이름 **으로 파일 저장** 대화 상자에서 파일에 지정할 이름 및 파일 **이름** 상자에 원하는 파일 형식을 나타내는 확장명을 입력 합니다. 예를 들어 *myfile.gif*합니다.

   > [!NOTE]
   > 다른 파일 형식으로 저장 하려면 프로젝트 외부에서 비트맵을 만들거나 열어야 합니다. 프로젝트 내에서 만들거나 여는 경우 **다른 이름으로 저장** 명령을 사용할 수 없습니다. 자세한 내용은 [프로젝트 외부에서 리소스 스크립트 파일의 리소스 보기 (독립 실행형)](./how-to-create-a-resource-script-file.md)를 참조 하세요.

1. **저장**을 선택합니다.

### <a name="to-convert-an-image-from-one-format-to-another"></a>이미지를 한 형식에서 다른 형식으로 변환 하려면

**이미지 편집기** 에서 GIF 또는 JPEG 이미지를 열고 비트맵으로 저장할 수 있습니다. 또한 비트맵 파일을 열고 GIF 또는 JPEG로 저장할 수 있습니다. 작업 하는 이미지는 개발 환경에서 편집 하기 위해 프로젝트에 포함 되지 않아도 됩니다 ( [독립 실행형 이미지 편집](./selecting-an-area-of-an-image-image-editor-for-icons.md)참조).

1. **이미지 편집기**에서 이미지를 엽니다.

1. 메뉴 파일 파일 **File**  >  ** *이름* 으로**이동을로 이동 합니다.

1. 다른 이름 **으로 파일 저장** 대화 상자의 **파일 이름** 상자에 원하는 형식을 나타내는 파일 이름과 확장명을 입력 합니다.

1. **저장**을 선택합니다.

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>관리 되지 않는 c + + 프로젝트에 새 이미지 리소스를 추가 하려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 *.rc* 파일을 마우스 오른쪽 단추로 클릭 한 다음 **리소스 삽입**을 선택 합니다. *.Rc* 파일에 커서와 같은 기존 이미지 리소스가 이미 있는 경우 **커서** 폴더를 마우스 오른쪽 단추로 클릭 하 고 **커서 삽입**을 선택할 수 있습니다.

1. [리소스 삽입 대화 상자](./how-to-create-a-resource-script-file.md)에서 만들려는 이미지 리소스의 유형 (예:**비트맵**)을 선택 하 고 **새로**만들기를 선택 합니다.

   **+** **리소스 삽입** 대화 상자에서 이미지 리소스 형식 옆에 더하기 기호 ()가 표시 되 면 도구 모음 템플릿을 사용할 수 있음을 의미 합니다. 더하기 기호를 선택 하 여 템플릿 목록을 확장 하 고, 템플릿을 선택 하 고, **새로 만들기**를 선택 합니다.

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>.NET 프로그래밍 언어의 프로젝트에 새 이미지 리소스를 추가 하려면

1. **솔루션 탐색기**에서 프로젝트 폴더를 마우스 오른쪽 단추로 클릭 합니다 (예: *WindowsApplication1*).

1. 바로 가기 메뉴에서 **추가**를 선택한 다음, **새 항목 추가**를 선택 합니다.

1. **범주** 창에서 **로컬 프로젝트 항목** 폴더를 확장 한 다음 **리소스**를 선택 합니다.

1. **템플릿** 창에서 프로젝트에 추가 하려는 리소스 종류를 선택 합니다.

   리소스가 **솔루션 탐색기** 의 프로젝트에 추가 되 고 리소스가 [이미지 편집기](../windows/image-editor-for-icons.md)에서 열립니다. 이제 이미지 **편집기** 에서 사용 가능한 모든 도구를 사용 하 여 이미지를 수정할 수 있습니다. 관리 되는 프로젝트에 이미지를 추가 하는 방법에 대 한 자세한 내용은 [디자인 타임에 그림 로드](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms)를 참조 하세요.

## <a name="requirements"></a>요구 사항

없음

## <a name="see-also"></a>참고 항목

[아이콘에 대 한 이미지 편집기](../windows/image-editor-for-icons.md)<br/>
[방법: 이미지 편집](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[방법: 그리기 도구 사용](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[방법: 색 작업](../windows/working-with-color-image-editor-for-icons.md)<br/>
[액셀러레이터 키](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
<!--
[Converting Bitmaps to Toolbars](./toolbar-editor.md)<br/>
[Creating New Toolbars](./toolbar-editor.md)<br/>
[Icons](/windows/win32/menurc/icons)<br/>
[Cursors](/windows/win32/menurc/cursors)<br/>-->
