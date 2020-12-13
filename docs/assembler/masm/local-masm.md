---
description: '다음에 대 한 자세한 정보: 로컬'
title: LOCAL (MASM)
ms.date: 12/16/2019
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: 27296f69b62de0dcd314b2575f045e06576bbf64
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97129755"
---
# <a name="local"></a>LOCAL

첫 번째 지시문의 매크로 내에서 **로컬** 은 매크로의 각 인스턴스에 고유한 레이블을 정의 합니다.

## <a name="syntax"></a>Syntax

> **로컬** *LocalId* ⟦, *localId* ... ⟧
>
> **LOCAL** *labelId* ⟦ __\[__ *count*__]__ ⟧ ⟦__:__*qualifiedType*⟧ ⟦__,__ *labelId* ⟦ __\[__ *count*__]__ ⟧ ⟦*qualifiedType*⟧ ... ⟧

## <a name="remarks"></a>설명

두 번째 지시문의 프로시저 정의 (**PROC**) 내에서 **로컬** 은 프로시저 기간 동안 존재 하는 스택 기반 변수를 만듭니다. *LabelId* 는 단순 변수 이거나 *count* 요소를 포함 하는 배열 일 수 있습니다. 여기서 *count* 는 상수 식입니다.

## <a name="see-also"></a>참고 항목

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
