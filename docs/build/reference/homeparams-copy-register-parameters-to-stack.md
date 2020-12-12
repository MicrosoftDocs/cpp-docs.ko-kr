---
description: 자세히 알아보기:/homeparams (스택에 레지스터 매개 변수 복사)
title: /homeparams(스택에 레지스터 매개 변수 복사)
ms.date: 12/17/2018
f1_keywords:
- /homeparams
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
ms.openlocfilehash: 52145534121831be256c3db2a6ccacdffb30b2c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191474"
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/homeparams(스택에 레지스터 매개 변수 복사)

레지스터에 전달 된 매개 변수를 함수 시작 시 스택의 해당 위치에도 기록 합니다.

## <a name="syntax"></a>Syntax

> **/homeparams**

## <a name="remarks"></a>설명

이 컴파일러 옵션은 x64를 대상으로 하는 네이티브 및 크로스 컴파일러 에서만 사용할 수 있습니다.

X64 호출 규칙에는 레지스터에 전달 된 매개 변수를 포함 하 여 모든 매개 변수에 대해 스택 공간을 할당 해야 합니다. 자세한 내용은 [매개 변수 전달](../../build/x64-calling-convention.md#parameter-passing)을 참조 하세요. 기본적으로 등록 매개 변수는 릴리스 빌드에서 할당 된 스택 공간에 복사 되지 않습니다. 이렇게 하면 프로그램의 최적화 된 릴리스 빌드를 디버그 하기가 어려워집니다.

릴리스 빌드의 경우 **/homeparams** 옵션을 사용 하 여 컴파일러가 응용 프로그램을 디버그할 수 있도록 레지스터 매개 변수를 스택에 강제로 복사 하도록 할 수 있습니다. **/homeparams** 는 스택에 레지스터 매개 변수를 로드 하는 데 추가 주기가 필요 하기 때문에 성능상의 단점을 의미 합니다.

디버그 빌드에서 스택에는 항상 레지스터에 전달 된 매개 변수가 채워집니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 엽니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
