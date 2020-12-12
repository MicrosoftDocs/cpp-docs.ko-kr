---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4946'
title: 컴파일러 경고(수준 1) C4946
ms.date: 11/04/2016
f1_keywords:
- C4946
helpviewer_keywords:
- C4946
ms.assetid: b85cbef0-e053-4de6-9b14-7b0f82d40495
ms.openlocfilehash: 75422a3923f0c39ec79945a2e1c6f8b91c00ace8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327999"
---
# <a name="compiler-warning-level-1-c4946"></a>컴파일러 경고(수준 1) C4946

관련 클래스 'class1'과(와) 'class2' 사이에 reinterpret_cast가 사용되었습니다.

[Reinterpret_cast](../../cpp/reinterpret-cast-operator.md) 를 사용 하 여 관련 형식 간에 캐스팅 하지 마십시오. 대신 [static_cast](../../cpp/static-cast-operator.md) 를 사용 하거나 다형성 형식의 경우 [dynamic_cast](../../cpp/dynamic-cast-operator.md)를 사용 합니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)을 참조하세요.

다음 코드 예제에서는 C4946이 생성됩니다.

```cpp
// C4946.cpp
// compile with: /W1
#pragma warning (default : 4946)
class a {
public:
   a() : m(0) {}
   int m;
};

class b : public virtual a {
};

class b2 : public virtual a {
};

class c : public b, public b2 {
};

int main() {
   c* pC = new c;
   a* pA = reinterpret_cast<a*>(pC);   // C4946
   // try the following line instead
   // a* pA = static_cast<a*>(pC);
}
```
