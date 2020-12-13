---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4670'
title: 컴파일러 경고(수준 4) C4670
ms.date: 11/04/2016
f1_keywords:
- C4670
helpviewer_keywords:
- C4670
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
ms.openlocfilehash: c1d0f81f10fe63882987d660e4b9099f4ff895ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134032"
---
# <a name="compiler-warning-level-4-c4670"></a>컴파일러 경고(수준 4) C4670

'identifier': 기본 클래스에 액세스할 수 없습니다.

블록에서 throw 되는 개체의 지정 된 기본 클래스에 **`try`** 액세스할 수 없습니다. Throw되는 경우 개체를 인스턴스화할 수 없습니다. 기본 클래스가 올바른 액세스 지정자와 함께 상속되는지 확인합니다.

다음 샘플에서는 C4670을 생성합니다.

```cpp
// C4670.cpp
// compile with: /EHsc /W4
class A
{
};

class B : /* public */ A
{
} b;   // inherits A with private access by default

int main()
{
    try
    {
       throw b;   // C4670
    }
    catch( B )
    {
    }
}
```
