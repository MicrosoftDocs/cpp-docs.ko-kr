---
title: ML 심각한 오류 A1010
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: b3141f8819a33281c70e34bd7772d4475886e557
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312588"
---
# <a name="ml-fatal-error-a1010"></a>ML 심각한 오류 A1010

**일치 하지 않는 블록 중첩:**

시작 블록에 짝이 되는 끝이 없거나, 블록 끝에 일치 하는 시작이 없습니다. 다음 중 하나가 포함 될 수 있습니다.

- 와 같은 상위 수준 지시문 [입니다. 이면](dot-if.md)이 고, 그렇지 않으면 [입니다. ](dot-repeat.md)또는를 반복 [합니다. WHILE](dot-while.md).

- [IF](if-masm.md), [REPEAT](repeat.md)또는 **WHILE**과 같은 조건부 어셈블리 지시문입니다.

- 구조체 또는 공용 구조체 정의입니다.

- 프로시저 정의입니다.

- 세그먼트 정의입니다.

- [POPCONTEXT](popcontext.md) 지시문입니다.

- [If](if-masm.md)와 일치 하지 않는 [ELSE](else-masm.md), [ELSEIF](elseif-masm.md)또는 **ENDIF** 와 같은 조건부 어셈블리 지시문입니다.

## <a name="see-also"></a>참조

[ML 오류 메시지](ml-error-messages.md)
