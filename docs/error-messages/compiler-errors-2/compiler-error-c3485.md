---
description: '자세한 정보: 컴파일러 오류 C3485'
title: 컴파일러 오류 C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 0b11eb4487a9b6deb611852dd11a8a1963dd961e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168386"
---
# <a name="compiler-error-c3485"></a>컴파일러 오류 C3485

람다 정의에 cv 한정자를 사용할 수 없습니다.

**`const`** 또는 **`volatile`** 한정자를 람다 식 정의의 일부로 사용할 수 없습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- **`const`** **`volatile`** 람다 식 정의에서 또는 한정자를 제거 합니다.

## <a name="example"></a>예제

다음 예제에서는 **`const`** 한정자를 람다 식 정의의 일부로 사용 하기 때문에 C3485를 생성 합니다.

```cpp
// C3485.cpp

int main()
{
   auto x = []() const mutable {}; // C3485
}
```

## <a name="see-also"></a>참조

[람다 식](../../cpp/lambda-expressions-in-cpp.md)
