---
description: '자세한 정보: 컴파일러 오류 C3480'
title: 컴파일러 오류 C3480
ms.date: 11/04/2016
f1_keywords:
- C3480
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
ms.openlocfilehash: dbeed462410d36b466e807d576549c1b73ee4917
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113417"
---
# <a name="compiler-error-c3480"></a>컴파일러 오류 C3480

'var': 람다 캡처 변수는 바깥쪽 함수 범위에 속해야 합니다.

람다 캡처 변수가 바깥쪽 함수 범위에 속하지 않습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 람다 식의 캡처 목록에서 변수를 제거합니다.

## <a name="examples"></a>예제

`global` 변수가 바깥쪽 함수 범위에 속하지 않으므로 다음 예제에서는 C3480을 생성합니다.

```cpp
// C3480a.cpp

int global = 0;
int main()
{
   [&global] { global = 5; }(); // C3480
}
```

다음 예제에서는 람다 식의 캡처 목록에서 `global` 변수를 제거하여 C3480을 해결합니다.

```cpp
// C3480b.cpp

int global = 0;
int main()
{
   [] { global = 5; }();
}
```

## <a name="see-also"></a>참조

[람다 식](../../cpp/lambda-expressions-in-cpp.md)
