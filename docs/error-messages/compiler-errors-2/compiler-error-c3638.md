---
description: '자세한 정보: 컴파일러 오류 C3638'
title: 컴파일러 오류 C3638
ms.date: 11/04/2016
f1_keywords:
- C3638
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
ms.openlocfilehash: 1d1cc59cd8065a5b0e661292b717ba885c6febeb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239196"
---
# <a name="compiler-error-c3638"></a>컴파일러 오류 C3638

' operator ': 표준 boxing 및 unboxing 변환 연산자는 다시 정의할 수 없습니다.

컴파일러는 암시적 boxing을 지원 하기 위해 관리 되는 각 클래스에 대 한 변환 연산자를 정의 합니다. 이 연산자는 다시 정의할 수 없습니다.

자세한 내용은 [암시적 Boxing](../../extensions/boxing-cpp-component-extensions.md)을 참조 하세요.

다음 샘플에서는 C3638를 생성 합니다.

```cpp
// C3638.cpp
// compile with: /clr
value struct V {
   V(){}
   static operator V^(V);   // C3638
};

int main() {
   V myV;
   V ^ pmyV = myV;   // operator supports implicit boxing
}
```
