---
description: 자세히 알아보기:/GZ (스택 프레임 Run-Time 오류 검사를 사용 하도록 설정)
title: /GZ(스택 프레임 런타임 오류 검사 사용)
ms.date: 11/04/2016
f1_keywords:
- /gz
helpviewer_keywords:
- -GZ compiler option [C++]
- release-build errors
- /GZ compiler option [C++]
- GZ compiler option [C++]
- debug builds, catch release-build errors
ms.assetid: b3efeeff-d5e3-4057-91c9-f6fc73d0270c
ms.openlocfilehash: 0b0936037c265bf57413c458ffc0a831184cb074
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191695"
---
# <a name="gz-enable-stack-frame-run-time-error-checking"></a>/GZ(스택 프레임 런타임 오류 검사 사용)

[/Rtc (런타임 오류 검사)](rtc-run-time-error-checks.md) 옵션과 동일한 작업을 수행 합니다. 더 이상 사용되지 않습니다.

## <a name="syntax"></a>구문

```
/GZ
```

## <a name="remarks"></a>설명

**/GZ** 는 최적화 되지 않은 ([/od (Debug)](od-disable-debug.md)) 빌드 에서만 사용 됩니다.

**/GZ** 는 Visual Studio 2005 이후부터 사용 되지 않습니다. 대신 [/rtc (런타임 오류 검사)를](rtc-run-time-error-checks.md) 사용 합니다. 사용 되지 않는 컴파일러 옵션의 목록은 [컴파일러 옵션 범주별](compiler-options-listed-by-category.md)목록에서 **사용 되지 않는 컴파일러 옵션** 을 참조 하세요.

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
