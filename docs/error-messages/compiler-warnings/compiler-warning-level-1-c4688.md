---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4688'
title: 컴파일러 경고(수준 1) C4688
ms.date: 11/04/2016
f1_keywords:
- C4688
helpviewer_keywords:
- C4688
ms.assetid: a027df3c-b2b8-4c49-8539-c2bc42db74e8
ms.openlocfilehash: 9abd793463cf576549b09a1a887d225317ca6fc5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285164"
---
# <a name="compiler-warning-level-1-c4688"></a>컴파일러 경고(수준 1) C4688

'constraint': 제약 조건 목록에 어셈블리 전용 형식 'type'이 있습니다.

제약 조건 목록에 어셈블리 전용 형식이 있으므로 어셈블리 외부에서 형식에 액세스하는 경우 사용할 수 없습니다. 자세한 내용은 [제네릭](../../extensions/generics-cpp-component-extensions.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4688을 생성합니다.

```cpp
// C4688.cpp
// compile with: /clr /c /W1
ref struct A {};   // private type
public ref struct B {};

// Delete the following 3 lines to resolve.
generic <class T>
where T : A   // C4688
public ref struct M {};

generic <class T>
where T : B
public ref struct N {};
```
