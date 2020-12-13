---
description: '자세히 알아보기: 매크로'
title: MACRO
ms.date: 12/16/2019
f1_keywords:
- MACRO
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
ms.openlocfilehash: 5410357e76d28cddd54f3c90a34d3e85b8629143
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97129742"
---
# <a name="macro"></a>MACRO

매크로 블록을 *이름* 이라고 표시 하 고 매크로가 호출 될 때 전달 되는 인수에 대 한 *매개 변수* 자리 표시자를 설정 합니다.

## <a name="syntax"></a>Syntax

> *name***매크로** ⟦*parameter* ⟦**: 필수** | : =*기본*  |  *인수* **: VARARG**⟧ ... ⟧\  
> *할당문*\
⟦**GOTO** :*macrolabelId*⟧ \
> ⟦**Exitm**⟧ \
> **Endm** ⟦*값*⟧

## <a name="remarks"></a>설명

매크로 함수는 호출 하는 문에 *값* 을 반환 합니다.

## <a name="see-also"></a>참고 항목

[지시문 참조](directives-reference.md)\
[GOTO (MASM)](goto-masm.md)\
[ENDM](endm.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
