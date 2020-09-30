---
title: '방법: 그리기 도구 사용'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.drawing
helpviewer_keywords:
- Image editor [C++], selecting drawing tools
- Image editor [C++], toolbar
- drawing tools
- Image editor [C++], drawing lines
- shapes, drawing
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
ms.openlocfilehash: 46ba1f1057484f2b5b1e1286482d80fd96312caf
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502928"
---
# <a name="how-to-use-a-drawing-tool"></a>방법: 그리기 도구 사용

**이미지 편집기** 는 모두 같은 방식으로 작동 하는 도구를 자유롭게 그리거나 지우는 도구를 포함 합니다. 도구를 선택 하 고 필요한 경우 전경색과 [배경색](./image-editor-for-icons.md) , 크기 및 모양 옵션을 선택 합니다. 그런 다음 포인터를 이미지로 이동 하 고,를 클릭 하거나 끌어 그리기 및 지우기로 이동 합니다.

## <a name="drawing-tools"></a>그리기 도구

**이미지 편집기** 도구 모음이 나 **이미지** 메뉴에서 그리기 도구를 선택할 수 있습니다. **지우개** 도구, **브러시** 도구 또는 **어 브러시** 도구를 선택 하면 옵션 선택기에 해당 도구의 옵션이 표시 됩니다.

> [!TIP]
> [이미지 편집기 도구 모음의](./image-editor-for-icons.md)단추 위에 커서를 놓으면 도구 설명이 나타납니다. 이러한 팁은 여기에 언급 된 특정 단추를 식별 하는 데 도움이 됩니다.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>이미지 편집기 도구 모음에서 그리기 도구를 선택 하 고 사용 하려면

1. **이미지 편집기** 도구 모음에서 단추를 선택 합니다.

   - **지우개** 도구는 마우스 왼쪽 단추를 누를 때 현재 배경색으로 이미지를 그립니다.

      > [!TIP]
      > **지우개** 도구를 사용 하는 대신 그리기 도구 중 하나를 사용 하 여 배경색으로 그리는 것이 더 편리할 수 있습니다.

   - **연필** 도구는 단일 픽셀의 상수 너비로 freehand를 그립니다.

   - **브러시** 도구에는 다양 한 모양과 크기가 있습니다.

   - 에 **어** 브러시 도구는 브러시의 중심을 기준으로 색 픽셀을 임의로 배포 합니다.

1. 필요한 경우 색 및 브러시를 선택 합니다.

   - [색 색상표](./image-editor-for-icons.md)에서 마우스 왼쪽 단추를 선택 하 여 전경색을 선택 하거나 마우스 오른쪽 단추를 선택 하 여 배경색을 선택 합니다.

   - [옵션 선택기에서](./image-editor-for-icons.md)사용 하려는 브러시를 나타내는 셰이프를 선택 합니다.

1. 이미지에서 그리기 또는 그리기를 시작 하려는 위치를 가리킵니다. 포인터는 선택한 도구에 따라 모양이 변경 됩니다.

1. 왼쪽 마우스 단추 (전경색의 경우) 또는 오른쪽 마우스 단추 (배경색의 경우)를 누른 채 그릴 때 해당 단추를 누릅니다.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>이미지 메뉴에서 그리기 도구를 선택 하 고 사용 하려면

1. 메뉴 **이미지**  >  **도구**로 이동 합니다.

1. 연계 하위 메뉴에서 사용 하려는 도구를 선택 합니다.

## <a name="lines-or-closed-figures"></a>선 또는 폐쇄형 그림

선 및 닫힌 그림을 그리기 위한 **이미지 편집기** 도구는 모두 같은 방식으로 작동 합니다. 즉, 한 지점에 삽입 지점을 놓고 다른 지점으로 끌어 놓습니다. 줄의 경우 이러한 점은 끝점입니다. 폐쇄형 그림의 경우 이러한 요소는 그림에 경계 하는 사각형의 반대쪽 모퉁이입니다.

선은 현재 브러시 선택에 의해 결정 되는 너비로 그려지며, 그림 그림은 현재 너비 선택에 따라 결정 되는 너비로 그려집니다. 왼쪽 마우스 단추를 누르거나 현재 배경색으로 마우스 오른쪽 단추를 누르면 선과 채워진 선 및 채워진 모든 그림이 현재 전경색으로 그려집니다.

### <a name="to-draw-a-line"></a>선을 그리려면

