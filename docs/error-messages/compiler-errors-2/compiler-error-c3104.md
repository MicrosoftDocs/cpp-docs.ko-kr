---
title: 컴파일러 오류 C3104
ms.date: 11/04/2016
f1_keywords:
- C3104
helpviewer_keywords:
- C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
ms.openlocfilehash: 5f72af3d7149db7362df9fa23ac5ad6c058c552b
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743466"
---
# <a name="compiler-error-c3104"></a>컴파일러 오류 C3104

특성 인수가 잘못 되었습니다.

특성에 대 한 잘못 된 인수를 지정 했습니다.

자세한 내용은 [특성 매개 변수 형식](../../extensions/attribute-parameter-types-cpp-component-extensions.md) 을 참조 하세요.

이 오류는 Visual Studio 2005에 대해 수행 된 컴파일러 규칙 작업의 결과로 생성 될 수 있습니다. 관리 되는 배열을 사용자 지정 특성에 전달할 때 배열의 형식이 더 이상 집계 초기화 목록에서 추론 되지 않습니다. 이제 컴파일러에서 이니셜라이저 목록 뿐만 아니라 배열의 형식을 지정 해야 합니다.

## <a name="examples"></a>예제

다음 샘플에서는 C3104를 생성 합니다.

```cpp
// C3104a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104
// try the following line instead
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

다음 샘플에서는 C3104를 생성 합니다.

```cpp
// C3104b.cpp
// compile with: /clr /c
// C3104 expected
using namespace System;

int func() {
   return 0;
}

[attribute(All)]
ref class A {
public:
   A(int) {}
};

// Delete the following 2 lines to resolve.
[A(func())]
ref class B {};

// OK
[A(0)]
ref class B {};
```
