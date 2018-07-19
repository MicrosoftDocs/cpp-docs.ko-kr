---
title: -Wp64 (64 비트 이식성 문제 검색) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems
- VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems
- /wp64
dev_langs:
- C++
helpviewer_keywords:
- 64-bit compiler [C++], detecting portability problems
- /Wp64 compiler option [C++]
- -Wp64 compiler option [C++]
- Wp64 compiler option [C++]
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 295f2f690cb3c9db17a410cea1f23d04e54b0054
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379174"
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64(64비트 이식성 문제 검색)

이 컴파일러 옵션은 더 이상 사용되지 않습니다. Visual Studio 2013 이전 버전에서는 [__w64](../../cpp/w64.md) 키워드로도 표시된 형식에서 64비트 이식성 문제를 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
/Wp64  
```  
  
## <a name="remarks"></a>설명  

버전의 Visual Studio 2013 이전 Visual Studio는 기본적으로는 **/Wp64** 32 비트 x86를 구축 하는 Visual c + + 컴파일러에서 컴파일러 옵션은 해제 되어 코드에서 Visual c + + 컴파일러에서 작성 하는 64 비트, x64 및 코드입니다.  
  
> [!IMPORTANT]
>  [/Wp64](../../build/reference/wp64-detect-64-bit-portability-issues.md) 컴파일러 옵션 및 [__w64](../../cpp/w64.md) 키워드는 Visual Studio 2010 및 Visual Studio 2012에서 더 이상 사용되지 않으며 Visual Studio 2013부터는 지원되지 않습니다. 이 스위치를 사용하는 프로젝트를 변환하면 변환 중에 스위치가 마이그레이션되지 않습니다. Visual Studio 2010 또는 Visual Studio 2012에서 이 옵션을 사용하려면 프로젝트 속성의 **명령줄** 섹션에서 **추가 옵션** 아래에 컴파일러 스위치를 입력해야 합니다. 명령줄에서 **/Wp64** 컴파일러 옵션을 사용하면 컴파일러에서 명령줄 경고 D9002를 표시합니다. 64비트 이식성 문제를 검색하기 위해 이 옵션과 키워드를 사용하는 대신 64비트 플랫폼을 대상으로 하는 Visual C++ 컴파일러를 사용하고 [/W4](../../build/reference/compiler-option-warning-level.md) 옵션을 지정합니다. 자세한 내용은 참조 [구성 Visual c + + 64 비트 x64 대상](../../build/configuring-programs-for-64-bit-visual-cpp.md)합니다.  
  
다음 유형의 변수는 64비트 운영 체제에서 사용되는 것처럼 32비트 운영 체제에서 테스트됩니다.  
  
-   int  
  
-   long  
  
-   포인터  
  
 64 비트 x64를 구축 하는 컴파일러를 사용 하 여 응용 프로그램을 정기적으로 컴파일하는 경우 코드를 비활성화 하는 것 **/Wp64** 32 비트 컴파일에서는 64 비트 컴파일러가 모든 문제를 검색할 수 있으므로 합니다. 대상 Windows 64 비트 운영 체제 하는 방법에 대 한 자세한 내용은 참조 [구성 Visual c + + 64 비트 x64 대상](../../build/configuring-programs-for-64-bit-visual-cpp.md)합니다.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면  
  
1.  프로젝트 **속성 페이지** 대화 상자를 엽니다.  
  
     자세한 내용은 참조 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)합니다.  
  
2.  **C/C++** 폴더를 클릭합니다.  
  
3.  **명령줄** 속성 페이지를 클릭합니다.  
  
4.  **/Wp64** 를 포함하도록 **추가 옵션**상자의 내용을 수정합니다.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면  
  
-   <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  

[컴파일러 옵션](../../build/reference/compiler-options.md)   
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)   
[64비트, x64 대상을 위한 Visual C++ 구성](../../build/configuring-programs-for-64-bit-visual-cpp.md)