---
title: '방법: 색 작업'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.color
- vc.editors.customcolorselector
- vc.editors.loadcolorpalette
- vc.editors.colorswindow
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors [C++], Image editor
- colors [C++]
- Image editor [C++], colors
- colors [C++], Image editor
- colors [C++], image
- images [C++], colors
- Image editor [C++], colors
- Fill tool
- colors [C++], image
- images [C++], colors
- colors [C++], selection tools
- Image editor [C++], colors
- Select Color tool
- dithered color, Image editor
- Custom Color Selector dialog box [C++]
- Image editor [C++], Colors Palette
- colors [C++], image
- bitmaps [C++], colors
- images [C++], colors
- HSL values
- Colors Palette, Image editor
- RGB color values
- Adjust Colors command [C++]
- Image editor [C++], dithered color
- Image editor [C++], Colors Palette
- Colors Palette, Image editor
- colors [C++], inverting
- colors [C++]
- Color Indicator
- colors [C++], Colors window
- Colors window, hiding colors
- Show Colors Window command
- Colors window, displaying colors
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
- color palettes
- Load Palette Colors dialog box [C++]
- opaque backgrounds [C++]
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- images [C++], transparency
- images [C++], opaque background
- colors [C++], image
- Image editor [C++], color inversion
- images [C++], colors
- colors [C++], inverting
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
ms.openlocfilehash: 3c9134fde9053f57f8848a37b1442728f6111c98
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502950"
---
# <a name="how-to-work-with-color"></a>방법: 색 작업

**이미지 편집기** 에는 색을 구체적으로 처리 하 고 사용자 지정 하는 다양 한 기능이 포함 되어 있습니다. 전경색 또는 배경색을 설정 하거나, 경계 영역을 색으로 채우거 나, 이미지에서 색을 선택 하 여 현재 전경색 또는 배경색으로 사용할 수 있습니다. [이미지 편집기 도구 모음의](./image-editor-for-icons.md) 도구와 **색** 창의 색상표를 함께 사용 하 여 이미지를 만들 수 있습니다.

**단색 및** 16 색 이미지의 모든 색 **이 색 창의 색상표에** 표시 됩니다. 16 가지 표준 색과 함께 사용자 지정 색을 직접 만들 수 있습니다. 색상표의 색을 변경 하면 이미지의 해당 색이 즉시 변경 됩니다.

256 색 아이콘 및 커서 이미지로 작업할 때 [속성 창](/visualstudio/ide/reference/properties-window) 의 **Colors** 속성이 사용 됩니다. 자세한 내용은 [256 색 아이콘 또는 커서 만들기](./creating-an-icon-or-other-image-image-editor-for-icons.md)를 참조 하세요.

트루 컬러 이미지를 만들 수도 있습니다. 그러나 색 샘플은 **색** 창의 전체 색상표에 표시 되지 않습니다. 전경색 또는 배경색 표시기 영역에만 표시 됩니다. 실제 색은 **사용자 지정 색 선택** 대화 상자를 사용 하 여 만듭니다.

사용자 지정 색상표를 디스크에 저장 하 고 필요에 따라 다시 로드할 수 있습니다. 가장 최근에 사용한 색상표는 레지스트리에 저장 되 고 다음에 Visual Studio를 시작할 때 자동으로 로드 됩니다.

**색** 창은 다음과 같은 두 부분으로 구성 됩니다.

- 색 **색상표**-사용할 수 있는 색을 나타내는 색 샘플의 배열입니다. 그래픽 도구를 사용 하는 경우 샘플을 선택 하 여 전경색 및 배경색을 선택할 수 있습니다.

- **색 표시기**는 화면색과 배경색 및 화면색 선택기와 반전색을 표시 합니다.

   ![Colors window](../windows/media/vccolorswindow.gif "vcColorsWindow")<br/>
   **색** 창

> [!NOTE]
> **화면 색** 및 **반전색** 도구는 아이콘 및 커서에만 사용할 수 있습니다.

