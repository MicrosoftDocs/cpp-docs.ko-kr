---
description: 자세히 알아보기:/Gy (Function-Level 연결 사용)
title: /Gy(함수 수준 링크 사용)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
ms.openlocfilehash: 3c4136b25001f7f6d6729b9c6089995d1bcd71bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200132"
---
# <a name="gy-enable-function-level-linking"></a>/Gy(함수 수준 링크 사용)

컴파일러가 개별 함수를 패키지된 함수(COMDAT)의 형태로 패키지할 수 있게 합니다.

## <a name="syntax"></a>구문

```
/Gy[-]
```

## <a name="remarks"></a>설명

링커에서는 함수를 Comdat로 별도로 패키지 하 여 DLL 또는 .exe 파일에서 개별 함수를 제외 하거나 순서를 정렬 해야 합니다.

링커 옵션 [/opt (최적화)](opt-optimizations.md) 를 사용 하 여 .exe 파일에서 참조 되지 않은 패키지 함수를 제외할 수 있습니다.

링커 옵션인 [/order (순서 대로 함수 배치)](order-put-functions-in-order.md) 를 사용 하 여 패키지 함수를 .exe 파일에 지정 된 순서로 포함할 수 있습니다.

인라인 함수는 호출로 인스턴스화된 경우 항상 패키지 됩니다. 예를 들어 인라이닝이 off 이거나 함수 주소를 사용 하는 경우와 같이 발생 합니다. 또한 클래스 선언에 정의 된 c + + 멤버 함수는 자동으로 패키지 됩니다. 다른 함수는 그렇지 않습니다. 패키지 함수로 컴파일하려면이 옵션을 선택 해야 합니다.

> [!NOTE]
> 편집 하며 계속 하기에 사용 되는 [/zi](z7-zi-zi-debug-information-format.md) 옵션은 자동으로 **/gy** 옵션을 설정 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **코드 생성** 속성 페이지를 클릭 합니다.

1. **Function-Level 링크 사용** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
