---
description: IF1 및 IF2에 대해 자세히 알아보세요.
title: IF1 및 IF2
ms.date: 11/21/2019
f1_keywords:
- IF2
- IF1
helpviewer_keywords:
- IF2 directive
- IF2 directive
ms.assetid: a0f75564-b51b-4e39-ad3b-f7421e7ecad6
ms.openlocfilehash: 427edae687846f19aa281db2b625c8cdf68a1707
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97130197"
---
# <a name="if1-and-if2"></a>IF1 및 IF2

**IF1** 블록은 첫 번째 어셈블리 패스에서 계산 됩니다.

**IF2** 블록은 **SETIF2** 가 **TRUE** 인 경우 모든 어셈블리 pass에서 평가 됩니다.

## <a name="syntax"></a>Syntax

> **IF1;;**

> **IF2;;**

## <a name="remarks"></a>설명

전체 [구문에 대 한 자세한 내용은](if-masm.md) 을 참조 하세요.

5.1 버전의 경우와 달리 MASM 6.1 이상에서는 첫 번째 패스에서 대부분의 작업을 수행 하며, 그런 다음 필요한 만큼 후속 패스를 수행 합니다. 이와 대조적으로 MASM 5.1은 항상 두 개의 소스 패스에서 어셈블합니다. 따라서 MASM 6.1 이상에서 일부 패스 종속 구문을 수정 하거나 삭제 해야 할 수 있습니다.

### <a name="two-pass-directives"></a>Two-Pass 지시문

호환성을 보장 하기 위해 MASM 6.1 이상에서는 두 개의 패스를 참조 하는 5.1 지시문을 지원 합니다. 여기에는가 포함 **됩니다. ERR1**, **. .ERR2**, **IF1**, **IF2**, **ELSEIF1** 및 **ELSEIF2** 입니다. 두 번째 패스 구문의 경우 [SETIF2 옵션](option-masm.md)을 지정 해야 합니다. **옵션 SETIF2** 가 없는 경우 **IF2** 및 **입니다. .ERR2** 지시문을 통해 오류가 발생 합니다.

```output
.ERR2 not allowed : single-pass assembler
```

MASM 6.1 이상에서는 첫 번째 패스 구문을 다르게 처리 합니다. 를 처리 **합니다. ERR1** 지시문 **입니다. ERR** 및 **IF1** 지시문은 **IF** 와 같습니다.

## <a name="see-also"></a>참고 항목

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
