---
description: '자세한 정보: 컴파일러 오류 C3462'
title: 컴파일러 오류 C3462
ms.date: 11/04/2016
f1_keywords:
- C3462
helpviewer_keywords:
- C3462
ms.assetid: 56b75f35-9fad-42d9-a969-eeca5d709bec
ms.openlocfilehash: e201dc9d999438053d5fd8d70813360c28a534df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315792"
---
# <a name="compiler-error-c3462"></a>컴파일러 오류 C3462

'type': 가져온 형식만 전달할 수 있습니다.

TypeForwardedTo 특성이 참조된 메타데이터의 형식에 적용되어야 합니다.

자세한 내용은 [형식 전달 (c + +/cli)](../../extensions/type-forwarding-cpp-cli.md)을 참조 하세요.

## <a name="examples"></a>예제

다음 샘플에서는 구성 요소를 만듭니다.

```cpp
// C3462.cpp
// compile with: /clr /LD
public ref class R {};
```

다음 샘플에서는 C3462를 생성합니다.

```cpp
// C3462b.cpp
// compile with: /clr /c
#using "C3462.dll"
ref class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3462
[assembly:TypeForwardedTo(R::typeid)];
```