[이미지 편집기 도구 모음](./image-editor-for-icons.md)에서 **색** 창을 사용할 수 있습니다.

- **색** 창을 표시 하려면 **이미지 편집기** 창을 마우스 오른쪽 단추로 클릭 하 고 **색 창 표시**를 선택 하거나 메뉴 [이미지](./image-editor-for-icons.md)  >  **색 표시 창**으로 이동 합니다.

- **색** 창을 숨기려면 창을 고정 해제 합니다 .이 작업을 수행 하면 창이 사용 되지 않을 때 자동으로 숨겨지도록 허용 됩니다. 또는 **닫기** 단추를 선택 합니다.

**색** 색상표는 처음에 16 개의 표준 색을 표시 합니다. 표시 된 색을 사용 하 여 사용자 지정 색을 직접 만들 수도 있습니다. 그런 다음 사용자 지정 색상표를 저장 및 로드할 수 있습니다.

**사용자 지정 색 선택** 대화 상자를 사용 하 여 다음 속성을 사용 하 여 이미지에 사용 하는 색을 사용자 지정할 수 있습니다.

|속성|설명|
|--------------------------|--------------------------|
|**그라데이션 색 표시**|선택한 색의 값을 변경 합니다.<br/><br/>변경할 색의 십자 표시를 설정 하 고 슬라이더를 위나 아래로 이동 하 여 색의 명도 또는 RGB 값을 변경 합니다.|
|**명도 막대**|**그라데이션 색 표시** 상자에서 선택한 색의 밝기를 설정 합니다.<br/><br/>흰색 화살표를 선택 하 여 막대의 위쪽으로 끌어 더 작은 밝기를 선택 합니다. **색** 상자에는 선택한 색과 설정한 밝기의 효과가 표시 됩니다.|
|**색상**|정의 하는 색의 색상 휠 값을 나열 합니다. 값의 범위는 0에서 240입니다. 여기서 0은 빨강, 60은 노란색, 120은 녹색, 180은 사이안, 200는 자홍, 240는 파란색입니다.|
|**Hue**|정의 하는 색의 색상 휠 값을 나열 합니다. 값의 범위는 0에서 240입니다. 여기서 0은 빨강, 60은 노란색, 120은 녹색, 180은 사이안, 200는 자홍, 240는 파란색입니다.|
|**채도**|정의 하는 색의 채도 값을 지정 합니다. 채도는 지정 된 색상의 색의 양입니다. 값의 범위는 0에서 240입니다.|
|**명도**|정의 하는 색의 명도 (밝기)를 나열 합니다. 값의 범위는 0에서 240입니다.|
|**Red**|정의 하는 색의 빨강 값을 지정 합니다. 값의 범위는 0에서 255입니다.|
|**Green**|정의 하는 색의 녹색 값을 지정 합니다. 값의 범위는 0에서 255입니다.|
|**Blue**|정의 하는 색의 파랑 값을 지정 합니다. 값의 범위는 0에서 255입니다.|

사용자 지정 색이 포함 된 **색** 색상표를 저장 하 고 로드할 수 있습니다. 기본적으로 Visual Studio를 시작할 때 가장 최근에 사용한 **색** 색상표가 자동으로 로드 됩니다.

> [!TIP]
> **이미지 편집기** 에는 **기본 색상표를** 복원할 수 있는 방법이 없기 때문에 기본 **색** 색상표를 *표준 pal* 또는 *default. p s p* 와 같은 이름으로 저장 하 여 기본 설정을 쉽게 복원할 수 있습니다.

**색상표 로드** 대화 상자를 사용 하 여 다음 속성으로 c + + 프로젝트에서 사용할 특수 색상표를 로드 합니다.

