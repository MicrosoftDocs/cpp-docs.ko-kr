---
title: 컴파일러 오류 C2061 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2061
dev_langs:
- C++
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 896fdb21c57e0f558b87ec23e2be309cf49f8095
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057966"
---
# <a name="compiler-error-c2061"></a>컴파일러 오류 C2061

구문 오류: 'identifier' 식별자

컴파일러가 필요한 되지 않은 식별자를 찾았습니다. 했는지 `identifier` 사용 하기 전에 선언 됩니다.

이니셜라이저는 괄호로 묶을 수 있습니다. 이 문제를 방지 하려면 괄호로 묶거나 또는 있도록를 `typedef`입니다.

컴파일러는 클래스 템플릿 인수로; 식을 검색 하는 경우이 오류를 일으킬 수도 있습니다. 사용 하 여 [typename](../../cpp/typename.md) 형식이 컴파일러에 지시 합니다.

다음 샘플에서는 C2061 오류가 생성 됩니다.

```
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

C2061 인스턴스 이름을 전달 하는 경우 발생할 수 있습니다 [typeid](../../windows/typeid-cpp-component-extensions.md):

```
// C2061b.cpp
// compile with: /clr
ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   System::Type ^ pType = typeid<pG>;   // C2061
   System::Type ^ pType2 = typeid<G>;   // OK
}
```