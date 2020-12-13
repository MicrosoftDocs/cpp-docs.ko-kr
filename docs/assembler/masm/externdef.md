---
description: '자세히 알아보기: EXTERNDEF'
title: EXTERNDEF
ms.date: 12/06/2019
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: b0ffc2154996fc7cea9f0b61917cadf7b776972f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97130327"
---
# <a name="externdef"></a>EXTERNDEF

형식이 *형식인* *name* 이라는 외부 변수, 레이블 또는 기호를 하나 이상 정의 합니다.

## <a name="syntax"></a>Syntax

> **EXTERNDEF** ⟦*⟧* *name*__:__ type ⟦__,__ ⟦*language-type*⟧ *name*__:__*type* ... ⟧

## <a name="remarks"></a>설명

*언어 형식* 인수는 32 비트 MASM 에서만 유효 합니다.

*Name* 이 모듈에 정의 된 경우 [PUBLIC](public-masm.md)으로 처리 됩니다. 모듈에서 *이름이* 참조 되 면 [EXTERN](extern-masm.md)으로 처리 됩니다. *이름을* 참조 하지 않으면 무시 됩니다. *형식은* *이름* 을 상수로 가져오는 [ABS](operator-abs.md)일 수 있습니다. 일반적으로 포함 파일에 사용 됩니다.

## <a name="see-also"></a>참고 항목

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
