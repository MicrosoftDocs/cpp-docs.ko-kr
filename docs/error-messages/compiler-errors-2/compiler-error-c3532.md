---
title: 컴파일러 오류 C3532
ms.date: 11/04/2016
f1_keywords:
- C3532
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
ms.openlocfilehash: f9339797f42967ef1de0253b1e51092e6d98df5d
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686784"
---
# <a name="compiler-error-c3532"></a>컴파일러 오류 C3532

' type ': ' auto '를 잘못 사용 했습니다.

표시 된 형식은 키워드를 사용 하 여 선언할 수 없습니다 **`auto`** . 예를 들어 키워드를 사용 **`auto`** 하 여 배열 또는 메서드 반환 형식을 선언할 수 없습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. 초기화 식이 올바른 형식을 생성 하는지 확인 하십시오.

1. 배열 또는 메서드 반환 형식을 선언 하지 않도록 합니다.

## <a name="examples"></a>예제

다음 예제에서는 **`auto`** 키워드가 메서드 반환 형식을 선언할 수 없기 때문에 C3532를 생성 합니다.

```cpp
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

다음 예제에서는 **`auto`** 키워드가 배열을 선언할 수 없기 때문에 C3532를 생성 합니다.

```cpp
// C3532b.cpp
// Compile with /Zc:auto
int main()
{
   int x[5];
   auto a[5];            // C3532
   auto b[1][2];         // C3532
   auto y[5] = x;        // C3532
   auto z[] = {1, 2, 3}; // C3532
   auto w[] = x;         // C3532
   return 0;
}
```

## <a name="see-also"></a>참조

[auto 키워드](../../cpp/auto-keyword.md)
