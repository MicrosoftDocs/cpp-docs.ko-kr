---
description: 자세히 알아보기:/Ge (스택 프로브 사용)
title: /Ge(스택 조사 사용)
ms.date: 11/04/2016
f1_keywords:
- /ge
helpviewer_keywords:
- -Ge compiler option [C++]
- enable stack probes
- /Ge compiler option [C++]
- stack, stack probes
- stack probes
- stack checking calls
- Ge compiler option [C++]
ms.assetid: 4b54deae-4e3c-4bfa-95f3-ba23590f7258
ms.openlocfilehash: db996deb1c5b964661e5465fe72cfb0fab93df56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192020"
---
# <a name="ge-enable-stack-probes"></a>/Ge(스택 조사 사용)

지역 변수에 대 한 저장소가 필요한 모든 함수 호출에 대해 스택 프로브를 활성화 합니다.

## <a name="syntax"></a>구문

```
/Ge
```

## <a name="remarks"></a>설명

이 메커니즘은 스택 프로브의 기능을 다시 작성 하는 경우에 유용 합니다. 스택 프로브를 다시 작성 하는 대신 [/Gh (후크 함수 _Penter 사용)](gh-enable-penter-hook-function.md) 를 사용 하는 것이 좋습니다.

[/Gs (스택 검사 호출 제어)](gs-control-stack-checking-calls.md) 는 동일한 효과를 가집니다.

**/Ge** 는 사용 되지 않습니다. Visual Studio 2005부터 컴파일러는 스택 검사를 자동으로 생성 합니다. 사용 되지 않는 컴파일러 옵션의 목록은 [컴파일러 옵션 범주별](compiler-options-listed-by-category.md)목록에서 **사용 되지 않는 컴파일러 옵션** 을 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
