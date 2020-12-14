---
description: '자세한 정보: 컴파일러 오류 C3171'
title: 컴파일러 오류 C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: 65e7e1db9a864b894a0bce825df09a372489a79d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242199"
---
# <a name="compiler-error-c3171"></a>컴파일러 오류 C3171

' module ': 프로젝트에 다른 모듈 특성을 지정할 수 없습니다.

컴파일의 두 파일에 다른 매개 변수 목록을 사용 하는 [모듈](../../windows/attributes/module-cpp.md) 특성이 있습니다. `module`컴파일 당 고유한 특성을 하나만 지정할 수 있습니다.

둘 `module` 이상의 소스 코드 파일에 동일한 특성을 지정할 수 있습니다.

예를 들어 다음과 같은 `module` 특성을 찾은 경우

```cpp
// C3171.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];
int main() {}
```

그리고

```cpp
// C3171b.cpp
// compile with: C3171.cpp
// C3171 expected
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];
```

컴파일러는 C3171를 생성 합니다 (다른 버전 값에 유의).
