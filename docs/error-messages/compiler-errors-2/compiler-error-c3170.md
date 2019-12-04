---
title: 컴파일러 오류 C3170
ms.date: 11/04/2016
f1_keywords:
- C3170
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
ms.openlocfilehash: e2d74a637e2902fcf636b49068882f32aa706f94
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761766"
---
# <a name="compiler-error-c3170"></a>컴파일러 오류 C3170

프로젝트에 다른 모듈 식별자를 사용할 수 없습니다.

컴파일할 때 파일 중 두 개에 다른 이름의 [모듈](../../windows/module-cpp.md) 특성이 있습니다. 컴파일 당 고유한 `module` 특성을 하나만 지정할 수 있습니다.

둘 이상의 소스 코드 파일에 동일한 `module` 특성을 지정할 수 있습니다.

예를 들어 다음 모듈 특성을 찾은 경우

```cpp
// C3170.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
int main() {}
```

그리고

```cpp
// C3170b.cpp
// compile with: C3170.cpp
// C3170 expected
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
```

컴파일러는 C3170를 생성 합니다 (다른 이름을 적어 둡니다).
