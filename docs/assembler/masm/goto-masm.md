---
description: '자세히 알아보기: GOTO'
title: GOTO (MASM)
ms.date: 12/16/2019
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: ab373d77cbfb660d4cc256e39de38b7f066eac27
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97130262"
---
# <a name="goto"></a>GOTO

_Macrolabel_ **로 표시 된** 줄로 어셈블리를 전송 합니다.

## <a name="syntax"></a>Syntax

> **GOTO** *macrolabel*

## <a name="remarks"></a>설명

**GOTO** 는 [매크로](macro.md), [FOR](for-masm.md), [forc](forc.md), [REPEAT](repeat.md)및 [WHILE](while-masm.md) 블록 내 에서만 사용할 수 있습니다. *Macrolabel* 대상은 줄에서 유일한 지시문 이어야 하며 선행 콜론 뒤에와 야 합니다.

## <a name="see-also"></a>참고 항목

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
