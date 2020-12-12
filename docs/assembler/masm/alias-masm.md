---
description: '자세히 알아보기: 별칭'
title: ALIAS (MASM)
ms.date: 12/17/2019
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: 7d5072cec8ef56f3dd2202617b3274c958a25d66
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97121760"
---
# <a name="alias"></a>ALIAS

**ALIAS** 지시문은 함수에 대 한 대체 이름을 만듭니다.  이를 통해 함수에 대 한 여러 이름을 만들거나 링커 (LINK.exe)가 이전 함수를 새 함수에 매핑할 수 있도록 하는 라이브러리를 만들 수 있습니다.

## <a name="syntax"></a>Syntax

> **앤티앨리어스 \<**_alias_**> = \<**_actual-name_**>**

#### <a name="parameters"></a>매개 변수

*실제 이름*\
함수 또는 프로시저의 실제 이름입니다.  꺾쇠 괄호가 필요 합니다.

*앤티앨리어스*\
대체 또는 별칭 이름입니다.  꺾쇠 괄호가 필요 합니다.

## <a name="see-also"></a>참고 항목

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
