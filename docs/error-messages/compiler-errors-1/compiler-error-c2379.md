---
description: '자세한 정보: 컴파일러 오류 C2379'
title: 컴파일러 오류 C2379
ms.date: 11/04/2016
f1_keywords:
- C2379
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
ms.openlocfilehash: 4b278040107a026ffd5f7bee79e709519647cb54
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174717"
---
# <a name="compiler-error-c2379"></a>컴파일러 오류 C2379

승격 시 형식 매개 변수 번호의 형식이 다릅니다.

지정 된 매개 변수의 형식은 이전 선언의 형식과 함께 기본 승격을 통해 호환 되지 않습니다. 이 오류는 ANSI C ([/za](../../build/reference/za-ze-disable-language-extensions.md))의 오류 이며 Microsoft 확장 (**/ze**)을 사용 하는 경고입니다.

다음 샘플에서는 C2379를 생성 합니다.

```c
// C2379.c
// compile with: /Za
void func();
void func(char);   // C2379, char promotes to int
```
