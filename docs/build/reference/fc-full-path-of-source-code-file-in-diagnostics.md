---
title: -FC (진단 소스 코드 파일의 전체 경로) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
dev_langs:
- C++
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a721b6887b6c5c07d96a79b06f05e6d7855250b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373207"
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC(진단 소스 코드 파일의 전체 경로)

컴파일러가 컴파일러 진단에 전달 된 소스 코드 파일의 전체 경로를 표시 합니다.

## <a name="syntax"></a>구문

> /FC

## <a name="remarks"></a>설명

다음 코드 예제를 고려해 야 합니다.

```cpp
// compiler_option_FC.cpp
int main( ) {
   int i   // C2143
}
```

없이 **/FC**, 진단 텍스트 진단 텍스트 유사 합니다.

- compiler_option_FC.cpp(5): 오류 C2143: 구문 오류: 없습니다. ';' 하기 전에 '을 (를) '

와 **/FC**, 진단 텍스트 진단 텍스트 유사 합니다.

- c:\test\compiler_option_fc.cpp(5): 오류 C2143: 구문 오류: 없습니다. ';' 하기 전에 '을 (를) '

 **/FC** 이 사용 하는 경우에 파일 이름의 전체 경로 표시 하려는 경우 필요는 &#95; &#95;파일&#95; &#95; 매크로입니다. 참조 [미리 정의 된 매크로](../../preprocessor/predefined-macros.md) 대 한 자세한 내용은 &#95; &#95;파일&#95;&#95;합니다.

**/FC** 옵션 암시 **/ZI**합니다. 에 대 한 자세한 내용은 **/ZI**, 참조 [/Z7, /Zi, /ZI (디버깅 정보 형식)](../../build/reference/z7-zi-zi-debug-information-format.md)합니다.

**/FC** 소문자로 전체 경로 출력 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 참조 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)합니다.

1. 선택 된 **구성 속성** > **C/c + +** > **고급** 속성 페이지.

1. 수정 된 **전체 경로 사용** 속성입니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[컴파일러 옵션](../../build/reference/compiler-options.md)   
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)
