---
title: 컴파일러 오류 C3465
ms.date: 11/04/2016
f1_keywords:
- C3465
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
ms.openlocfilehash: 56eeac18d5b8efc32501bf54e2de3aa216e05a13
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742023"
---
# <a name="compiler-error-c3465"></a>컴파일러 오류 C3465

'type' 형식을 사용하려면 'assembly' 어셈블리를 참조해야 합니다.

클라이언트를 다시 컴파일할 때까지 형식 전달은 클라이언트 애플리케이션에 대해 작동합니다. 다시 컴파일하는 경우에는 클라이언트 애플리케이션에서 사용하는 형식의 정의를 비롯하여 모든 어셈블리에 대한 참조가 필요합니다.

자세한 내용은 [형식 전달 (c + +/cli)](../../extensions/type-forwarding-cpp-cli.md)을 참조 하세요.

## <a name="examples"></a>예제

다음 샘플에서는 형식의 새 위치를 포함하는 어셈블리를 빌드합니다.

```cpp
// C3465.cpp
// compile with: /clr /LD
public ref class R {
public:
   ref class N {};
};
```

다음 샘플에서는 형식의 정의를 포함하는 데 사용한 어셈블리를 빌드하지만 이제는 형식에 대한 전달 구문을 포함합니다.

```cpp
// C3465_b.cpp
// compile with: /clr /LD
#using "C3465.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

다음 샘플에서는 C3465를 생성합니다.

```cpp
// C3465_c.cpp
// compile with: /clr
// C3465 expected
#using "C3465_b.dll"
// Uncomment the following line to resolve.
// #using "C3465.dll"

int main() {
   R^ r = gcnew R();
}
```
