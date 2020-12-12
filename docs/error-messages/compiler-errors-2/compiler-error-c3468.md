---
description: '자세한 정보: 컴파일러 오류 C3468'
title: 컴파일러 오류 C3468
ms.date: 11/04/2016
f1_keywords:
- C3468
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
ms.openlocfilehash: 7e6d58e012baa0163f33867069e7250da61177b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315740"
---
# <a name="compiler-error-c3468"></a>컴파일러 오류 C3468

'type': 어셈블리에만 형식을 전달할 수 있습니다.

'`file`'은 어셈블리가 아닙니다.

어셈블리의 형식만 전달할 수 있습니다.

자세한 내용은 [형식 전달 (c + +/cli)](../../extensions/type-forwarding-cpp-cli.md)을 참조 하세요.

## <a name="examples"></a>예제

다음 샘플에서는 모듈을 만듭니다.

```cpp
// C3468.cpp
// compile with: /LN /clr
public ref class R {};
```

다음 샘플에서는 C3468을 생성합니다.

```cpp
// C3468_b.cpp
// compile with: /clr /c
#using "C3468.netmodule"
[ assembly:TypeForwardedTo(R::typeid) ];   // C3468
```
