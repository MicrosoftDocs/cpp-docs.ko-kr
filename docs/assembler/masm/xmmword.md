---
description: '자세한 정보: XMMWORD'
title: XMMWORD
ms.date: 12/17/2019
f1_keywords:
- XMMWORD
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
ms.openlocfilehash: 304ac53a29fa7912107d6d4e87ee6efd3924ac3f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124984"
---
# <a name="xmmword"></a>XMMWORD

MMX 및 SSE (XMM) 명령을 포함 하는 128 비트 멀티미디어 피연산자에 사용 됩니다.

## <a name="syntax"></a>Syntax

> **XMMWORD**

## <a name="remarks"></a>설명

**Xmmword** 는 [__m128](../../cpp/m128.md)와 동일한 형식을 표시 하기 위한 것입니다.

## <a name="example"></a>예제

```asm
    movdqa   xmm0, xmmword ptr [ebx]
```

## <a name="see-also"></a>참고 항목

[MASM BNF 문법](masm-bnf-grammar.md)
