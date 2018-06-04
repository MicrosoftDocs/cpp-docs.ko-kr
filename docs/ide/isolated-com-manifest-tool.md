---
title: 매니페스트 도구 격리 COM 속성(Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
dev_langs:
- C++
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c425a71f8bb8a7972ade29fb0d18cf3eab7debb5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330183"
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>격리 COM, 매니페스트 도구, 구성 속성, &lt;Projectname&gt; 속성 페이지 대화 상자
이 대화 상자를 사용하여 [Mt.exe](http://msdn.microsoft.com/library/aa375649)에 대한 **격리 COM** 옵션을 지정합니다.  
  
 이 속성 페이지 대화 상자에 액세스하려면 프로젝트 또는 속성 시트의 속성 페이지를 엽니다. **공용 속성**에서 **매니페스트 도구** 노드를 확장한 다음, **격리 COM**을 선택합니다.  
  
## <a name="task-list"></a>작업 목록  
  
-   [방법: COM 구성 요소를 사용하는 격리된 응용 프로그램 빌드](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
## <a name="uielement-list"></a>UI 요소 목록  
 **형식 라이브러리 파일**  
 /tlb 옵션을 사용하여 매니페스트 도구가 매니페스트 파일을 생성하는 데 사용할 형식 라이브러리 파일(.tlb 파일)의 이름을 지정합니다.  
  
 **등록자 스크립트 파일**  
 /rgs 옵션을 사용하여 매니페스트 도구가 매니페스트 파일을 생성하는 데 사용할 등록자 스크립트 파일(.rgs 파일)의 이름을 지정합니다.  
  
 **구성 요소 파일 이름**  
 /dll 옵션을 사용하여 매니페스트 도구가 생성할 리소스의 이름을 지정합니다. **형식 라이브러리 파일** 또는 **등록자 스크립트 파일**에 대한 값이 지정되면 이 속성의 값을 입력해야 합니다.  
  
 **대체 파일**  
 /replacements 옵션을 사용하여 .rgs 파일에서 대체 가능한 문자열 값이 포함된 파일의 전체 경로를 지정합니다.  
  
## <a name="see-also"></a>참고 항목  
 [격리된 응용 프로그램](http://msdn.microsoft.com/library/aa375190)   
 [ClickOnce 응용 프로그램 매니페스트](/visualstudio/deployment/clickonce-application-manifest)   
 [매니페스트 도구 속성 페이지](../ide/manifest-tool-property-pages.md)   
 [프로젝트 속성 사용](../ide/working-with-project-properties.md)   