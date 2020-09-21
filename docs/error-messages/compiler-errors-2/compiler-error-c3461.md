---
title: 컴파일러 오류 C3461
ms.date: 11/04/2016
f1_keywords:
- C3461
helpviewer_keywords:
- C3461
ms.assetid: bd66833a-545d-445a-bdfe-dee771a450a4
ms.openlocfilehash: c5195e0a9bba1bc9e5962f3d3ae1795bb098be3d
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742881"
---
# <a name="compiler-error-c3461"></a>컴파일러 오류 C3461

'type': 관리되는 형식만 전달할 수 있습니다.

형식 전달은 CLR 형식에서만 발생할 수 있습니다.  자세한 내용은 [클래스 및 구조체](../../extensions/classes-and-structs-cpp-component-extensions.md) 를 참조 하세요.

자세한 내용은 [형식 전달 (c + +/cli)](../../extensions/type-forwarding-cpp-cli.md)을 참조 하세요.

## <a name="examples"></a>예제

다음 샘플에서는 구성 요소를 만듭니다.

```cpp
// C3461.cpp
// compile with: /clr /LD
public ref class R {};
```

다음 샘플에서는 C3461을 생성합니다.

```cpp
// C3461b.cpp
// compile with: /clr /c
#using "C3461.dll"
class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3461
[assembly:TypeForwardedTo(R::typeid)];   // OK
```
