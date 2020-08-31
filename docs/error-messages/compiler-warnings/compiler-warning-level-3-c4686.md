---
title: 컴파일러 경고(수준 3) C4686
description: Microsoft c + + 컴파일러 경고 C4686.
ms.date: 08/29/2020
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: 6886ae7f413de630457b53e85b5cd75c4542ee19
ms.sourcegitcommit: 3628707bc17c99aac7aac27eb126cc2eaa4d07b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89194499"
---
# <a name="compiler-warning-level-3-c4686"></a>컴파일러 경고(수준 3) C4686

> '*사용자 정의 형식*': 동작이 변경 될 수 있습니다. UDT 반환 호출 규칙이 변경 되었습니다.

## <a name="remarks"></a>설명

클래스 템플릿 특수화는 반환 형식에서 사용 되기 전에 정의 되지 않았습니다. 클래스를 인스턴스화하는 모든 항목은 C4686를 확인 합니다. 인스턴스를 선언 하거나 멤버 (예:)에 액세스 하 `C<int>::some_member` 는 것도 옵션입니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제 되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md)를 참조 하세요.

## <a name="example"></a>예제

대신 다음을 시도 하세요.

```cpp
// C4686.cpp
// compile with: /W3
#pragma warning (default : 4686)
template <class T>
class C;

template <class T>
C<T> f(T);

template <class T>
class C {};

int main() {
   f(1);   // C4686
}

template <class T>
C<T> f(T) {
   return C<int>();
}
```
