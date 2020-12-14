---
description: 자세히 알아보기:/Zs (구문 검사만 해당)
title: /Zs(구문만 검사)
ms.date: 11/04/2016
f1_keywords:
- /zs
helpviewer_keywords:
- -Zs compiler option [C++]
- Syntax Check Only compiler option
- Zs compiler option
- /Zs compiler option [C++]
ms.assetid: b4b41e6a-3f41-4d09-9cb6-fde5aa2cfecf
ms.openlocfilehash: a4f5e2227104003a637db1d921fd959ea0a11ad7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224298"
---
# <a name="zs-syntax-check-only"></a>/Zs(구문만 검사)

명령줄에서 소스 파일의 구문만 확인 하도록 컴파일러에 지시 합니다.

## <a name="syntax"></a>구문

```
/Zs
```

## <a name="remarks"></a>설명

이 옵션을 사용 하면 출력 파일이 생성 되지 않고 오류 메시지가 표준 출력에 기록 됩니다.

**/Zs** 옵션은 소스 파일을 컴파일 및 연결 하기 전에 구문 오류를 찾고 수정 하는 빠른 방법을 제공 합니다.

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
