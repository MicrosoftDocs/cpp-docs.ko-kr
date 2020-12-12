---
description: '자세한 정보: 컴파일러 오류 C3483'
title: 컴파일러 오류 C3483
ms.date: 11/04/2016
f1_keywords:
- C3483
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
ms.openlocfilehash: 7c67e1e4d44c64fbcc023ee410dff2ecdd92c361
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113390"
---
# <a name="compiler-error-c3483"></a>컴파일러 오류 C3483

'var'은 이미 람다 캡처 목록의 일부입니다.

람다 식의 캡처 목록에 동일한 변수를 두 번 이상 전달했습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 캡처 목록에서 변수의 추가 인스턴스를 모두 제거합니다.

## <a name="example"></a>예제

다음 예제에서는 변수 `n` 이 람다 식의 캡처 목록에 두 번 이상 나타나므로 C3483을 생성합니다.

```cpp
// C3483.cpp

int main()
{
   int m = 6, n = 5;
   [m,n,n] { return n + m; }(); // C3483
}
```

## <a name="see-also"></a>참조

[람다 식](../../cpp/lambda-expressions-in-cpp.md)
