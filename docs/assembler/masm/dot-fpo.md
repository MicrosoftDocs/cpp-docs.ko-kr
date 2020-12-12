---
description: 에 대해 자세히 알아보세요. FPO (32 비트 MASM)
title: .FPO
ms.date: 11/05/2019
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 058189329cbe849086a3b1540ac7883ecac4d026
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97131705"
---
# <a name="fpo-32-bit-masm"></a>. FPO (32 비트 MASM)

**입니다. FPO** 지시문은 디버그 레코드를 debug $ F 세그먼트 또는 섹션으로 내보내기를 제어 합니다. (32 비트 MASM에만 해당)

## <a name="syntax"></a>Syntax

> **. FPO** (*cdwlocals*, *cdwlocals*, *cbprolog*, *cbregs*, *fUseBP*, *cbprolog*)

### <a name="parameters"></a>매개 변수

*cdwLocals*\
지역 변수의 수 이며, 부호 없는 32 비트 값입니다.

*cdwParams*\
DWORD에서 부호 없는 16 비트 값인 매개 변수의 크기입니다.

*cbProlog*\
부호 없는 8 비트 값인 함수 프롤로그 코드의 바이트 수입니다.

*cbRegs*\
숫자 레지스터가 저장 되었습니다.

*fUseBP*\
EBP 레지스터가 할당 되었는지 여부를 나타냅니다. 0 또는 1입니다.

*cbFrame*\
프레임 유형을 나타냅니다.  자세한 내용은 [FPO_DATA](/windows/win32/api/winnt/ns-winnt-fpo_data) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
