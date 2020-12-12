---
description: '자세한 정보: 컴파일러 오류 C2218'
title: 컴파일러 오류 C2218
ms.date: 11/04/2016
f1_keywords:
- C2218
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
ms.openlocfilehash: d2761bb822c5a1055974e4a0bcd6011e7f451821
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245527"
---
# <a name="compiler-error-c2218"></a>컴파일러 오류 C2218

> '__vectorcall'은 '/arch:IA32'와 함께 사용할 수 없습니다.

**`__vectorcall`** 호출 규칙은 SSE2 (스트리밍 SIMD 확장 2) 이상을 포함 하는 x86 및 x64 프로세서의 네이티브 코드 에서만 지원 됩니다. 자세한 내용은 [`__vectorcall`](../../cpp/vectorcall.md)를 참조하세요.

이 오류를 해결하려면 컴파일러 옵션을 대상 SSE2, AVX 또는 AVX2 명령 집합으로 변경합니다. 자세한 내용은  [`/arch` (x86)](../../build/reference/arch-x86.md)를 참조하세요.
