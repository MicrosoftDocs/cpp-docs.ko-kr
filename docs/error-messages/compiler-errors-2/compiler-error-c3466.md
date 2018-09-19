---
title: 컴파일러 오류 C3466 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3466
dev_langs:
- C++
helpviewer_keywords:
- C3466
ms.assetid: 69a877d9-a749-474b-bfc3-8d3fd53ba8fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b851a9ae24b315aded5cd545ede77fd920a2b63
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105234"
---
# <a name="compiler-error-c3466"></a>컴파일러 오류 C3466

'type': 제네릭 클래스의 특수화를 전달할 수 없습니다.

제네릭 클래스의 특수화에는 형식 전달을 사용할 수 없습니다.

자세한 내용은 [형식 전달 (C + + /cli CLI)](../../windows/type-forwarding-cpp-cli.md)합니다.

## <a name="example"></a>예제

다음 샘플에서는 구성 요소를 만듭니다.

```
// C3466.cpp
// compile with: /clr /LD
generic<typename T>
public ref class GR {};

public ref class GR2 {};
```

## <a name="example"></a>예제

다음 샘플에서는 C3466를 생성합니다.

```
// C3466_b.cpp
// compile with: /clr /c
#using "C3466.dll"
[assembly:TypeForwardedTo(GR<int>::typeid)];   // C3466
[assembly:TypeForwardedTo(GR2::typeid)];   // OK
```