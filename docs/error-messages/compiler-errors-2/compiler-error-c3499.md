---
title: 컴파일러 오류 C3499
ms.date: 11/04/2016
f1_keywords:
- C3499
helpviewer_keywords:
- C3499
ms.assetid: 6717de5c-ae0f-4024-bdf2-b5598009e7b6
ms.openlocfilehash: 381e665745f79f6156350f66e412f0580a06f6fb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027313"
---
# <a name="compiler-error-c3499"></a>컴파일러 오류 C3499

반환 형식이 void로 지정된 람다가 값을 반환할 수 없습니다.

`void` 를 반환 형식으로 지정하는 람다 식이 값을 반환하거나 람다 식이 둘 이상의 문을 포함하고 값을 반환하지만 반환 형식을 지정하지 않을 경우 컴파일러에서 이 오류를 생성합니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 람다 식에서 값을 반환하지 않습니다. 또는

- 람다 식의 반환 형식을 제공합니다. 또는

- 람다 식의 본문을 구성하는 문을 단일 문으로 결합합니다.

## <a name="example"></a>예제

다음 예제에서는 람다 식의 본문이 여러 문을 포함하고 값을 반환하지만 람다 식에서 반환 형식을 지정하지 않으므로 C3499를 생성합니다.

```
// C3499a.cpp

int main()
{
   [](int x) { int n = x * 2; return n; } (5); // C3499
}
```

## <a name="example"></a>예제

다음 예제에서는 C3499에 대한 두 가지 해결 방법을 보여 줍니다. 첫 번째 해결 방법은 람다 식의 반환 형식을 제공하는 것입니다. 두 번째 해결 방법은 람다 식의 본문을 구성하는 문을 단일 문으로 결합하는 것입니다.

```
// C3499b.cpp

int main()
{
   // Possible resolution 1:
   // Provide the return type of the lambda expression.
   [](int x) -> int { int n = x * 2; return n; } (5);

   // Possible resolution 2:
   // Combine the statements that make up the body of
   // the lambda expression into a single statement.
   [](int x) { return x * 2; } (5);
}
```

## <a name="see-also"></a>참고자료

[람다 식](../../cpp/lambda-expressions-in-cpp.md)