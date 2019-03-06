---
title: /GX(예외 처리 사용)
ms.date: 11/04/2016
f1_keywords:
- /gx
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
ms.openlocfilehash: 4ac2b86c19845a092c743c484ad48d0cd0b6fb35
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416035"
---
# <a name="gx-enable-exception-handling"></a>/GX(예외 처리 사용)

더 이상 사용되지 않습니다. 가정 함수를 사용 하 여 동기 예외 처리를 사용 하 여 선언 하면 `extern "C"` 예외를 throw 하지 않습니다.

## <a name="syntax"></a>구문

```
/GX
```

## <a name="remarks"></a>설명

**/GX** 는 사용 되지 않습니다. 해당 사용 [/EHsc](../../build/reference/eh-exception-handling-model.md) 옵션을 사용 합니다. 사용 되지 않는 컴파일러 옵션의 목록을 참조 하세요. 합니다 **컴파일러 옵션 및 사용 되지 않음** 섹션 [컴파일러 옵션 범주별 목록](../../build/reference/compiler-options-listed-by-category.md)합니다.

기본적으로 **/EHsc**는 해당 **/GX**, Visual Studio 개발 환경을 사용 하 여 컴파일하는 경우 적용 됩니다. 명령줄 도구를 사용 하는 경우 예외 처리 하지 않아도 지정 됩니다. 에 해당 하는 이것이 **/GX-** 합니다.

자세한 내용은 [c + + 예외 처리](../../cpp/cpp-exception-handling.md)합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. 탐색 창에서 선택 **구성 속성**, **C/c + +** 하십시오 **명령줄**합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고자료

[컴파일러 옵션](../../build/reference/compiler-options.md)<br/>
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)<br/>
[/EH(예외 처리 모델)](../../build/reference/eh-exception-handling-model.md)
