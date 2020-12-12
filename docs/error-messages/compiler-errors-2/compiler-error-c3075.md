---
description: '자세한 정보: 컴파일러 오류 C3075'
title: 컴파일러 오류 C3075
ms.date: 11/04/2016
f1_keywords:
- C3075
helpviewer_keywords:
- C3075
ms.assetid: f431daa9-e0fa-48f0-a5c3-f99be96b55e3
ms.openlocfilehash: 68169ade5e9de13b618fe6d90936cbe887690775
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320225"
---
# <a name="compiler-error-c3075"></a>컴파일러 오류 C3075

'instance': 참조 형식 'type'의 인스턴스는 값 형식에 포함할 수 없습니다.

값 형식이 참조 형식의 인스턴스를 포함할 수 없습니다.

자세한 내용은 [참조 형식에 대 한 c + + 스택 의미 체계](../../dotnet/cpp-stack-semantics-for-reference-types.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3075를 생성합니다.

```cpp
// C3075.cpp
// compile with: /clr /c
ref struct U {};
value struct X {
   U y;   // C3075
};

ref struct Y {
   U y;   // OK
};
```
