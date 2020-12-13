---
description: '자세한 정보: 컴파일러 오류 C2449'
title: 컴파일러 오류 C2449
ms.date: 11/04/2016
f1_keywords:
- C2449
helpviewer_keywords:
- C2449
ms.assetid: 544bf0b6-daa0-40e8-9f21-8e583d472a2d
ms.openlocfilehash: cea4218d71b01a5f93b4c9409175449f78e3211f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332454"
---
# <a name="compiler-error-c2449"></a>컴파일러 오류 C2449

파일 범위에 ' {'가 있습니다 (함수 헤더 없음?).

파일 범위에서 여는 중괄호가 발생 합니다.

함수 헤더와 함수 정의의 여는 중괄호 사이에 세미콜론이 있으면이 오류가 발생할 수 있습니다.

다음 샘플에서는 C2499를 생성 합니다.

```c
// C2449.c
// compile with: /c
void __stdcall func(void) {}   // OK
void __stdcall func(void);  // extra semicolon on this line
{                         // C2449 detected here
```
