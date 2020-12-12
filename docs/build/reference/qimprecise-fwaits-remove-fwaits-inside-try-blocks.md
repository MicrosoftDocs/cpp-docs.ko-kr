---
description: 다음에 대 한 자세한 정보:/Qimprecise_fwaits (Try 블록 내의 fwait 제거)
title: /Qimprecise_fwaits(Try 블록 내의 fwait 제거)
ms.date: 11/04/2016
f1_keywords:
- /Qimprecise_fwaits
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
ms.openlocfilehash: 5f3d96656d062a7e5b0c4ad78ba7cd536069e013
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225624"
---
# <a name="qimprecise_fwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits(Try 블록 내의 fwait 제거)

`fwait` **`try`** [/Fp: except](fp-specify-floating-point-behavior.md) 컴파일러 옵션을 사용 하는 경우 블록 내부의 명령을 제거 합니다.

## <a name="syntax"></a>구문

```
/Qimprecise_fwaits
```

## <a name="remarks"></a>설명

이 옵션은 **/fp: except** 가 지정 되지 않은 경우에는 적용 되지 않습니다. **/Fp: except** 옵션을 지정 하면 컴파일러는 `fwait` 블록의 각 코드 줄 주위에 명령을 삽입 합니다 **`try`** . 이러한 방식으로 컴파일러는 예외를 생성 하는 코드의 특정 줄을 식별할 수 있습니다. **/Qimprecise_fwaits** 내부 `fwait` 지침을 제거 하 여 블록 주위의 대기만 남겨 둡니다 **`try`** . 이렇게 하면 성능이 향상 되지만 컴파일러는 **`try`** 예외를 발생 시키는 어떤 줄이 아니라는 블록만 나타낼 수 있습니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/Q 옵션 (하위 수준 작업)](q-options-low-level-operations.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
