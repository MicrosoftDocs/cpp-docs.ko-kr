---
description: '다음에 대 한 자세한 정보: IF'
title: IF (MASM)
ms.date: 12/17/2019
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: 09b4bd09155ef848ad165b4e8b0d3a093ade0008
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97130211"
---
# <a name="if"></a>IF

*Expression1* 가 true (0이 아닌 경우) 또는 *elseifstatements* ( *expression1* 가 false)이 고 *식* 1이 true 인 경우 *ifstatements* 의 어셈블리를 부여 합니다.

## <a name="syntax"></a>Syntax

> *Expression1* **인 경우**\
> *if 문*\
> ⟦**ELSEIF** *식 2*\
> *elseif-문*⟧ \
> ⟦**ELSE**\
> *else 문*⟧ \
> **ENDIF**

## <a name="remarks"></a>설명

다음 지시문은 [ELSEIF](elseif-masm.md): **ELSEIFB**, **ELSEIFDEF**, **ELSEIFDIF**, **ELSEIFDIFI**, **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB** 및 **ELSEIFNDEF** 로 대체 될 수 있습니다. 필요에 따라 이전 식이 false 인 경우 *else 문을* 어셈블합니다. 식은 어셈블리 시간에 계산 됩니다.

## <a name="see-also"></a>참고 항목

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
