---
title: 컴파일러 경고 (수준 1) C4490
ms.date: 11/04/2016
f1_keywords:
- C4490
helpviewer_keywords:
- C4490
ms.assetid: f9b03ecf-41a1-4f4d-a74c-2c1e88234ccc
ms.openlocfilehash: 41fa124eed365b87b419a4019262c0c673399295
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966188"
---
# <a name="compiler-warning-level-1-c4490"></a>컴파일러 경고 (수준 1) C4490

' override ': 재정의 지정자를 잘못 사용 했습니다. ' function '이 기본 ref 클래스 메서드와 일치 하지 않습니다.

재정의 지정자를 잘못 사용 했습니다. 예를 들어 인터페이스 함수를 재정의 하지 않는 경우이 함수를 구현 합니다.

자세한 내용은 [Override 지정자](../../extensions/override-specifiers-cpp-component-extensions.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4490를 생성 합니다.

```cpp
// C4490.cpp
// compile with: /clr /c /W1

interface struct IFace {
   void Test();
};

ref struct Class1 : public IFace {
   virtual void Test() override {}   // C4490
   // try the following line instead
   // virtual void Test() {}
};
```