---
title: -C (전처리 중에 주석 유지) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- /c
- VC.Project.VCCLWCECompilerTool.KeepComments
dev_langs:
- C++
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8716c0a0f954b0a2ad0bbe0e25c29a4445b11823
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428345"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C(전처리 중에 주석 유지)

전처리하는 동안 주석을 유지합니다.

## <a name="syntax"></a>구문

```
/C
```

## <a name="remarks"></a>설명

이 컴파일러 옵션에 필요 합니다 **/E**, **/P**, 또는 **/EP** 옵션입니다.

다음 코드 샘플에는 소스 코드 주석이 표시 됩니다.

```
// C_compiler_option.cpp
// compile with: /E /C /c
int i;   // a variable
```

이 샘플에는 다음과 같은 출력이 생성 됩니다.

```
#line 1 "C_compiler_option.cpp"
int i;   // a variable
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. **C/C++** 폴더를 클릭합니다.

1. 클릭 합니다 **전처리기** 속성 페이지.

1. 수정 된 **주석 유지** 속성입니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[컴파일러 옵션](../../build/reference/compiler-options.md)<br/>
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)<br/>
[/E(stdout으로 전처리)](../../build/reference/e-preprocess-to-stdout.md)<br/>
[/P(파일로 전처리)](../../build/reference/p-preprocess-to-a-file.md)<br/>
[/EP(#line 지시문 없이 stdout으로 전처리)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)