---
description: '자세한 정보: 컴파일러 오류 C3363'
title: 컴파일러 오류 C3363
ms.date: 11/04/2016
f1_keywords:
- C3363
helpviewer_keywords:
- C3363
ms.assetid: 41aa922f-608e-4f7a-ba66-451fc1161935
ms.openlocfilehash: b746a4c1e220ee05f96f3f2ceae524d5747550d7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335029"
---
# <a name="compiler-error-c3363"></a>컴파일러 오류 C3363

'type': 'typeid'는 형식에만 적용될 수 있습니다.

[typeid](../../extensions/typeid-cpp-component-extensions.md) 연산자를 잘못 사용했습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3363을 생성합니다.

```cpp
// C3363.cpp
// compile with: /clr
int main() {
   System::typeid;   // C3363
}
```
