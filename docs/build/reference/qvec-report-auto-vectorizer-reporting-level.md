---
description: 자세히 알아보기:/Qvec-report (자동 벡터화 도우미 보고 수준)
title: /Qvec-report(자동 벡터화 도우미 보고 수준)
ms.date: 11/04/2016
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
ms.openlocfilehash: 734dabffa3bf19ecaba42d35d208eb27ec7b2968
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225468"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report(자동 벡터화 도우미 보고 수준)

컴파일러 [자동 벡터화](../../parallel/auto-parallelization-and-auto-vectorization.md) 의 보고 기능을 사용 하도록 설정 하 고 컴파일하는 동안 출력에 대 한 정보 메시지의 수준을 지정 합니다.

## <a name="syntax"></a>구문

```
/Qvec-report:{1}{2}
```

## <a name="remarks"></a>설명

**/Qvec-report: 1**<br/>
벡터화 루프에 대 한 정보 메시지를 출력 합니다.

**/Qvec-report: 2**<br/>
벡터화 및 벡터화 되지 않는 루프에 대 한 정보 메시지를 이유 코드와 함께 출력 합니다.

이유 코드 및 메시지에 대 한 자세한 내용은 [벡터화 및 평행 화 도우미 messages](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)를 참조 하세요.

### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>Visual Studio에서/Qvec-report 컴파일러 옵션을 설정 하려면

1. **솔루션 탐색기** 에서 프로젝트의 바로 가기 메뉴를 열고 **속성** 을 선택합니다.

1. **속성 페이지** 대화 상자의 **C/c + +** 에서 **명령줄** 을 선택 합니다.

1. **추가 옵션** 상자에 또는을 입력 `/Qvec-report:1` `/Qvec-report:2` 합니다.

### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>프로그래밍 방식으로/Qvec-report 컴파일러 옵션을 설정 하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>에 있는 코드 예제를 사용합니다.

## <a name="see-also"></a>참고 항목

[/Q 옵션 (하위 수준 작업)](q-options-low-level-operations.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[Visual Studio의 네이티브 코드 벡터화](/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