1. [이미지 편집기 도구 모음](./image-editor-for-icons.md) 을 사용 하거나 메뉴 **이미지**도구로 이동 하 여 >  **Tools** **선** 도구를 선택 합니다.

1. 필요한 경우 색 및 브러시를 선택 합니다.

   - [색 색상표](./image-editor-for-icons.md)에서 마우스 왼쪽 단추를 선택 하 여 전경색을 선택 하거나 마우스 오른쪽 단추를 선택 하 여 배경색을 선택 합니다.

   - [옵션 선택기에서](./image-editor-for-icons.md)사용 하려는 브러시를 나타내는 셰이프를 선택 합니다.

1. 줄의 시작 지점에 포인터를 놓습니다.

1. 를 줄의 끝점으로 끕니다.

### <a name="to-draw-a-closed-figure"></a>폐쇄형 그림을 그리려면

1. **이미지 편집기** 도구 모음을 사용 하거나 메뉴 **이미지**  >  **도구로** 이동 하 여 **닫힌 그림 그리기** 도구를 선택 합니다.

   **닫힌 그림 그리기** 도구는 해당 단추에 표시 된 대로 그림을 만듭니다.

1. 필요한 경우 색 및 선 두께를 선택 합니다.

1. 포인터를 그림을 그릴 사각형 영역의 한 모퉁이로 이동 합니다.

1. 포인터를 대각선 방향의 대각선으로 끌어 놓습니다.

## <a name="custom-brushes"></a>사용자 지정 브러시

사용자 지정 브러시는 이미지 **편집기**의 미리 만든 브러시 중 하 나와 같이 선택 하 여 사용 하는 이미지의 사각형 부분입니다. 선택 영역에서 수행할 수 있는 모든 작업은 사용자 지정 브러시 에서도 수행할 수 있습니다.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>이미지의 일부에서 사용자 지정 브러시를 만들려면

1. 브러시에 사용할 이미지의 파트를 선택 합니다.

1. **Shift** 키를 누른 상태에서 선택 영역을 선택 하 고 이미지 전체로 끌거나 메뉴 **이미지**로 이동을 선택 하  >  **여 브러시로 선택**합니다.

   선택 항목은 이미지 전체에서 선택 영역에 있는 색을 배포 하는 사용자 지정 브러시가 됩니다. 선택 항목의 복사본은 끌기 경로를 따라 유지 됩니다. 더 천천히 끌면 복사본이 더 많이 생성 됩니다.

   > [!NOTE]
   > 이미지의 일부를 먼저 선택 하지 않고 **선택 항목을 브러시로 사용** 을 선택 하면 전체 이미지가 브러시로 사용 됩니다. 또한 사용자 지정 브러시를 사용한 결과는 [불투명 또는 투명 한 배경을](./image-editor-for-icons.md)선택 했는지 여부에 따라 달라 집니다.

현재 배경색과 일치 하는 사용자 지정 브러시의 픽셀은 일반적으로 투명 합니다. 기존 이미지를 칠하지 않습니다. 배경 색 픽셀이 기존 이미지 위에 표시 되도록이 동작을 변경할 수 있습니다.

스탬프 또는 스텐실과 같은 사용자 지정 브러시를 사용 하 여 다른 특수 효과를 만들 수 있습니다.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>배경색으로 사용자 지정 브러시 셰이프를 그리려면

1. 불투명 또는 투명 한 배경을 선택 합니다.

1. 배경색을 그리려는 색으로 설정 합니다.

1. 사용자 지정 브러시를 그리려는 위치에 배치 합니다.

1. 마우스 오른쪽 단추를 선택 합니다. 사용자 지정 브러시의 불투명 영역은 배경색으로 그려집니다.

### <a name="to-double-or-halve-the-custom-brush-size"></a>사용자 지정 브러시 크기를 두 배 또는 halve

**더하기 기호** ( **+** ) 키를 눌러 브러시 크기를 두 번 입력 하거나 **빼기 기호** ( **-** ) 키를 눌러 halve.

### <a name="to-cancel-the-custom-brush"></a>사용자 지정 브러시를 취소 하려면

**Esc** 키를 누르거나 다른 그리기 도구를 선택 합니다.

## <a name="requirements"></a>요구 사항

없음

## <a name="see-also"></a>참고 항목

[아이콘에 대 한 이미지 편집기](../windows/image-editor-for-icons.md)<br/>
[방법: 아이콘 또는 다른 이미지 만들기](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[방법: 이미지 편집](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[방법: 색 작업](../windows/working-with-color-image-editor-for-icons.md)<br/>
[액셀러레이터 키](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
