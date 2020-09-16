---
title: 컴파일러 오류 C3535
ms.date: 11/04/2016
f1_keywords:
- C3535
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
ms.openlocfilehash: 673fe6a8b5eb6dfcd9caa841b18d5b47fb7858bf
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686092"
---
# <a name="compiler-error-c3535"></a>컴파일러 오류 C3535

' u s e r '에서 ' type2 '의 형식을 추론할 수 없습니다.

키워드로 선언 된 변수의 형식은 **`auto`** 초기화 식의 형식에서 추론할 수 없습니다. 예를 들어 초기화 식이 형식이 아닌로 계산 되는 경우이 오류가 발생 합니다 **`void`** .

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. 초기화 식의 형식이이 아닌지 확인 **`void`** 합니다.

1. 선언이 기본 형식에 대 한 포인터가 아닌지 확인 합니다. 자세한 내용은 [기본 형식](../../cpp/fundamental-types-cpp.md)을 참조 하세요.

1. 선언이 형식에 대 한 포인터인 경우 초기화 식이 포인터 형식 인지 확인 합니다.

## <a name="examples"></a>예제

다음 예에서는 초기화 식이로 계산 되기 때문에 C3535를 생성 합니다 **`void`** .

```cpp
// C3535a.cpp
// Compile with /Zc:auto
void f(){}
int main()
{
   auto x = f();   //C3535
   return 0;
}
```

다음 예에서는 문이 변수를 `x` 추론 된 형식에 대 한 포인터로 선언 하지만 이니셜라이저 식의 형식이 double 이기 때문에 c3535를 생성 합니다. 따라서 컴파일러가 변수의 형식을 추론할 수 없습니다.

```cpp
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

다음 예제에서는 변수가 `p` 추론 된 형식에 대 한 포인터를 선언 하지만 초기화 식이 포인터 형식이 아니기 때문에 c3535를 생성 합니다.

```cpp
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>참조

[auto 키워드](../../cpp/auto-keyword.md)<br/>
[기본 형식](../../cpp/fundamental-types-cpp.md)
