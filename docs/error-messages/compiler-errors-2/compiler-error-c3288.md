---
title: 컴파일러 오류 C3288
ms.date: 11/04/2016
f1_keywords:
- C3288
helpviewer_keywords:
- C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
ms.openlocfilehash: a7b87fdbd2e15906ebc0c669f0b9a74ebf97f0b3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760181"
---
# <a name="compiler-error-c3288"></a>컴파일러 오류 C3288

' type ': 핸들 형식에 대 한 역참조가 잘못 되었습니다.

컴파일러가 핸들 형식의 잘못 된 역참조를 검색 했습니다. 핸들 형식을 역참조 하 고 참조에 할당할 수 있습니다. 자세한 내용은 [추적 참조 연산자](../../extensions/tracking-reference-operator-cpp-component-extensions.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3288를 생성 합니다.

```cpp
// C3288.cpp
// compile with: /clr
ref class R {};
int main() {
   *(System::Object^) nullptr;   // C3288

// OK
   (System::Object^) nullptr;   // OK
   R^ r;
   R% pr = *r;
}
```
