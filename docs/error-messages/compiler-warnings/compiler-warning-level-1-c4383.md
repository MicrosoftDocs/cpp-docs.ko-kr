---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4383'
title: 컴파일러 경고(수준 1) C4383
ms.date: 11/04/2016
f1_keywords:
- C4383
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
ms.openlocfilehash: f6ece51ed497919cf444952f42130cc3a4bfb4a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339932"
---
# <a name="compiler-warning-level-1-c4383"></a>컴파일러 경고(수준 1) C4383

' instance_dereference_operator ': 사용자 정의 ' operator ' 연산자가 있는 경우 핸들 역참조의 의미가 변경 될 수 있습니다. 피연산자에 대해 명시적으로 연산자를 정적 함수로 작성 합니다.

관리 되는 형식에서 역참조 연산자의 사용자 정의 인스턴스 재정의를 추가 하면 해당 형식의 역참조 연산자가 핸들의 개체를 반환 하는 기능을 재정의할 수 있습니다. 정적 사용자 정의 역참조 연산자를 작성 하는 것이 좋습니다.

자세한 내용은 [개체 연산자 (^)](../../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) 및 [추적 참조 연산자](../../extensions/tracking-reference-operator-cpp-component-extensions.md)에 대 한 핸들을 참조 하십시오.

또한 인스턴스 연산자는 참조 된 메타 데이터를 통해 다른 언어 컴파일러에서 사용할 수 없습니다. 자세한 내용은 [사용자 정의 연산자 (c + +/cli)](../../dotnet/user-defined-operators-cpp-cli.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4383를 생성 합니다.

```cpp
// C4383.cpp
// compile with: /clr /W1

ref struct S {
   int operator*() { return 0; }   // C4383
};

ref struct T {
   static int operator*(T%) { return 0; }
};

int main() {
   S s;
   S^ pS = %s;

   T t;
   T^ pT = %t;
   T% rT = *pT;
}
```
