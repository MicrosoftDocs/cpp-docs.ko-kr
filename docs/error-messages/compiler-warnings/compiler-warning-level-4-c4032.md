---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4032'
title: 컴파일러 경고 (수준 4) C4032
ms.date: 11/04/2016
f1_keywords:
- C4032
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
ms.openlocfilehash: 1c150bff398bbd2d6e5f1a8d21211f4c6b4cb6bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262102"
---
# <a name="compiler-warning-level-4-c4032"></a>컴파일러 경고 (수준 4) C4032

' number ' 형식 매개 변수의 형식이 서로 다릅니다.

매개 변수 형식은 기본 프로 모션을 통해 이전 선언의 형식과 호환 되지 않습니다.

이 오류는 ANSI C ([/za](../../build/reference/za-ze-disable-language-extensions.md))의 오류 이며 Microsoft 확장 (/ze)에서 경고가 발생 합니다.

## <a name="example"></a>예제

```c
// C4032.c
// compile with: /W4
void func();
void func(char);   // C4032, char promotes to int

int main()
{
}
```
