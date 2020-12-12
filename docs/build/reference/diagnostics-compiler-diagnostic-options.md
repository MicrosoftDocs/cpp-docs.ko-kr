---
description: 자세히 알아보기:/diagnostics (컴파일러 진단 옵션)
title: /di (컴파일러 진단 옵션)
ms.date: 11/11/2016
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 2c34edc0374e59720eb05e97379702833efaa703
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201419"
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/di (컴파일러 진단 옵션)

**/진단** 컴파일러 옵션을 사용 하 여 오류 및 경고 위치 정보의 표시를 지정할 수 있습니다.

## <a name="syntax"></a>구문

```
/diagnostics:{caret|classic|column}
```

## <a name="remarks"></a>설명

이 옵션은 Visual Studio 2017 이상에서 지원 됩니다.

**/Snos** 컴파일러 옵션은 오류 및 경고 정보의 표시를 제어 합니다.

**/Cdiagnostics: 클래식** 옵션은 문제가 발견 된 줄 번호를 보고 하는 기본값입니다.

**/Sdiagnostics: 열** 옵션에는 문제가 발견 된 열도 포함 됩니다. 이를 통해 문제의 원인이 되는 특정 언어 구문 또는 문자를 식별할 수 있습니다.

**/Cdiagnostics: 캐럿** 옵션에는 문제가 발견 된 열이 포함 되며, 문제가 검색 된 코드 줄의 위치 아래에 캐럿 (^)이 배치 됩니다.

경우에 따라 컴파일러는 발생 한 문제를 검색 하지 않습니다. 예를 들어, 다른 예기치 않은 기호가 발견 될 때까지 누락 된 세미콜론이 검색 되지 않을 수 있습니다. 열이 보고 되 고 컴파일러가 잘못 된 것을 발견 한 것으로 감지 된 캐럿이 배치 됩니다.

**/Sics** 옵션은 Visual Studio 2017부터 사용할 수 있습니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다.

1. **구성 속성** 에서 **C/c + +** 폴더를 확장 하 고 **일반** 속성 페이지를 선택 합니다.

1. 진단 **형식** 필드에서 드롭다운 컨트롤을 사용 하 여 진단 표시 옵션을 선택 합니다. **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
