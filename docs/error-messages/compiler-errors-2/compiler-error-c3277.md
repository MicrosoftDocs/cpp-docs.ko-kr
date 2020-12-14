---
description: '자세한 정보: 컴파일러 오류 C3277'
title: 컴파일러 오류 C3277
ms.date: 11/04/2016
f1_keywords:
- C3277
helpviewer_keywords:
- C3277
ms.assetid: 8ac5f476-e30c-4879-92c6-f03cdbd74045
ms.openlocfilehash: ca04074dd077c63355f7da9a6a5feabcc0d03fac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228991"
---
# <a name="compiler-error-c3277"></a>컴파일러 오류 C3277

관리 되는 ' type ' 내에서 관리 되지 않는 ' enum ' 열거형을 정의할 수 없습니다.

열거형이 관리 되는 형식 내에서 잘못 정의 되었습니다.

다음 샘플에서는 C3277를 생성 합니다.

```cpp
// C3277a.cpp
// compile with: /clr
ref class A
{
   enum E {e1,e2};   // C3277
   // try the following line instead
   // enum class E {e1,e2};
};

int main()
{
}
```
