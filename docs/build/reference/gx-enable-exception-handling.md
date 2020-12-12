---
description: 자세히 알아보기:/GX (예외 처리 사용)
title: /GX(예외 처리 사용)
ms.date: 11/19/2019
f1_keywords:
- /gx
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
ms.openlocfilehash: e511407504129f94b615fb3ec05c9f8a04766b10
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191708"
---
# <a name="gx-enable-exception-handling"></a>/GX(예외 처리 사용)

더 이상 사용되지 않습니다. 를 사용 하 여 선언 된 함수가 예외를 throw 하지 않는다고 가정 하 고 동기 예외 처리를 사용 하도록 설정 `extern "C"` 합니다.

## <a name="syntax"></a>구문

```
/GX
```

## <a name="remarks"></a>설명

**/Gx** 는 사용 되지 않습니다. 대신 해당 [/ehsc](eh-exception-handling-model.md) 옵션을 사용 하십시오. 사용 되지 않는 컴파일러 옵션의 목록은 [컴파일러 옵션 범주별 목록](compiler-options-listed-by-category.md)에서 **사용 되지 않는 컴파일러 옵션** 섹션을 참조 하세요.

기본적으로 **/gx** 와 동일한 **/Ehsc** 는 Visual Studio 개발 환경을 사용 하 여 컴파일할 때 적용 됩니다. 명령줄 도구를 사용 하는 경우 예외 처리가 지정 되지 않습니다. 이는 **/GX-** 에 해당 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. 탐색 창에서 **구성 속성**, **C/c + +**, **명령줄** 을 선택 합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[/EH (예외 처리 모델)](eh-exception-handling-model.md)
