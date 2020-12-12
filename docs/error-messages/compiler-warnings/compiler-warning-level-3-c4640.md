---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4640'
title: 컴파일러 경고(수준 3) C4640
ms.date: 11/04/2016
f1_keywords:
- C4640
helpviewer_keywords:
- C4640
ms.assetid: f76871f6-e436-4c35-9793-d2f22f7e1c7f
ms.openlocfilehash: f0fc41256d11c54742a157236e09e36277902b5e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338555"
---
# <a name="compiler-warning-level-3-c4640"></a>컴파일러 경고(수준 3) C4640

' instance ': 지역 정적 개체의 생성은 스레드로부터 안전 하지 않습니다.

개체의 정적 인스턴스는 스레드로부터 안전 하지 않습니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4640를 생성 합니다.

```cpp
// C4640.cpp
// compile with: /W3
#pragma warning(default:4640)

class X {
public:
   X() {
   }
};

void f() {
   static X aX;   // C4640
}

int main() {
   f();
}
```
