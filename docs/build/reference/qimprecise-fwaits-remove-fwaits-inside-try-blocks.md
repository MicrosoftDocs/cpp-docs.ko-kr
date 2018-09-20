---
title: -Qimprecise_fwaits (Try 블록 내의 fwait 제거) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Qimprecise_fwaits
dev_langs:
- C++
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cad23ebdd2289791b50b0e956368b934fe0f1087
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385198"
---
# <a name="qimprecisefwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits(Try 블록 내의 fwait 제거)

제거 합니다 `fwait` 내부 명령을 `try` 사용 하는 경우 차단 합니다 [/fp: 제외 하 고](../../build/reference/fp-specify-floating-point-behavior.md) 컴파일러 옵션입니다.

## <a name="syntax"></a>구문

```
/Qimprecise_fwaits
```

## <a name="remarks"></a>설명

하는 경우이 옵션은 효과가 없습니다 **/fp: 제외한** 도 지정 하지 않으면. 지정 하는 경우는 **/fp: 제외 하 고** 컴파일러는 삽입 옵션을는 `fwait` 명령을 각 줄의 코드 주위를 `try` 블록입니다. 컴파일러는 이러한 방식으로 예외를 생성 하는 코드의 특정 줄을 식별할 수 있습니다. **/Qimprecise_fwaits** 제거 내부 `fwait` 지침을 관련 대기만 종료를 `try` 블록. 성능 향상이 되지만 컴파일러를 말할 수 있는 수만 `try` 블록 하면 예외가 줄 없습니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. **C/C++** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/Q 옵션(하위 수준 작업)](../../build/reference/q-options-low-level-operations.md)<br/>
[컴파일러 옵션](../../build/reference/compiler-options.md)<br/>
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)