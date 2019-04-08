---
title: 컴파일러 오류 C3468
ms.date: 11/04/2016
f1_keywords:
- C3468
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
ms.openlocfilehash: e3870fa21e2b4a932937edd49091980406a5ff0d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58777234"
---
# <a name="compiler-error-c3468"></a>컴파일러 오류 C3468

'type': 어셈블리에만 형식을 전달할 수 있습니다.

'`file`'은 어셈블리가 아닙니다.

어셈블리의 형식만 전달할 수 있습니다.

자세한 내용은 [형식 전달 (C + + /cli CLI)](../../extensions/type-forwarding-cpp-cli.md)합니다.

## <a name="example"></a>예제

다음 샘플에서는 모듈을 만듭니다.

```
// C3468.cpp
// compile with: /LN /clr
public ref class R {};
```

## <a name="example"></a>예제

다음 샘플에서는 C3468을 생성합니다.

```
// C3468_b.cpp
// compile with: /clr /c
#using "C3468.netmodule"
[ assembly:TypeForwardedTo(R::typeid) ];   // C3468
```