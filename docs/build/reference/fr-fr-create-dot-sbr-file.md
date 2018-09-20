---
title: -FR,-Fr (만듭니다. Sbr 파일) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BrowseInformation
- VC.Project.VCCLCompilerTool.BrowseInformation
- /fr
- VC.Project.VCCLCompilerTool.BrowseInformationFile
- VC.Project.VCCLWCECompilerTool.BrowseInformationFile
dev_langs:
- C++
helpviewer_keywords:
- /FR compiler option [C++]
- -FR compiler option [C++]
- FR compiler option [C++]
- symbolic browser information
ms.assetid: 3fd8f88b-3924-4feb-9393-287036a28896
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6afcd4aa8ba2e86d687739bc3891f45f2da5672c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379167"
---
# <a name="fr-fr-create-sbr-file"></a>/FR, /Fr(.Sbr 파일 만들기)

.sbr 파일을 만듭니다.

## <a name="syntax"></a>구문

```
/FR[pathname[\filename]]
/Fr[pathname[\filename]]
```

## <a name="remarks"></a>설명

빌드 프로세스 중 Microsoft Browse Information File Maintenance Utility(BSCMAKE)는 이러한 파일을 사용하여 찾아보기 정보를 표시하는 데 사용되는 .BSC 파일을 만듭니다.

**/FR** 은 전체 기호화된 정보를 사용하여 .sbr 파일을 만듭니다.

**/Fr** 은 지역 변수에 대한 정보 없이.sbr 파일을 만듭니다.

`filename`을 지정하지 않으면 .sbr 파일은 소스 파일과 동일한 기본 이름을 가져옵니다.

**/Fr** 은 사용되지 않습니다. 대신 **/FR** 을 사용하세요. 자세한 내용은 [Compiler Options Listed by Category](../../build/reference/compiler-options-listed-by-category.md)에서 사용되지 않는 컴파일러 옵션을 참조하세요.

> [!NOTE]
>  .sbr 확장명을 변경하지 마세요. BSCMAKE는 해당 확장명을 사용하려면 매개자 파일이 필요합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. 탐색 창에서 **C/C++**, **찾아보기 정보** 속성 페이지를 선택합니다.

1. **찾아보기 정보 파일** 또는 **찾아보기 정보 사용** 속성을 수정합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> 및 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>을 참조하십시오.

## <a name="see-also"></a>참고 항목

[출력 파일(/F) 옵션](../../build/reference/output-file-f-options.md)<br/>
[컴파일러 옵션](../../build/reference/compiler-options.md)<br/>
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)<br/>
[경로 이름 지정](../../build/reference/specifying-the-pathname.md)