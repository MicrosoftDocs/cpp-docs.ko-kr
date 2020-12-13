---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4623'
title: 컴파일러 경고(수준 4) C4623
ms.date: 11/04/2016
f1_keywords:
- C4623
helpviewer_keywords:
- C4623
ms.assetid: e630d8d0-f6ea-469c-a74f-07b027587225
ms.openlocfilehash: 3e10b83af1ba38d50307abdc87f3fde3b9b30417
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134240"
---
# <a name="compiler-warning-level-4-c4623"></a>컴파일러 경고(수준 4) C4623

'`derived class`': 기본 클래스의 기본 생성자에 액세스할 수 없거나 이러한 생성자가 삭제되므로 기본 생성자가 암시적으로 삭제된 것으로 정의됩니다.

생성자가 기본 클래스에서 액세스할 수 없으며 파생 클래스에 대해 생성되지 않았습니다. 스택에 이 형식의 개체를 만들려고 하면 컴파일러 오류가 발생합니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4623 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C4623.cpp
// compile with: /W4
#pragma warning(default : 4623)
class B {
   B();
};

class C {
public:
   C();
};

class D : public B {};   // C4623 - to fix, make B's constructor public
class E : public C {};   // OK - class C constructor is public

int main() {
   // D d;  will cause an error
}
```
