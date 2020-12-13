---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4625'
title: 컴파일러 경고(수준 4) C4625
ms.date: 11/04/2016
f1_keywords:
- C4625
helpviewer_keywords:
- C4625
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
ms.openlocfilehash: 1b154e1f2e52c21affd47c1b0fc30d29b290269e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134227"
---
# <a name="compiler-warning-level-4-c4625"></a>컴파일러 경고(수준 4) C4625

'derived class': 기본 클래스의 복사 생성자에 액세스할 수 없거나 이러한 생성자가 삭제되었으므로 복사 생성자가 암시적으로 삭제된 것으로 정의됩니다.

복사 생성자가 삭제되었거나 기본 클래스에서 액세스할 수 없으므로 파생 클래스에 대해 생성되지 않았습니다. 이 형식의 개체를 복사하려고 하면 컴파일러 오류가 발생합니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4625를 생성하고 해결 방법을 보여 줍니다.

```cpp
// C4625.cpp
// compile with: /W4 /c
#pragma warning(default : 4625)

struct A {
   A() {}

private:
   A(const A&) {}
};

struct C : private virtual A {};
struct B :  C {};   // C4625 no copy constructor

struct D : A {};
struct E :  D {};   // OK
```
