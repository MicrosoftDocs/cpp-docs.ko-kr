---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4205'
title: 컴파일러 경고(수준 4) C4205
ms.date: 11/04/2016
f1_keywords:
- C4205
helpviewer_keywords:
- C4205
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
ms.openlocfilehash: d4a9250ad84f45a9e2ce40e6f103904ce7f8722e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173235"
---
# <a name="compiler-warning-level-4-c4205"></a>컴파일러 경고(수준 4) C4205

비표준 확장이 사용 됨: 함수 범위에 정적 함수 선언이 있습니다.

Microsoft 확장 (/Ze)을 사용 하면 **`static`** 다른 함수 내에서 함수를 선언할 수 있습니다. 함수는 전역 범위를 제공 합니다.

## <a name="example"></a>예제

```c
// C4205.c
// compile with: /W4
void func1()
{
   static int func2();  // C4205
};

int main()
{
}
```

이러한 초기화는 ANSI 호환성 ([/za](../../build/reference/za-ze-disable-language-extensions.md))에서 유효 하지 않습니다.
