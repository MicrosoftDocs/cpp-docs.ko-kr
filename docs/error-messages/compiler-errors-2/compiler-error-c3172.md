---
title: 컴파일러 오류 C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: ca0eab35f6e60d81a324156905619ceb7ace8830
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508290"
---
# <a name="compiler-error-c3172"></a>컴파일러 오류 C3172

' module_name ': 프로젝트에서 다른 idl_module 특성을 지정할 수 없습니다.

[idl_module](../../windows/attributes/idl-module.md) `dllname` `version` 컴파일할 때 파일 중 두 개에서 이름이 같지만 매개 변수가 다른 idl_module 특성을 찾았습니다. `idl_module`컴파일 당 고유한 특성을 하나만 지정할 수 있습니다.

둘 `idl_module` 이상의 소스 코드 파일에 동일한 특성을 지정할 수 있습니다.

예를 들어 다음과 같은 `idl_module` 특성을 찾은 경우

```cpp
// C3172.cpp
[module(name="MyMod")];
[ idl_module(name="x", dllname="file.dll", version="1.1") ];
int main() {}
```

그리고

```cpp
// C3172b.cpp
// compile with: C3172.cpp
// C3172 expected
[ idl_module(name="x", dllname="file.dll", version="1.0") ];
```

컴파일러는 C3172를 생성 합니다 (다른 버전 값에 유의).
