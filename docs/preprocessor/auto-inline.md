---
description: '다음에 대 한 자세한 정보: auto_inline pragma'
title: auto_inline pragma
ms.date: 08/29/2019
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
ms.openlocfilehash: f629bbe5dc47ba15bba5b2b55541509f421fcd8c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301050"
---
# <a name="auto_inline-pragma"></a>auto_inline pragma

**Off** 가 지정 된 범위 내에서 정의 된 모든 함수를 자동 인라인 확장의 후보로 간주 하지 않도록 제외 합니다.

## <a name="syntax"></a>Syntax

> **#pragma auto_inline (** [{ **on**  |  **off** }] **)**

## <a name="remarks"></a>설명

**Auto_inline** pragma를 사용 하려면 함수 정의를 포함 하지 않고 바로 앞과 뒤에 놓습니다. Pragma는 pragma가 표시 된 후 첫 번째 함수 정의가 즉시 적용 됩니다.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
