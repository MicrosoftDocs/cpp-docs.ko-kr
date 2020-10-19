---
title: 컴파일러 경고(수준 4) C4389
description: Microsoft C/c + + 컴파일러 경고 C4389, 해당 원인 및 해결 방법
ms.date: 10/16/2020
f1_keywords:
- c4389
helpviewer_keywords:
- C4389
ms.openlocfilehash: b06b013151ed12b4f66bb23a7e862992d05e6b30
ms.sourcegitcommit: f19f02f217b80804ab321d463c76ce6f681abcc6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92176271"
---
# <a name="compiler-warning-level-4-c4389"></a>컴파일러 경고(수준 4) C4389

> '*같음-연산자*': signed/unsigned가 일치 하지 않습니다.

**`==`** **`!=`** 및 변수와 관련 된 또는 연산 **`signed`** **`unsigned`** 입니다. 이로 인해 데이터가 손실 될 수 있습니다.

## <a name="remarks"></a>설명

이 경고를 해결 하는 한 가지 방법은 및 형식을 비교할 때 두 가지 형식 중 하나를 캐스팅 하는 것입니다 **`signed`** **`unsigned`** .

## <a name="example"></a>예제

다음 샘플에서는 C4389를 생성 합니다.

```cpp
// C4389.cpp
// compile with: cl /EHsc /W4 C4389.cpp

int main()
{
   int a = 9;
   unsigned int b = 10;
   int result = 0;

   if (a == b)   // C4389
      result = 1;
   else
      result = 2;

   if (unsigned(a) == b) // OK
      result = 3;
   else
      result = 4;

   return result;
}
```

## <a name="see-also"></a>참고 항목

[컴파일러 경고 C4018](compiler-warning-level-3-c4018.md)\
[컴파일러 경고 (수준 4) C4388](c4388.md)
