---
title: 아이콘에 대 한 이미지 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.cursor.F1
- vc.editors.icon.F1
- vc.editors.cursor
- vc.editors.bitmap.F1
dev_langs:
- C++
helpviewer_keywords:
- editors, images
- resource editors, graphics
- Image editor [C++]
- resource editors, Image editor
ms.assetid: 586d2b8b-0348-4883-a85d-1ff0ddbf14dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b4f038dea14aedc4016746297ac99aedd57445eb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215843"
---
# <a name="image-editor-for-icons"></a>아이콘에 대한 이미지 편집기

이미지 편집기에는 도구 모음 비트맵 만들기에 도움이 되는 기능뿐 아니라 이미지 만들기와 편집에 사용하는 다양한 도구도 들어 있습니다. **이미지 편집기** 도구 모음에서 **이미지** 메뉴와 도구의 명령을 사용하여 비트맵, 아이콘 및 커서뿐 아니라 GIF나 JPEG 형식의 이미지도 편집할 수 있습니다.

이미지 편집기를 사용하면 다음과 같은 작업을 할 수 있습니다.

- [그래픽 리소스 편집](../windows/editing-graphical-resources-image-editor-for-icons.md)

- [색 작업](../windows/working-with-color-image-editor-for-icons.md)

- [아이콘과 커서를 사용한 작업: 디스플레이 장치용 이미지 리소스](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

- [이미지 편집기의 액셀러레이터 키 명령 사용](../windows/accelerator-keys-image-editor-for-icons.md)

합니다 **이미지 편집기** 창 두 창을 구분 분할줄으로 이미지 뷰 두 개가 표시 됩니다. 분할줄을 한 쪽에서 다른 쪽으로 끌면 창의 상대적 크기를 변경할 수 있습니다. 활성 창에는 선택 테두리가 표시됩니다.

합니다 **이미지 편집기** 창을 필요와 선호에 맞게 조정할 수 있습니다. [확대 비율을 변경](../windows/changing-the-magnification-factor-image-editor-for-icons.md) 하거나 [픽셀 모눈을 표시 또는 숨길](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md)수 있습니다.

> [!NOTE]
> 사용 하 여 **이미지 편집기**, 32 비트 이미지를 볼 수 있지만 편집할 수는 없습니다.

## <a name="visual-studio-image-library"></a>Visual Studio 이미지 라이브러리

무료로 다운로드할 수 있습니다 합니다 **Visual Studio 이미지 라이브러리** 여러 애니메이션, 비트맵 및 응용 프로그램에서 사용할 수 있는 아이콘을 포함 하는 합니다. 라이브러리를 다운로드하는 방법에 대한 자세한 내용은 [Visual Studio 이미지 라이브러리](/visualstudio/designers/the-visual-studio-image-library)를 참조하십시오.

## <a name="managed-resources"></a>관리되는 리소스

사용할 수는 **이미지** 편집기와 [바이너리 편집기](binary-editor.md) 관리 프로젝트에서 리소스 파일로 작업 하 합니다. 편집할 관리되는 리소스는 연결된 리소스여야 합니다. Visual Studio 리소스 편집기에서는 포함된 리소스를 편집할 수 없습니다.

관리 되는 프로젝트에 리소스를 추가 하는 방법에 대 한 정보를 참조 하세요 [데스크톱 앱의 리소스](/dotnet/framework/resources/index) 에 *.NET Framework Developer's Guide*합니다. 수동으로 관리 되는 프로젝트에 리소스 파일을 추가, 리소스 액세스, 정적 리소스 표시 및 속성에 리소스 문자열 할당에 대 한 내용은 참조 하세요 [데스크톱 앱에 대 한 리소스 파일 만들기](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)합니다. 전역화 및 지역화 관리 되는 앱의 리소스에 대 한 내용은 참조 하세요 [Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)합니다.

## <a name="requirements"></a>요구 사항

없음

## <a name="see-also"></a>참고 항목

[리소스 편집기](../windows/resource-editors.md)  
[아이콘](https://msdn.microsoft.com/library/windows/desktop/ms646973.aspx)