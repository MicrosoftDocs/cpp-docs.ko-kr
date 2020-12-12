---
description: 자세히 알아보기:/Qpa (자동 평행 화 도우미)
title: /Qpar(자동 평행화 도우미)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
ms.openlocfilehash: f0d4264acc4224aaad518f936dcb885d592d3007
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225585"
---
# <a name="qpar-auto-parallelizer"></a>/Qpar(자동 평행화 도우미)

컴파일러의 [자동 평행 화 도우미](../../parallel/auto-parallelization-and-auto-vectorization.md) 기능을 사용 하 여 코드에서 루프를 자동으로 병렬화 합니다.

## <a name="syntax"></a>구문

```
/Qpar
```

## <a name="remarks"></a>설명

컴파일러가 코드에서 루프를 자동으로 평행화하면 계산이 여러 프로세서 코어로 분산됩니다. 컴파일러에서 평행화가 적절하고 평행화를 통해 성능이 향상될 것으로 확인되는 경우에만 루프가 평행화됩니다.

`#pragma loop()` 지시문은 최적화 프로그램이 특정 루프를 평행화하는 데 사용할 수 있습니다. 자세한 내용은 [loop](../../preprocessor/loop.md)를 참조 하세요.

자동 평행 화 도우미에 대 한 출력 메시지를 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 [/Qpar-report (auto-평행 화 도우미 Reporting Level)](qpar-report-auto-parallelizer-reporting-level.md)를 참조 하세요.

### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>Visual Studio에서 /Qpar 컴파일러 옵션을 설정하려면

1. **솔루션 탐색기** 에서 프로젝트의 바로 가기 메뉴를 열고 **속성** 을 선택합니다.

1. **속성 페이지** 대화 상자의 **C/c + +** 에서 **명령줄** 을 선택 합니다.

1. **추가 옵션** 상자에를 입력 `/Qpar` 합니다.

### <a name="to-set-the-qpar-compiler-option-programmatically"></a>프로그래밍 방식으로 /Qpar 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>에 있는 코드 예제를 사용합니다.

## <a name="see-also"></a>참고 항목

[/Q 옵션 (하위 수준 작업)](q-options-low-level-operations.md)<br/>
[/Qpar-report (자동 평행 화 도우미 보고 수준)](qpar-report-auto-parallelizer-reporting-level.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[#pragma loop ()](../../preprocessor/loop.md)<br/>
[Visual Studio의 네이티브 코드 벡터화](/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
