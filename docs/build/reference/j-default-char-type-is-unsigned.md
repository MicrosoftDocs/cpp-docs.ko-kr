---
description: 자세한 정보:/J (부호 없는 기본 문자 형식)
title: /J(부호 없는 기본 문자 형식)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
ms.openlocfilehash: 0e6f09a05925fd0248f1e777d578570cd7b44946
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191227"
---
# <a name="j-default-char-type-is-unsigned"></a>/J(부호 없는 기본 문자 형식)

기본 **`char`** 형식을에서로 변경 **`signed char`** **`unsigned char`** 하 고 형식이 **`char`** 형식으로 확장 될 때 0으로 확장 됩니다 **`int`** .

## <a name="syntax"></a>구문

```
/J
```

## <a name="remarks"></a>설명

**`char`** 값이 명시적으로로 선언 된 경우/j 옵션은이 값에 영향을 주지 않으며, **`signed`** 값은 형식으로 확장 될 때 부호가 확장  됩니다 **`int`** .

**/J** 옵션은 `_CHAR_UNSIGNED` `#ifndef` 기본 형식의 범위를 정의 하기 위해 LIMITS 파일의와 함께 사용 되는을 정의 합니다. **`char`**

ANSI C 및 c + +에는 특정 형식의 구현이 필요 하지 않습니다 **`char`** . 이 옵션은 문자 데이터로 작업할 때 궁극적으로 영어가 아닌 언어로 번역 되는 경우에 유용 합니다.

> [!NOTE]
> ATL/MFC에 이 컴파일러 옵션을 사용하면 오류가 생성될 수 있습니다. `_ATL_ALLOW_CHAR_UNSIGNED`를 정의해서 이 오류를 비활성화할 수도 있지만 이 해결 방법은 지원되지 않으며, 항상 작동하지 않을 수도 있습니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. **솔루션 탐색기** 에서 프로젝트의 바로 가기 메뉴를 열고 **속성** 을 선택합니다.

1. 프로젝트 **속성 페이지** 대화 상자의 **구성 속성** 아래에 있는 왼쪽 창에서 **C/c + +** 를 확장 하 고 **명령줄** 을 선택 합니다.

1. **추가 옵션** 창에서 **/j** 컴파일러 옵션을 지정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)
