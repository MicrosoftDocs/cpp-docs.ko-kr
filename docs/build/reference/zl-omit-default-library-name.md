---
description: 자세히 알아보기:/Zl (기본 라이브러리 이름 생략)
title: /Zl(기본 라이브러리 이름 생략)
ms.date: 11/04/2016
f1_keywords:
- /zl
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
ms.openlocfilehash: eaf39b7bfe1a2b7f2d2c7754cccf8061543e4c7c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224428"
---
# <a name="zl-omit-default-library-name"></a>/Zl(기본 라이브러리 이름 생략)

.Obj 파일에서 기본 C 런타임 라이브러리 이름을 생략 합니다. 기본적으로 컴파일러는 올바른 라이브러리로 링커를 보내기 위해 라이브러리 이름을 .obj 파일에 넣습니다.

## <a name="syntax"></a>구문

```
/Zl
```

## <a name="remarks"></a>설명

기본 라이브러리에 대 한 자세한 내용은 [Use Run-Time library](md-mt-ld-use-run-time-library.md)를 참조 하세요.

**/Zl** 을 사용 하 여 라이브러리에 넣으려는 .obj 파일을 컴파일할 수 있습니다. 라이브러리 이름을 생략 하면 단일 .obj 파일의 공간만 저장 되지만, 저장 된 총 공간은 많은 개체 모듈을 포함 하는 라이브러리에서 중요 합니다.

이 옵션은 고급 옵션입니다. 이 옵션을 설정 하면 응용 프로그램에 필요할 수 있는 특정 C 런타임 라이브러리 지원이 제거 되므로 응용 프로그램이이 지원에 종속 되는 경우 링크 타임 오류가 발생 합니다. 이 옵션을 사용 하는 경우 다른 방법으로 필요한 구성 요소를 제공 해야 합니다.

[/Nodefaultlib (라이브러리 무시)](nodefaultlib-ignore-libraries.md)를 사용 합니다. 모든 .obj 파일에서 라이브러리 참조를 무시 하도록 링커에 지시 합니다.

자세한 내용은 [CRT 라이브러리 기능](../../c-runtime-library/crt-library-features.md)을 참조하세요.

**/Zl** 로 컴파일하는 경우 `_VC_NODEFAULTLIB` 이 정의 됩니다.  예를 들어:

```cpp
// vc_nodefaultlib.cpp
// compile with: /Zl
void Test() {
   #ifdef _VC_NODEFAULTLIB
      int i;
   #endif

   int i;   // C2086
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **고급** 속성 페이지를 클릭 합니다.

1. **기본 라이브러리 이름 생략** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
