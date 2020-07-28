---
title: 인라인 어셈블리의 데이터 지시문과 연산자
ms.date: 08/30/2018
helpviewer_keywords:
- data directives [C++]
- __asm keyword [C++], referencing limitations
- MASM (Microsoft Macro Assembler), directives
- directives [C++], MASM
- MASM (Microsoft Macro Assembler), structures
- operators [MASM]
- inline assembly, operators
- inline assembly, data directives
- MASM (Microsoft Macro Assembler), operators
- structures [C++], MASM
ms.assetid: fb7410c7-156a-4131-bcfc-211aa70533e3
ms.openlocfilehash: bcacb0cdd26181da3cf80a582866c1e30567d043
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192355"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>인라인 어셈블리의 데이터 지시문과 연산자

**Microsoft 전용**

블록은 **`__asm`** C 또는 c + + 데이터 형식과 개체를 참조할 수 있지만 MASM 지시문 이나 연산자를 사용 하 여 데이터 개체를 정의할 수는 없습니다. 특히 **,,**, `DW` **DD**, `DQ` , `DT` , 및 `DF` 연산자 `DUP` 또는 **이**를 정의 하는 지시문을 사용할 수 없습니다. MASM 구조체와 레코드도 사용할 수 없습니다. 인라인 어셈블러는 지시문 `STRUC` , `RECORD` , **너비**또는 **마스크**를 허용 하지 않습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__Asm 블록에서 어셈블리 언어 사용](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