|속성|설명|
|-----------------|-----------------|
|**Look in**|파일이 나 폴더를 찾을 위치를 지정 합니다.<br/><br/>화살표를 선택 하 여 다른 위치를 선택 하거나 도구 모음에서 폴더 아이콘을 선택 하 여 수준을 이동 합니다.|
|**파일 이름**|열려는 파일의 이름을 입력할 수 있는 입력란을 제공 합니다.<br/><br/>이전에 연 파일을 신속 하 게 찾으려면 드롭다운 목록에서 파일 이름을 선택 합니다 (사용 가능한 경우).<br/><br/>파일을 검색 하는 경우 별표 (*)를 와일드 카드로 사용할 수 있습니다. 예를 들어를 입력 \* 하 여 \* 모든 파일의 목록을 볼 수 있습니다. 파일의 전체 경로 (예: *C:\My Documents\MyColorPalette.pal* 또는 * \\ \NetworkServer\MyFolder\MyColorPalette.pal*)를 입력할 수도 있습니다.|
|**파일 형식**|표시할 파일 유형을 나열 합니다.<br/><br/>색상표 (* pal)는 색상표의 기본 파일 형식입니다.|

## <a name="how-to"></a>방법

### <a name="to-select-foreground-or-background-colors"></a>전경색 또는 배경색을 선택 하려면

**지우개**를 제외 하 고, **이미지 편집기** 도구 모음의 도구는 각각 왼쪽 또는 오른쪽 마우스 단추를 누를 때 현재 전경색 또는 배경색을 사용 하 여 그립니다.

- 전경색을 선택 하려면 마우스 왼쪽 단추를 사용 하 여 **색** 색상표에서 원하는 색을 선택 합니다.

- 배경색을 선택 하려면 마우스 오른쪽 단추를 사용 하 여 **색** 색상표에서 원하는 색을 선택 합니다.

### <a name="to-fill-a-bounded-area-of-an-image-with-a-color"></a>이미지의 경계 영역을 색으로 채우려면

**이미지 편집기** 에서는 포함 된 이미지 영역을 현재 그리기 색 이나 현재 배경색으로 채울 **채우기** 도구를 제공 합니다.

### <a name="to-use-the-fill-tool"></a>채우기 도구를 사용 하려면

1. **이미지 편집기** 도구 모음을 사용 하거나 메뉴 **이미지**도구로 이동 하 여  >  **Tools** **채우기** 도구를 선택 합니다.

1. 필요한 경우 색 그리기를 선택 합니다. [색 색상표](./image-editor-for-icons.md)에서 마우스 왼쪽 단추를 선택 하 여 전경색을 선택 하거나 마우스 오른쪽 단추를 선택 하 여 배경색을 선택 합니다.

1. **채우기 도구를** 채우려는 영역으로 이동 합니다.

1. 왼쪽 또는 오른쪽 마우스 단추를 선택 하 여 전경색 또는 배경색으로 각각 채웁니다.

### <a name="to-pick-up-a-color-from-an-image-to-use-elsewhere"></a>이미지에서 색을 선택 하 여 다른 곳에서 사용할 수 있습니다.

**선택 색**또는 색 픽업 도구는 왼쪽 이나 오른쪽 마우스 단추를 누르는 지 여부에 따라 이미지의 색을 현재 전경색 또는 배경색으로 만듭니다. **색 선택** 도구를 취소 하려면 다른 도구를 선택 합니다.

1. **이미지 편집기** 도구 모음을 사용 하거나 메뉴 **이미지**도구로 이동 하 여  >  **Tools** **색 선택** 도구를 선택 합니다.

1. 이미지에서 선택 하려는 색을 선택 합니다.

   > [!NOTE]
   > 색을 선택 하면 **이미지 편집기** 에서 가장 최근에 사용한 도구를 다시 활성화 합니다.

1. 전경색으로 왼쪽 마우스 단추를 사용 하 여 그리거나 배경색에 마우스 오른쪽 단추를 사용 하 여 그립니다.

### <a name="to-choose-the-background"></a>배경을 선택 하려면

이미지에서 선택 영역을 이동 하거나 복사 하는 경우 선택 영역에서 현재 배경색과 일치 하는 모든 픽셀은 기본적으로 투명 하 고 대상 위치에서 픽셀을 숨기는 것이 아닙니다.

