---
description: 자세히 알아보기:/LN (MSIL 모듈 만들기)
title: /LN(MSIL 모듈 만들기)
ms.date: 11/04/2016
f1_keywords:
- /LN
helpviewer_keywords:
- -LN compiler option [C++]
- /LN compiler option [C++]
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
ms.openlocfilehash: 63b6f47fe6bef24341d3c19a6ad96ac3808e486e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190922"
---
# <a name="ln-create-msil-module"></a>/LN(MSIL 모듈 만들기)

어셈블리 매니페스트를 출력 파일에 삽입하지 않도록 지정합니다.

## <a name="syntax"></a>구문

```
/LN
```

## <a name="remarks"></a>설명

기본적으로 **/LN** 는 적용 되지 않습니다 (어셈블리 매니페스트가 출력 파일에 삽입 됨).

**/LN** 를 사용 하는 경우 [/Clr (공용 언어 런타임 컴파일)](clr-common-language-runtime-compilation.md) 옵션 중 하나를 사용 해야 합니다.

매니페스트에 어셈블리 메타 데이터가 없는 관리 되는 프로그램을 모듈 이라고 합니다. [/C (링크 없이 컴파일)](c-compile-without-linking.md) 및 **/LN** 를 사용 하 여 컴파일하는 경우 링커 단계에서 [/Noassembly (MSIL 모듈 만들기)](noassembly-create-a-msil-module.md) 를 지정 하 여 출력 파일을 만듭니다.

어셈블리를 빌드하는 구성 요소 기반 접근 방법을 사용 하려는 경우 모듈을 만들 수 있습니다.  즉, 형식을 작성 하 고 모듈로 컴파일할 수 있습니다.  그런 다음 하나 이상의 모듈에서 어셈블리를 생성할 수 있습니다.  모듈에서 어셈블리를 만드는 방법에 대 한 자세한 내용은 [.Netmodule 파일 링커 입력](netmodule-files-as-linker-input.md) 또는 [Al.exe (어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)를 참조 하세요.

모듈의 기본 파일 확장명은 .netmodule입니다.

Visual Studio 2005 이전 릴리스에서는 **/clr: noAssembly** 를 사용 하 여 모듈을 만들었습니다.

MSVC 링커는 .netmodule 파일을 입력으로 사용 하 고 링커에 의해 생성 된 출력 파일은 어셈블리 또는 .netmodule이 되며 링커에 대 한 입력 된 .netmodules에 대 한 런타임 종속성이 없습니다.  자세한 내용은 [링커 입력 파일로 사용하는 .netmodule 파일](netmodule-files-as-linker-input.md)을 참조하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

- 링커 단계에서 [/Noassembly (MSIL 모듈 만들기)](noassembly-create-a-msil-module.md) 를 지정 하 여 출력 파일을 만듭니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- 이 컴파일러 옵션은 프로그래밍 방식으로 변경할 수 없습니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
