---
description: 자세한 정보:/Zg (함수 프로토타입 생성)
title: /Zg(함수 프로토타입 생성)
ms.date: 11/04/2016
f1_keywords:
- /zg
helpviewer_keywords:
- Zg compiler option [C++]
- /Zg compiler option [C++]
- function prototypes, generate function prototypes compiler option
- -Zg compiler option [C++]
- generate function prototypes compiler option
ms.assetid: c8df1b46-24ff-46f2-8356-e0a144b21dd2
ms.openlocfilehash: ee0bed48f15acae867d344a60a6d42f3b17c7e85
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178877"
---
# <a name="zg-generate-function-prototypes"></a>/Zg(함수 프로토타입 생성)

제거됩니다. 소스 파일에 정의된 각 함수에 대한 함수 프로토타입을 만들지만 소스 파일을 컴파일하지 않습니다.

## <a name="syntax"></a>구문

```
/Zg
```

## <a name="remarks"></a>설명

이 컴파일러 옵션은 더 이상 사용할 수 없습니다. Visual Studio 2015에서 제거 되었습니다. 이 페이지는 이전 버전의 Visual Studio 사용자를 위해 유지 됩니다.

함수 프로토타입에는 함수 반환 형식 및 인수 형식 목록이 포함되어 있습니다. 인수 형식 목록은 함수의 정식 매개 변수 형식에서 만들어집니다. 소스 파일에 이미 있는 모든 함수 프로토타입은 무시됩니다.

프로토타입 목록은 표준 출력에 기록됩니다. 이 목록은 함수의 실제 인수 및 정식 매개 변수가 호환되는지 확인하는 데 유용합니다. 표준 출력을 파일로 리디렉션하여 목록을 저장할 수 있습니다. 그런 다음 **#include** 를 사용하여 함수 프로토타입 목록을 소스 파일의 일부로 만들 수 있습니다. 그러면 컴파일러가 인수 형식 검사를 수행합니다.

**/Zg** 옵션을 사용하고 프로그램에 구조체, 열거형 또는 공용 구조체 형식(또는 이러한 형식에 대한 포인터)이 있는 정식 매개 변수가 포함되는 경우 각 구조체, 열거형 또는 공용 구조체 형식의 선언에 태그(이름)가 있어야 합니다. 다음 샘플에서 태그 이름은 `MyStruct`입니다.

```C
// Zg_compiler_option.c
// compile with: /Zg
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```

**/Zg** 옵션은 visual studio 2005에서 더 이상 사용 되지 않으며 visual studio 2015에서 제거 되었습니다. MSVC 컴파일러는 이전의 C 스타일 코드에 대 한 지원을 제거 했습니다. 사용 되지 않는 컴파일러 옵션의 목록은 [컴파일러 옵션 범주별](compiler-options-listed-by-category.md)목록에서 **사용 되지 않는 컴파일러 옵션** 을 참조 하세요.

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
