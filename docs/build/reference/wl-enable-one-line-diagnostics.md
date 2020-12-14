---
description: 자세히 알아보기:/WL (One-Line 진단 사용)
title: /WL(1줄 진단 사용)
ms.date: 11/04/2016
f1_keywords:
- /wl
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
ms.openlocfilehash: 032f2c41558c1475be5673d4a69de9ff9b09f323
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258865"
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL(1줄 진단 사용)

오류 또는 경고 메시지에 추가 정보를 추가 합니다.

## <a name="syntax"></a>구문

```
/WL
```

## <a name="remarks"></a>설명

C + + 컴파일러의 오류 및 경고 메시지 뒤에는 기본적으로 새 줄에 표시 되는 추가 정보가 표시 될 수 있습니다. 명령줄에서 컴파일하는 경우 오류 또는 경고 메시지에 추가 정보 줄을 추가할 수 있습니다. 이는 빌드 출력을 로그 파일에 캡처한 다음 해당 로그를 처리 하 여 모든 오류와 경고를 찾는 경우에 적합할 수 있습니다. 세미콜론이 추가 줄에서 오류 또는 경고 메시지를 구분 합니다.

모든 오류 및 경고 메시지에 추가 정보 줄이 포함 되어 있는 것은 아닙니다. 다음 코드는 추가 정보 줄을 포함 하는 오류를 생성 합니다. **/WL** 를 사용할 때 효과를 테스트할 수 있습니다.

```cpp
// compiler_option_WL.cpp
// compile with: /WL
#include <queue>
int main() {
   std::queue<int> q;
   q.fromthecontinuum();   // C2039
}
```

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
