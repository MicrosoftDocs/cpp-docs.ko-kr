---
description: '자세한 정보: 컴파일러 오류 C3737'
title: 컴파일러 오류 C3737
ms.date: 11/04/2016
f1_keywords:
- C3737
helpviewer_keywords:
- C3737
ms.assetid: ca2aeb23-2491-4ccb-8838-884abf7065c8
ms.openlocfilehash: 0b7c604f49c710334eb9ddfafa253df90c72103c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244981"
---
# <a name="compiler-error-c3737"></a>컴파일러 오류 C3737

' delegate ': 대리자는 명시적 호출 규칙을 사용할 수 없습니다.

에 대 한 [호출 규칙](../../cpp/calling-conventions.md) 은 지정할 수 없습니다 **`delegate`** .

## <a name="example"></a>예제

다음 샘플에서는 C3737를 생성 합니다.

```cpp
// C3737a.cpp
// compile with: /clr
delegate void __stdcall MyFunc();   // C3737
// Try the following line instead.
// delegate void MyFunc();

int main() {
}
```
