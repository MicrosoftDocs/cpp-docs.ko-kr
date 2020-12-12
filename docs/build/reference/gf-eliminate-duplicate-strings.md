---
description: 자세히 알아보기:/GF (중복 문자열 제거)
title: /GF(중복 문자열 제거)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.StringPooling
- VC.Project.VCCLWCECompilerTool.StringPooling
- /gf
helpviewer_keywords:
- duplicate strings
- Eliminate Duplicate Strings compiler option [C++]
- pooling strings compiler option [C++]
- -GF compiler option [C++]
- /GF compiler option [C++]
- GF compiler option [C++]
- strings [C++], pooling
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
ms.openlocfilehash: 65c8cca610b9e01cf49939c2074a698b00c6e338
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191942"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF(중복 문자열 제거)

컴파일러가 실행 중에 프로그램 이미지와 메모리에 동일한 문자열의 단일 복사본을 만들 수 있도록 합니다. 이는 작은 프로그램을 만들 수 있는 *문자열 풀링* 이라는 최적화입니다.

## <a name="syntax"></a>구문

```
/GF
```

## <a name="remarks"></a>설명

**/Gf** 를 사용 하는 경우 운영 체제는 메모리의 문자열 부분을 바꾸지 않으며 이미지 파일에서 문자열을 다시 읽을 수 있습니다.

**/Gf** 는 문자열을 읽기 전용으로 풀링합니다. **/Gf** 에서 문자열을 수정 하려고 하면 응용 프로그램 오류가 발생 합니다.

문자열 풀링은 여러 버퍼에 대 한 여러 포인터를 단일 버퍼에 대 한 여러 포인터로 사용할 수 있도록 합니다. 다음 코드에서 `s` 및 `t` 는 동일한 문자열을 사용 하 여 초기화 됩니다. 문자열 풀링은 동일한 메모리를 가리키도록 합니다.

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
> 편집 하며 계속 하기에 사용 되는 [/zi](z7-zi-zi-debug-information-format.md) 옵션은 **/gf** 옵션을 자동으로 설정 합니다.

> [!NOTE]
> **/Gf** 컴파일러 옵션은 각 고유 문자열에 대해 주소 지정 가능 섹션을 만듭니다. 기본적으로 개체 파일에는 최대 65536 개의 주소를 지정할 수 있는 섹션이 포함 될 수 있습니다. 프로그램에 65536 개 이상의 문자열이 포함 된 경우 [/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md) 컴파일러 옵션을 사용 하 여 더 많은 섹션을 만듭니다.

**/Gf** 는 [/O1](o1-o2-minimize-size-maximize-speed.md) 또는 [/o1](o1-o2-minimize-size-maximize-speed.md) 를 사용할 때 적용 됩니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **코드 생성** 속성 페이지를 클릭 합니다.

1. **문자열 풀링 사용** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
