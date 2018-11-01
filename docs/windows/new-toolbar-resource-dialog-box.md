---
title: 새 도구 모음 리소스 대화 상자 (c + +)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.newtoolbarresource
helpviewer_keywords:
- New Toolbar Resource dialog box [C++]
ms.assetid: 52dd01ad-e748-4ab2-b3eb-59f5df990ca6
ms.openlocfilehash: 7c45daeb2c07426918f1a636f4230c1c07026ca2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595925"
---
# <a name="new-toolbar-resource-dialog-box-c"></a>새 도구 모음 리소스 대화 상자 (c + +)

합니다 **새 도구 모음 리소스** 대화 상자를 사용 하면 c + + 프로젝트의 도구 모음 리소스를 추가 하는 단추의 높이 너비를 지정할 수 있습니다. 기본값은 16 × 15 픽셀입니다.

도구 모음을 만드는 데 사용 되는 비트맵은 2048의 최대 너비입니다. 설정한 경우 합니다 **단추 너비** 단추 4 개를 하나만 사용할 수 있습니다, 512입니다. 513에 너비를 설정 하는 경우만 세 개의 단추가 있습니다.

### <a name="button-width"></a>단추 너비

도구 모음 리소스 비트맵 리소스를 변환 하는 도구 모음 단추에 대 한 너비를 입력할 공간을 제공 합니다. 이미지 너비와 높이가 지정 된 자르고 색 표준 도구 모음 색 (16 색)을 사용 하도록 조정 됩니다.

### <a name="button-height"></a>단추의 높이

도구 모음 리소스 비트맵 리소스를 변환 하는 도구 모음 단추에 대 한 높이 입력할 공간을 제공 합니다. 이미지 너비와 높이가 지정 된 자르고 색 표준 도구 모음 색 (16 색)을 사용 하도록 조정 됩니다.

관리 되는 프로젝트에 리소스를 추가 하는 방법에 대 한 정보를 참조 하세요 [데스크톱 앱의 리소스](/dotnet/framework/resources/index) 에 *.NET Framework Developer's Guide*합니다. 수동으로 관리 되는 프로젝트에 리소스 파일을 추가, 리소스 액세스, 정적 리소스 표시 및 속성에 리소스 문자열 할당에 대 한 내용은 참조 하세요 [데스크톱 앱에 대 한 리소스 파일 만들기](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)합니다. 전역화 및 지역화 관리 되는 앱의 리소스에 대 한 내용은 참조 하세요 [Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)합니다.

## <a name="requirements"></a>요구 사항

MFC 또는 ATL

## <a name="see-also"></a>참고 항목

[도구 모음 단추 속성](../windows/toolbar-button-properties.md)<br/>
[비트맵을 도구 모음으로 변환](../windows/converting-bitmaps-to-toolbars.md)<br/>
[도구 모음 편집기](../windows/toolbar-editor.md)