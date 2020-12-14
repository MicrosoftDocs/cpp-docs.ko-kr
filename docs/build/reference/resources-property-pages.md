---
description: '자세히 알아보기: 리소스 속성 페이지'
title: 리소스
ms.date: 08/28/2019
ms.topic: article
ms.assetid: dade2f6b-c51f-4c33-9023-41956ae4b5f6
f1_keywords:
- VC.Project.VCResourceCompilerTool.PreprocessorDefinitions
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- VC.Project.VCResourceCompilerTool.Culture
- VC.Project.VCResourceCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCResourceCompilerTool.IgnoreStandardIncludePath
- VC.Project.VCResourceCompilerTool.ShowProgress
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.ResourceOutputFileName
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: d074cbb6035bd138ca322197e50e9a3f892b325b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225104"
---
# <a name="resources-property-page"></a>리소스 속성 페이지

네이티브 Windows 데스크톱 프로그램의 경우 빌드는 [리소스 컴파일러 (rc.exe)](/windows/win32/menurc/resource-compiler) 를 호출 하 여 이미지, 문자열 테이블 및 *.res* 파일을 이진에 추가 합니다. 이 속성 페이지에 노출 되는 속성은 c + + 컴파일러 또는 링커가 아닌 리소스 컴파일러에 전달 됩니다. 여기에 나열 된 속성 및 RC 명령줄 옵션에 매핑되는 방법에 대 한 자세한 내용은 [Rc 사용 (Rc 명령줄)](/windows/win32/menurc/using-rc-the-rc-command-line-)을 참조 하세요. **리소스** 속성 페이지에 액세스 하는 방법에 대 한 자세한 내용은 [Visual Studio에서 c + + 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조 하세요. 프로그래밍 방식으로 이러한 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProjectEngine.VCResourceCompilerTool>을 참조하세요.

C + +/CLI 응용 프로그램의 .NET 리소스에 대 한 속성은 [관리 되는 리소스 속성 페이지](managed-resources-property-page.md)에서 제공 됩니다.

## <a name="preprocessor-definitions"></a>전처리기 정의

리소스 컴파일러에 대 한 정의를 하나 이상 지정 합니다. (/d [macro])

## <a name="undefine-preprocessor-definitions"></a>전처리기 정의 해제

기호 정의를 해제 합니다. /u

## <a name="culture"></a>culture

리소스에 사용 되는 문화권 (예: 미국 영어 또는 이탈리아어)을 나열 합니다. (/l [num])

## <a name="additional-include-directories"></a>추가 포함 디렉터리

포함 경로에 추가할 하나 이상의 디렉터리를 지정 합니다. 두 개 이상 있는 경우 세미콜론 구분 기호를 사용 합니다. (/I [path])

## <a name="ignore-standard-include-paths"></a>표준 포함 경로 무시

리소스 컴파일러가 INCLUDE 환경 변수에 지정 된 디렉터리에서 포함 파일을 검색 하지 않도록 합니다. /X

## <a name="show-progress"></a>진행률 표시

진행 메시지를 출력 창으로 보냅니다. /v

## <a name="suppress-startup-banner"></a>시작 배너 표시 안 함

시작 배너 및 정보 메시지 (/nologo) 표시를 표시 하지 않습니다.

## <a name="resource-file-name"></a>리소스 파일 이름

리소스 파일의 이름을 지정 합니다 (/fo [file]).

## <a name="null-terminate-strings"></a>Null 종료 문자열

문자열 테이블의 모든 문자열에 null을 추가 합니다. /n

## <a name="see-also"></a>참조

[C++ 프로젝트 속성 페이지 참조](property-pages-visual-cpp.md)
