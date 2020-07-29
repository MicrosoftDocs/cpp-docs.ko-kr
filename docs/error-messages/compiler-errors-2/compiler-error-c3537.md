---
title: 컴파일러 오류 C3537
ms.date: 11/04/2016
f1_keywords:
- C3537
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
ms.openlocfilehash: 663ef761d6c52aeb4c3cc9ce109079c647904e36
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197555"
---
# <a name="compiler-error-c3537"></a>컴파일러 오류 C3537

' type ': ' a u t o '가 포함 된 형식으로 캐스팅할 수 없습니다.

형식에 **`auto`** 키워드가 포함 되 고 기본 [/zc: auto](../../build/reference/zc-auto-deduce-variable-type.md) 컴파일러 옵션이 적용 되므로 지정 된 형식으로 변수를 캐스팅할 수 없습니다.

## <a name="example"></a>예제

변수가 키워드를 포함 하는 형식으로 캐스팅 되기 때문에 다음 코드는 C3537을 생성 합니다 **`auto`** .

```cpp
// C3537.cpp
// Compile with /Zc:auto
int main()
{
   int value = 123;
   auto(value);                        // C3537
   (auto)value;                        // C3537
   auto x1 = auto(value);              // C3537
   auto x2 = (auto)value;              // C3537
   auto x3 = static_cast<auto>(value); // C3537
   return 0;
}
```

## <a name="see-also"></a>참조

[auto 키워드](../../cpp/auto-keyword.md)
