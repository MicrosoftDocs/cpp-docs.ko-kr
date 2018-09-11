---
title: 장치 이미지 (아이콘에 대 한 이미지 편집기)에서 투명 하 게 또는 반전 영역 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
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
ms.assetid: a994954b-b039-4391-a535-58d1fa10fc3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ab57df8151d02064b244212f28fe21628f0f3bb8
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314848"
---
# <a name="creating-transparent-or-inverse-regions-in-device-images-image-editor-for-icons"></a>장치 이미지에서 투명한 영역 또는 반전 영역 만들기(아이콘에 대한 이미지 편집기)

에 [이미지 편집기](../windows/image-editor-for-icons.md), 초기 아이콘 또는 커서 이미지의 특성은 투명 합니다. 아이콘 및 커서 이미지는 사각형, 대부분 표시 되지 않습니다 있도록 이미지 부분; 투명 하 게 되므로 아이콘 또는 커서를 통해 화면에서 기본 이미지를 보여 줍니다. 아이콘을 끌어 이미지의 부분 반전된 된 색으로 나타날 수 있습니다. 화면색 및 반전색에서 설정 하 여 이러한 효과 낼 합니다 [색 창](../windows/colors-window-image-editor-for-icons.md)합니다.

아이콘의 화면 및 역 색을 적용 하 고 커서 셰이프 및 파생된 이미지 색 또는 반전 영역을 지정 합니다. 색은 해당 특성을 갖는 이미지 부분을 나타냅니다. 편집 화면색 및 반전색 특성을 나타내는 색을 변경할 수 있습니다. 이러한 변경 내용은 아이콘이 나 응용 프로그램에서 커서의 모양을 영향을 주지 않습니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정 또는 버전에 따라 **도움말**에 설명된 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio IDE 개인 설정](/visualstudio/ide/personalizing-the-visual-studio-ide)을 참조하세요.

### <a name="to-create-transparent-or-inverse-regions"></a>투명 또는 반전 영역을 만드는 데

1. 에 **색** 창에서 클릭 합니다 **화면 색상** 선택기 또는 **반전색** 선택기.

2. 화면 또는 반전색 그리기 도구를 사용 하 여 이미지에 적용 됩니다. 그리기 도구에 대 한 자세한 내용은 참조 하세요. [그리기 도구를 사용 하 여](using-a-drawing-tool-image-editor-for-icons.md)입니다.

### <a name="to-change-the-screen-or-inverse-color"></a>화면 또는 역 색을 변경 하려면

1. 중 하나를 선택 합니다 **화면색** 선택기 또는 **반전색** 선택기입니다.

2. 색을 선택 합니다 **색** 색상표에는 **색** 창입니다.

   보완 색상 다른 선택기에 대 한 자동 지정 됩니다.

   > [!TIP]
   > 두 번 클릭 합니다 **화면색** 또는 **반전색** 선택기를 [사용자 지정 색 선택 대화 상자](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) 나타납니다.

관리 되는 프로젝트에 리소스를 추가 하는 방법에 대 한 정보를 참조 하세요 [데스크톱 앱의 리소스](/dotnet/framework/resources/index) 에 *.NET Framework Developer's Guide*합니다. 수동으로 관리 되는 프로젝트에 리소스 파일을 추가, 리소스 액세스, 정적 리소스 표시 및 속성에 리소스 문자열 할당에 대 한 내용은 참조 하세요 [데스크톱 앱에 대 한 리소스 파일 만들기](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)합니다. 전역화 및 지역화 관리 되는 앱의 리소스에 대 한 내용은 참조 하세요 [Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)합니다.

## <a name="requirements"></a>요구 사항

없음

## <a name="see-also"></a>참고 항목

[액셀러레이터 키](../windows/accelerator-keys-image-editor-for-icons.md)  
[아이콘 및 커서: 디스플레이 장치용 이미지 리소스](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)