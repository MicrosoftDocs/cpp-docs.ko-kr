---
title: 새 도구 모음 (c + +) 만들기
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar
helpviewer_keywords:
- toolbars [C++], creating
- Toolbar editor [C++], creating new toolbars
- Insert Resource
ms.assetid: 1b28264b-0718-4df8-9f65-979805d2efef
ms.openlocfilehash: 3c36579560c78ff77a624e4827df9d6a9302ae57
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551309"
---
# <a name="creating-new-toolbars-c"></a>새 도구 모음 (c + +) 만들기

### <a name="to-create-a-new-toolbar"></a>새 도구 모음을 만들려면

1. **자원** 보거나.rc 파일을 마우스 오른쪽 단추로 클릭 한 다음 선택 **리소스 추가** 바로 가기 메뉴에서. (단추로 단순히 기존 도구 모음.rc 파일에 있는 경우는 **도구 모음** 선택한 폴더 **도구 모음 삽입** 바로 가기 메뉴에서.)

   > [!NOTE]
   > 프로젝트에 .rc 파일이 아직 없는 경우 [새 리소스 스크립트 파일 만들기](../windows/how-to-create-a-resource-script-file.md)를 참조하세요.

2. 에 **리소스 추가** 대화 상자에서 **도구 모음** 에 **리소스 종류** 목록을 클릭 하 **새**.

   더하기 기호 (**+**) 옆에 표시 되는 **도구 모음** 리소스 종류, 즉 모음 템플릿을 사용할 수 있습니다. 템플릿의 목록을 확장 하는 템플릿을 선택 하 고 클릭 더하기 기호를 클릭 **새로 만들기**합니다.

   \- 또는 -

3. [도구 모음에 기존 비트맵 이미지를 변환할](../windows/converting-bitmaps-to-toolbars.md)합니다.

관리 되는 프로젝트에 리소스를 추가 하는 방법에 대 한 정보를 참조 하세요 [데스크톱 앱의 리소스](/dotnet/framework/resources/index) 에 *.NET Framework Developer's Guide*합니다. 수동으로 관리 되는 프로젝트에 리소스 파일을 추가, 리소스 액세스, 정적 리소스 표시 및 속성에 리소스 문자열 할당에 대 한 내용은 참조 하세요 [데스크톱 앱에 대 한 리소스 파일 만들기](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)합니다. 전역화 및 지역화 관리 되는 앱의 리소스에 대 한 내용은 참조 하세요 [Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)합니다.

## <a name="requirements"></a>요구 사항

MFC 또는 ATL

## <a name="see-also"></a>참고 항목

[도구 모음 편집기](../windows/toolbar-editor.md)