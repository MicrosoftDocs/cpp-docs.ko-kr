---
description: /Sfsanitroros (sanitizers 사용) 컴파일러 옵션에 대 한 자세한 정보
title: /sfsanitana (sanitizers 사용)
ms.date: 02/24/2021
f1_keywords:
- /fsanitize
- -fsanitize
- /fsanitize=address
- /fsanitize-address-use-after-return
- -fsanitize-address-use-after-return
- /fno-sanitize-address-vcasan-lib
- -fno-sanitize-address-vcasan-lib
helpviewer_keywords:
- /fsanitize [C++]
- -fsanitize=address [C++]
- address sanitizer compiler option [C++]
- /fsanitize-address-use-after-return
- /fno-sanitize-address-vcasan-lib
ms.openlocfilehash: 820d39e54db29a5e06d119cbefc8a1980447e8cc
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471101"
---
# <a name="fsanitize-enable-sanitizers"></a>`/fsanitize` (Sanitizers 사용)

**`/fsanitize`** 컴파일러 옵션을 사용 하 여 sanitizers를 사용 하도록 설정 합니다. Visual Studio 2019 16.9에서 유일 하 게 지원 되는 sanitizer는 [AddressSanitizer](../../sanitizers/asan.md)입니다.

## <a name="syntax"></a>구문

> **`/fsanitize=address`**\
> **`/fsanitize-address-use-after-return`**\
> **`/fno-sanitize-address-vcasan-lib`**

## <a name="remarks"></a>설명

**`/fsanitize=address`** 컴파일러 옵션을 사용 하면 강력한 컴파일러 및 런타임 기술인 [AddressSanitizer](../../sanitizers/asan.md)을 통해 강력한 [버그를 찾을](../../sanitizers/asan.md#error-types)수 있습니다.

**`/fsanitize-address-use-after-return`** 및 **`/fno-sanitize-address-vcasan-lib`** 컴파일러 옵션과 [ `/INFERASANLIBS` (유추 된 sanitizer 라이브러리 사용)](./inferasanlibs.md) 및 **`/INFERASANLIBS:NO`** 링커 옵션은 고급 사용자에 대 한 지원을 제공 합니다. 자세한 내용은 [AddressSanitizer 빌드 및 언어 참조](../../sanitizers/asan-building.md)를 참조 하세요.

**`/fsanitize`** 이 옵션은 Visual Studio 2019 버전 16.9부터 사용할 수 있습니다.

### <a name="to-set-the-fsanitizeaddress-compiler-option-in-the-visual-studio-development-environment"></a>**`/fsanitize=address`** Visual Studio 개발 환경에서 컴파일러 옵션을 설정 하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다.

1. **구성 속성** > **C/C++**  > **일반** 속성 페이지를 선택합니다.

1. **Enable Address Sanitizer** 속성을 수정 합니다. 사용 하도록 설정 하려면 **예 (/sfsanitrod = address)** 를 선택 합니다.

1. **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

### <a name="to-set-the-advanced-compiler-options"></a>고급 컴파일러 옵션을 설정 하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **/Fsanitize-address-use-after-return** 또는 **/fno-sanitize-address-vcasan-lib** 를 설정 하도록 **추가 옵션** 속성을 수정 합니다.

1. **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)\
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)\
[`/INFERASANLIBS` (유추 된 sanitizer 라이브러리 사용)](./inferasanlibs.md)\
[AddressSanitizer 개요](../../sanitizers/asan.md)\
[알려진 문제 AddressSanitizer](../../sanitizers/asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](../../sanitizers/asan-building.md)
