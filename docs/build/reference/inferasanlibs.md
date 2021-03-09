---
description: /INFERASANLIBS (유추 sanitizer 라이브러리 사용) 링커 옵션에 대해 자세히 알아보세요.
title: /INFERASANLIBS (유추 sanitizer 라이브러리 사용)
ms.date: 03/01/2021
f1_keywords:
- /INFERASANLIBS
- /INFERASANLIBS:NO
helpviewer_keywords:
- /INFERASANLIBS [C++]
- address sanitizer [C++] linker option
ms.openlocfilehash: 82337b5b77bab2a9066427662f3fd0956684c636
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471105"
---
# <a name="inferasanlibs-use-inferred-sanitizer-libs"></a>`/INFERASANLIBS` (유추 된 sanitizer 라이브러리 사용)

**`/INFERASANLIBS`** 링커 옵션을 사용 하 여 기본 AddressSanitizer 라이브러리에 대 한 연결을 설정 하거나 해제할 수 있습니다. Visual Studio 2019 16.9에서 유일 하 게 지원 되는 sanitizer는 [AddressSanitizer](../../sanitizers/asan.md)입니다.

## <a name="syntax"></a>구문

> **`/INFERASANLIBS`**\[**`:NO`**]

## <a name="remarks"></a>설명

**`/INFERASANLIBS`** 링커 옵션은 기본 [AddressSanitizer](../../sanitizers/asan.md) 라이브러리를 사용 하도록 설정 합니다. 기본적으로 이 옵션은 사용하도록 설정됩니다.

**`/INFERASANLIBS`** 및 **`/INFERASANLIBS:NO`** 링커 옵션은 고급 사용자에 대 한 지원을 제공 합니다. 자세한 내용은 [AddressSanitizer 빌드 및 언어 참조](../../sanitizers/asan-building.md)를 참조 하세요.

**`/INFERASANLIBS`** 이 옵션은 Visual Studio 2019 버전 16.9부터 사용할 수 있습니다.

### <a name="to-set-the-inferasanlibs-linker-option-in-the-visual-studio-development-environment"></a>**`/INFERASANLIBS`** Visual Studio 개발 환경에서 링커 옵션을 설정 하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다.

1. **구성 속성** > **링커** > **명령줄** 속성 페이지를 선택합니다.

1. **추가 옵션** 속성을 수정 합니다. 기본 라이브러리를 사용 하도록 설정 하려면 편집 상자에 **/INFERASANLIBS** 를 입력 합니다. 기본 라이브러리를 사용 하지 않도록 설정 하려면 **/INFERASANLIBS: NO** 를 대신 입력 합니다.

1. **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)\
[MSVC 링커 옵션](linker-options.md)\
[`/fsanitize` (Sanitizers 사용)](./fsanitize.md)\
[AddressSanitizer 개요](../../sanitizers/asan.md)\
[알려진 문제 AddressSanitizer](../../sanitizers/asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](../../sanitizers/asan-building.md)
