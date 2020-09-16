---
title: 컴파일러 오류 C3489
ms.date: 11/04/2016
f1_keywords:
- C3489
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
ms.openlocfilehash: 3b192a14a39b7c0c9d264bda8073c54f0f395924
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685768"
---
# <a name="compiler-error-c3489"></a>컴파일러 오류 C3489

기본 캡처 모드가 값 방식인 경우 'var'이 필요합니다.

람다 식에 대한 기본 캡처 모드를 값 방식으로 지정할 경우 해당 식의 캡처 절에 변수를 값으로 전달할 수 없습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 변수를 캡처 절에 명시적으로 전달하지 마세요. 또는

- 값 방식을 기본 캡처 모드로 지정하지 마세요. 또는

- 참조 방식을 기본 캡처 모드로 지정합니다. 또는

- 변수를 캡처 절에 참조로 전달합니다. 이 경우 람다 식의 동작이 변경될 수 있습니다.

## <a name="examples"></a>예제

다음 예제에서는 기본 모드가 값 방식인 람다 식의 캡처 절에 `n` 변수가 값으로 나타나기 때문에 C3489를 생성합니다.

```cpp
// C3489a.cpp

int main()
{
   int n = 5;
   [=, n]() { return n; } (); // C3489
}
```

다음 예제에서는 C3489에 대한 네 가지 해결 방법을 보여 줍니다.

```cpp
// C3489b.cpp

int main()
{
   int n = 5;

   // Possible resolution 1:
   // Do not explicitly pass n to the capture clause.
   [=]() { return n; } ();

   // Possible resolution 2:
   // Do not specify by-value as the default capture mode.
   [n]() { return n; } ();

   // Possible resolution 3:
   // Specify by-reference as the default capture mode.
   [&, n]() { return n; } ();

   // Possible resolution 4:
   // Pass n by reference to the capture clause.
   [&n]() { return n; } ();
}
```

## <a name="see-also"></a>참조

[람다 식](../../cpp/lambda-expressions-in-cpp.md)
