---
title: 컴파일러 오류 C3536
ms.date: 11/04/2016
f1_keywords:
- C3536
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
ms.openlocfilehash: a140847b642ac2437b67aa957328c3b8fbfc592d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761571"
---
# <a name="compiler-error-c3536"></a>컴파일러 오류 C3536

' symbol ': 초기화 되기 전에 사용할 수 없습니다.

표시 된 기호는 초기화 되기 전에 사용할 수 없습니다. 실제로, 이는 변수를 사용하여 자신을 초기화할 수 없음을 의미합니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. 자체를 사용 하 여 변수를 초기화 하지 마십시오.

## <a name="example"></a>예제

다음 예에서는 각 변수가 자체로 초기화 되기 때문에 C3536을 생성 합니다.

```cpp
// C3536.cpp
// Compile with /Zc:auto
int main()
{
   auto a = a;     //C3536
   auto b = &b;    //C3536
   auto c = c + 1; //C3536
   auto* d = &d;   //C3536
   auto& e = e;    //C3536
   return 0;
};
```

## <a name="see-also"></a>참조

[auto 키워드](../../cpp/auto-keyword.md)
