---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4514'
title: 컴파일러 경고(수준 4) C4514
ms.date: 11/04/2016
f1_keywords:
- C4514
helpviewer_keywords:
- C4514
ms.assetid: cdae966a-9cd4-4e31-af30-2a014e68f614
ms.openlocfilehash: 5d0ba77f6e2d2f0288f92994f0daffde36545c27
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241224"
---
# <a name="compiler-warning-level-4-c4514"></a>컴파일러 경고(수준 4) C4514

' function ': 참조 되지 않은 인라인 함수를 제거 했습니다.

최적화 프로그램에서 호출 되지 않은 인라인 함수를 제거 했습니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4514를 생성 합니다.

```cpp
// C4514.cpp
// compile with: /W4
#pragma warning(default : 4514)
class A
{
   public:
      void func()   // C4514, remove the function to resolve
      {
      }
};

int main()
{
}
```
