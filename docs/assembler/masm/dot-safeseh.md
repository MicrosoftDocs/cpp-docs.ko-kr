---
title: .SAFESEH
ms.date: 11/05/2019
f1_keywords:
- .SAFESEH
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
ms.openlocfilehash: 5953ad6bdf1d9d1b0070ce83dd1d764799b7440a
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317567"
---
# <a name="safeseh-32-bit-masm"></a>. SAFESEH (32 비트 MASM)

함수를 구조화 된 예외 처리기로 등록 합니다. (32 비트 MASM에만 해당)

## <a name="syntax"></a>구문

> **. SAFESEH** *식별자*

## <a name="remarks"></a>주의

*식별자* 는 로컬로 정의 된 [Proc](proc.md) 또는 [extrn](extrn.md) PROC의 ID 여야 합니다. [레이블은](label-masm.md) 허용 되지 않습니다. 여. SAFESEH 지시문을 사용 하려면 [/safeseh](ml-and-ml64-command-line-reference.md) ml 명령줄 옵션이 필요 합니다.

구조적 예외 처리기에 대 한 자세한 내용은 [/safeseh](../../build/reference/safeseh-image-has-safe-exception-handlers.md)를 참조 하십시오.

예를 들어 안전한 예외 처리기를 등록 하려면 다음과 같이 새 MASM 파일을 만들고,/safeseh를 사용 하 여 어셈블한 다음 연결 된 개체에 추가 합니다.

```asm
.386
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>참조

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
