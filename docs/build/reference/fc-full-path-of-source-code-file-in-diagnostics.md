---
description: 자세한 정보:/FC (진단 소스 코드 파일의 전체 경로)
title: /FC(진단 소스 코드 파일의 전체 경로)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
ms.openlocfilehash: 01d1148a32179a7c605a19dc7f2856b7697ae6fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200678"
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC(진단 소스 코드 파일의 전체 경로)

컴파일러가 진단의 컴파일러에 전달 된 소스 코드 파일의 전체 경로를 표시 하도록 합니다.

## <a name="syntax"></a>Syntax

> /FC

## <a name="remarks"></a>설명

다음 코드 샘플을 참조 하세요.

```cpp
// compiler_option_FC.cpp
int main( ) {
   int i   // C2143
}
```

**/Fc** 를 사용 하지 않으면 진단 텍스트가 다음 진단 텍스트와 유사 하 게 표시 됩니다.

- compiler_option_FC .cpp (5): 오류 C2143: 구문 오류: '} ' 앞에 '; '이 없습니다.

**/Fc** 를 사용 하면 진단 텍스트가 다음과 같이 진단 텍스트와 유사 하 게 표시 됩니다.

- c:\test\ compiler_option_fc. .cpp (5): 오류 C2143: 구문 오류: '} ' 앞에 '; '이 없습니다.

또한 &#95;&#95;FILE&#95;&#95; 매크로를 사용할 때 파일 이름의 전체 경로를 확인 하려는 경우에는 **/fc** 가 필요 합니다.  &#95;&#95;파일&#95;&#95;에 대 한 자세한 내용은 [미리 정의 된 매크로](../../preprocessor/predefined-macros.md) 를 참조 하세요.

**/Fc** 옵션은 **/zi** 에 의해 암시 됩니다. **/Zi** 에 대 한 자세한 내용은 [/z7,/zi,/Zi (디버그 정보 형식)](z7-zi-zi-debug-information-format.md)를 참조 하세요.

**/Fc** 는 소문자로 전체 경로를 출력 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **고급** 속성 페이지를 선택 합니다.

1. **전체 경로 사용** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
