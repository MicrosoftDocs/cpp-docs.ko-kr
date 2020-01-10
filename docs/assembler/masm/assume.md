---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: a74a5336e626f561f1fc61e866792ce193332d84
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316540"
---
# <a name="assume"></a>ASSUME

레지스터 값에 대 한 오류 검사를 사용 하도록 설정 합니다. (32 비트 MASM에만 해당)

## <a name="syntax"></a>구문

> *Segregister* __:__ *name* ⟦ __,__ *segregister* __:__ *name*... ⟧\
> *Dataregister*를 가정__합니다. ⟦__ __,__ *dataregister* __:__ *type*... ⟧\
> *레지스터* __: error__ ⟦ __,__ *register* __: error__...를 가정 합니다. ⟧\
> ⟦*Register* __:__ ⟧**NOTHING** ⟦ __,__ *register* __: nothing__...을 **가정** 합니다. ⟧

## <a name="remarks"></a>주의

**가정을** 적용 한 후에는 어셈블러가 지정 된 레지스터의 값에 대 한 변경 내용을 감시 합니다. 레지스터를 사용 하는 경우 **오류** 를 생성 합니다. 등록 오류 검사를 제거 하지 **않습니다** . 한 문에서 여러 종류의 가정을 조합할 수 있습니다.

## <a name="see-also"></a>참조

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
