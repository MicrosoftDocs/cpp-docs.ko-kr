---
description: 자세한 정보:/Zo (최적화 된 디버깅 향상)
title: /Zo(최적화된 디버깅 향상)
ms.date: 11/04/2016
f1_keywords:
- -Zo
- /Zo
helpviewer_keywords:
- Zo compiler option [C++]
- /Zo compiler option [C++]
- -Zo compiler option [C++]
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
ms.openlocfilehash: b2d5fb37205a6cf58492d7e6bc9080867ebacf54
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224350"
---
# <a name="zo-enhance-optimized-debugging"></a>/Zo(최적화된 디버깅 향상)

디버그되지 않은 빌드에서 최적화된 코드에 대해 향상된 디버깅 정보를 생성합니다.

## <a name="syntax"></a>구문

```cpp
/Zo[-]
```

## <a name="remarks"></a>설명

**/Zo** 컴파일러 스위치는 최적화 된 코드에 대 한 향상 된 디버깅 정보를 생성 합니다. 최적화는 지역 변수에 레지스터를 사용하고 코드를 다시 정렬하며 루프를 벡터화하고 인라인 함수 호출을 수행할 수 있습니다. 이와 같이 최적화를 수행하면 소스 코드와 컴파일된 개체 코드 간 관계가 명확하지 않을 수 있습니다. **/Zo** 스위치는 지역 변수 및 인라인 함수에 대 한 추가 디버깅 정보를 생성 하도록 컴파일러에 지시 합니다. Visual Studio 디버거에서 최적화 된 코드를 단계별로 실행 하는 경우 **자동**, **지역** 및 **조사식** 창에서 변수를 확인 하는 데 사용 합니다. 또한 스택 추적을 설정하여 WinDBG 디버거에 인라인된 함수를 표시할 수도 있습니다. 최적화를 사용 하지 않도록 설정 된 ([/od](od-disable-debug.md)) 디버그 빌드에는 **/zo** 가 지정 될 때 생성 되는 추가 디버깅 정보가 필요 하지 않습니다. **/Zo** 스위치를 사용 하 여 최적화가 설정 된 릴리스 구성을 디버그할 수 있습니다. 최적화 스위치에 대 한 자세한 내용은 [/O 옵션 (코드 최적화)](o-options-optimize-code.md)을 참조 하세요. **/Zi** 또는 **/zo** 을 사용 하 여 디버깅 정보를 지정 하는 경우 Visual Studio에서 **/zo** 옵션은 기본적으로 사용 하도록 설정 됩니다. 이 컴파일러 옵션을 명시적으로 사용 하지 않도록 설정 하려면 **/Zo-** 를 지정 하십시오.

**/Zo** 스위치는 Visual Studio 2013 업데이트 3부터 사용할 수 있으며 이전에 문서화 되지 않은 **/d2Zi +** 스위치를 대체 합니다.

### <a name="to-set-the-zo-compiler-option-in-visual-studio"></a>Visual Studio에서 /Zo 컴파일러 옵션을 설정하려면

1. 프로젝트에 대한 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성**, **C/C++** 폴더를 선택합니다.

1. **명령줄** 속성 페이지를 선택 합니다.

1. 포함 하도록 **추가 옵션** 속성을 수정한 `/Zo` 다음 **확인** 을 선택 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/O 옵션 (코드 최적화)](o-options-optimize-code.md)<br/>
[/Z7,/Zi,/ZI (디버그 정보 형식)](z7-zi-zi-debug-information-format.md)<br/>
[편집하며 계속하기](/visualstudio/debugger/edit-and-continue)
