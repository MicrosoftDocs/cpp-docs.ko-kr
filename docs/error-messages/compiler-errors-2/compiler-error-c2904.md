---
title: 컴파일러 오류 C2904
ms.date: 11/04/2016
f1_keywords:
- C2904
helpviewer_keywords:
- C2904
ms.assetid: d5802f2e-d3fc-473d-aa04-36957b4eaca5
ms.openlocfilehash: 506618da12af7d78db948f1a4197bf93367b7f7d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750600"
---
# <a name="compiler-error-c2904"></a>컴파일러 오류 C2904

'identifier': 이름이 현재 범위의 템플릿으로 이미 사용되었습니다.

코드 이름이 중복되지 않았는지 확인합니다.

다음 샘플에서는 C2904를 생성합니다.

```cpp
// C2904.cpp
// compile with: /c
void X();  // X is declared as a function
template<class T> class X{};  // C2904
```
