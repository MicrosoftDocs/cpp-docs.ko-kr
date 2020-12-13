---
description: '자세한 정보: EXTERN'
title: EXTERN (MASM)
ms.date: 12/06/2019
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 354a390a16fb663dc6e907e37022a362c3ab5648
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97130353"
---
# <a name="extern"></a>EXTERN

형식이 *형식인* *name* 이라는 외부 변수, 레이블 또는 기호를 하나 이상 정의 합니다.

## <a name="syntax"></a>Syntax

> **EXTERN** ⟦*language-type*⟧ *name* ⟦ __(__*altid*__)__ ⟧ __:__ *type* ⟦__,__ ⟦*language-type*⟧ *name* ⟦ __(__*altid*__)__ ⟧ __:__ *type* ... ⟧

## <a name="remarks"></a>설명

*언어 형식* 인수는 32 비트 MASM 에서만 유효 합니다.

*형식은* *이름* 을 상수로 가져오는 [ABS](operator-abs.md)일 수 있습니다. [Extrn](extrn.md)과 동일 합니다.

## <a name="see-also"></a>참고 항목

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
