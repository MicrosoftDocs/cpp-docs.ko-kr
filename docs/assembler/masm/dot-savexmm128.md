---
description: 에 대해 자세히 알아보세요. SAVEXMM128
title: .SAVEXMM128
ms.date: 12/17/2019
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: 697598aa5820b029d19da62a817c60455059865e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97131120"
---
# <a name="savexmm128"></a>.SAVEXMM128

`UWOP_SAVE_XMM128` `UWOP_SAVE_XMM128_FAR` 지정 된 XMM 레지스터 및 현재 프롤로그 오프셋을 사용 하 여 오프셋에 대 한 해제 코드 항목을 생성 합니다. MASM은 가장 효율적인 인코딩을 선택 합니다.

## <a name="syntax"></a>Syntax

> **. SAVEXMM128** *xmmreg* , *offset*

## <a name="remarks"></a>설명

**. SAVEXMM128** 를 사용 하면 ml64.exe 사용자는 프레임 함수를 해제 하는 방법을 지정할 수 있으며, 프롤로그 내 에서만 허용 되며, [프로시저](proc.md) 프레임 선언에서로 확장 됩니다 [. ENDPROLOG](dot-endprolog.md) 지시문입니다. 이러한 지시문은 코드를 생성 하지 않습니다. 및만 생성 `.xdata` `.pdata` 합니다. . SAVEXMM128는 해제할 작업을 실제로 구현 하는 지침을 따라야 합니다. 규약을 보장 하기 위해 매크로에서 해제할 해제 지시문과 코드를 모두 래핑하는 것이 좋습니다.

*오프셋* 은 16의 배수 여야 합니다.

자세한 내용은 x [64 용 MASM (ml64.exe)](masm-for-x64-ml64-exe.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
