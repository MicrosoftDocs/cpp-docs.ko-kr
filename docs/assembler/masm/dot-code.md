---
description: 에 대해 자세히 알아보세요. CODE
title: .CODE
ms.date: 12/17/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 3f47b3bf9f345ae39f68b1b21e8f3807f554ea2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132278"
---
# <a name="code"></a>.CODE

(32 비트 MASM에만 해당) 과 함께 사용 [됩니다. MODEL](dot-model.md)-코드 세그먼트의 시작을 나타냅니다.

## <a name="syntax"></a>Syntax

> **. CODE** ⟦*name*⟧ \
> ⟦ *segmentItem* ⟧ ...
> ⟦ *codesegmentnameId* **end**;; ⟧\

### <a name="parameters"></a>매개 변수

*이름의*\
코드 세그먼트의 이름을 지정 하는 선택적 매개 변수입니다. 기본 이름은 소형, 소형, 소형 및 플랫 [모델](dot-model.md)에 **_TEXT** 됩니다. 다른 모델에 대 한 기본 이름은 *modulename* _TEXT입니다.

## <a name="see-also"></a>참고 항목

[지시문 참조](directives-reference.md)\
[. 데이터로](dot-data.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
