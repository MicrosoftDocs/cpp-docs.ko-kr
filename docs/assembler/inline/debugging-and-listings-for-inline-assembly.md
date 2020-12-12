---
description: '자세한 정보: 인라인 어셈블리의 디버깅 및 목록'
title: 인라인 어셈블리의 디버깅 및 목록
ms.date: 08/30/2018
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
ms.openlocfilehash: b4608a0176de5e061d7dc7f15b8758d9bd3a94b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117872"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>인라인 어셈블리의 디버깅 및 목록

**Microsoft 전용**

[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 옵션으로 컴파일하는 경우 인라인 어셈블리 코드가 포함 된 프로그램을 소스 수준 디버거로 디버그할 수 있습니다.

디버거 내에서 C 또는 C++ 및 어셈블리 언어 줄에 중단점을 설정할 수 있습니다. 혼합된 어셈블리 및 소스 모드를 사용하면 어셈블리 코드의 소스와 디스어셈블된 형태를 모두 표시할 수 있습니다.

여러 어셈블리 명령 또는 소스 언어 문을 한 줄에 배치하면 디버깅에 방해가 될 수 있습니다. 소스 모드에서는 디버거를 사용하여 중단점을 한 줄에 설정할 수 있지만 같은 줄의 개별 문에 설정할 수는 없습니다. **`__asm`** 단일 논리 줄로 확장 되는 C 매크로로 정의 된 블록에도 동일한 원칙이 적용 됩니다.

[/FAs](../../build/reference/fa-fa-listing-file.md) 컴파일러 옵션을 사용 하 여 혼합 소스와 어셈블리를 만드는 경우 목록에는 각 어셈블리 언어 줄의 소스 및 어셈블리 형식이 모두 포함 됩니다. 매크로는 목록에서 확장되지 않지만 컴파일 중에는 확장됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__Asm 블록에서 어셈블리 언어 사용](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