투명 한 배경 (기본값)에서 불투명 배경으로 전환 하 고 다시 되돌릴 수 있습니다. 선택 도구를 사용 하는 경우 **투명 한 배경** 및 **불투명 배경** 옵션이 **이미지 편집기** 도구 모음의 **옵션** 선택기에 표시 됩니다.

![배경 옵션 &#45; 불투명 또는 투명](../windows/media/vcimageeditoropaqtranspback.gif "배경 옵션 &#45; 불투명 또는 투명")<br/>
**이미지 편집기 도구 모음의** **투명 및 불투명 옵션**

#### <a name="to-switch-between-a-transparent-and-opaque-background"></a>투명 한 배경 및 불투명 배경 사이를 전환 하려면

**이미지 편집기** 도구 모음에서 **옵션** 선택기를 선택 하 고 적절 한 배경을 선택 합니다.

- **불투명 배경 (O)**: 선택 영역의 모든 부분에서 기존 이미지를 가립니다.

- **투명 한 배경 (T)**: 기존 이미지는 현재 배경색과 일치 하는 선택 영역의 일부를 표시 합니다.

> [!TIP]
> 바로 가기의 경우 **이미지** 메뉴에서 **불투명 그리기**를 선택 하거나 선택 취소 합니다.

선택 항목이 이미 적용 된 상태에서 이미지의 일부를 투명 하 게 변경 하는 동안에는 배경색을 변경할 수 있습니다.

### <a name="to-invert-the-colors-in-a-selection"></a>선택 영역에서 색을 반전 하려면

이미지 **편집기** 에서는 이미지를 반전 된 색으로 표시 하는 방법을 알 수 있도록 이미지의 선택 된 부분에서 색을 간편 하 게 반전 시킬 수 있습니다.

현재 선택 영역에서 색을 반전 하려면 메뉴 **이미지**  >  **색 반전**으로 이동 합니다.

### <a name="to-customize-or-change-colors-on-the-colors-palette"></a>색상표에서 색을 사용자 지정 하거나 변경 하려면

1. 메뉴 **이미지**  >  **색 조정**으로 이동 합니다.

1. **사용자 지정 색 선택** 대화 상자에서 해당 텍스트 상자에 RGB 또는 HSL 값을 입력 하 여 색을 정의 하거나 **그라데이션 색 표시** 상자에서 색을 선택 합니다.

1. **명도** 막대에서 슬라이더를 움직여 밝기를 설정 합니다.

1. 많은 사용자 지정 색이 디더링됩니다. 디더링 색에 가장 가까운 단색을 원하는 경우 **색** 상자를 두 번 클릭 합니다.

   나중에 디더링된 색을 원하는 경우 **광도** 표시줄에서 슬라이더를 이동 하거나 **그라데이션 색 표시** 상자에서 십자 표시를 다시 이동 하 여 디더링를 복원 합니다.

1. **확인** 을 선택 하 여 새 색을 추가 합니다.

### <a name="to-save-a-custom-colors-palette"></a>사용자 지정 색 색상표를 저장하려면

1. 메뉴 **이미지**  >  **저장 팔레트**로 이동 합니다.

1. 색상표를 저장할 디렉터리로 이동하고 색상표의 이름을 입력합니다.

1. **저장**을 선택합니다.

### <a name="to-load-a-custom-colors-palette"></a>사용자 지정 색 색상표를 로드하려면

1. 메뉴 **이미지**  >  **로드 팔레트**로 이동 합니다.

1. **색 색상표 로드** 대화 상자에서 올바른 디렉터리로 이동 하 고 로드할 색상표를 선택 합니다. **색상표** 는. p p a 파일 확장명으로 저장 됩니다.

## <a name="requirements"></a>요구 사항

없음

## <a name="see-also"></a>참고 항목

[아이콘에 대 한 이미지 편집기](../windows/image-editor-for-icons.md)<br/>
[방법: 아이콘 또는 다른 이미지 만들기](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[방법: 이미지 편집](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[방법: 그리기 도구 사용](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[액셀러레이터 키](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
