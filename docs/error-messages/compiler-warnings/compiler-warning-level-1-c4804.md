---
title: 컴파일러 경고 (수준 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 97ad076325b11329896d98367fb3ac311ec5ded9
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051566"
---
# <a name="compiler-warning-level-1-c4804"></a>컴파일러 경고 (수준 1) C4804

' operation ': 연산에 ' bool ' 형식을 안전 하 게 사용 하지 않습니다.

이 경고는 `bool` 변수나 값을 예기치 않은 방식으로 사용한 경우에 발생 합니다. 예를 들어 음의 단항 연산자 ( **-** ) 또는 보수 연산자 (`~`)와 같은 연산자를 사용 하는 경우 C4804이 생성 됩니다. 컴파일러가 식을 계산 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4804를 생성 합니다.

```cpp
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```