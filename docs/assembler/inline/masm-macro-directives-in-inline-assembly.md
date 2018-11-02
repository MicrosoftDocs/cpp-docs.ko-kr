---
title: 인라인 어셈블리의 MASM 매크로 지시문
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 7e1bed782d28a5bf7c934c3f57f50aae70038578
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508929"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>인라인 어셈블리의 MASM 매크로 지시문

**Microsoft 전용**

인라인 어셈블러는 매크로 어셈블러가 아닙니다. MASM 매크로 지시문을 사용할 수 없습니다 (**매크로**, `REPT`합니다 **IRC**를 `IRP`, 및 `ENDM`) 또는 매크로 연산자 (**<>**, **!** , **&** 하십시오 `%`, 및 `.TYPE`). 그러나 `__asm` 블록에 C 전처리기 지시문을 사용할 수 있습니다. 참조 [__asm 블록에서 c + + 또는 C를 사용 하 여](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) 자세한 내용은 합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고자료

[__asm 블록에서 어셈블리 언어 사용](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>