---
description: '자세한 정보: 컴파일러 오류 C2534'
title: 컴파일러 오류 C2534
ms.date: 11/04/2016
f1_keywords:
- C2534
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
ms.openlocfilehash: fbdc4c292a8eb59ee9ab51de0100455139473f7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302077"
---
# <a name="compiler-error-c2534"></a>컴파일러 오류 C2534

' identifier ': 생성자는 값을 반환할 수 없습니다.

생성자는 값을 반환 하거나 반환 형식이 아니더라도 반환 형식을 가질 수 없습니다 **`void`** .

생성자 정의에서 문을 제거 하 여이 오류를 해결할 수 있습니다 **`return`** .

다음 샘플에서는 C2534를 생성 합니다.

```cpp
// C2534.cpp
class A {
public:
   int i;
   A() { return i; }   // C2534
};
```
