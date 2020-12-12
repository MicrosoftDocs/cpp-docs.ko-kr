---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4706'
title: 컴파일러 경고(수준 4) C4706
ms.date: 11/04/2016
f1_keywords:
- C4706
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
ms.openlocfilehash: ca614d0ca55dcfa22ec31df78ebe2be904ffd9e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208530"
---
# <a name="compiler-warning-level-4-c4706"></a>컴파일러 경고(수준 4) C4706

조건식 내에 할당

조건식의 테스트 값이 할당의 결과입니다.

할당에는 테스트 식을 포함 하 여 다른 식에서 합법적으로 사용할 수 있는 값 (할당의 왼쪽에 있는 값)이 있습니다.

다음 샘플에서는 C4706를 생성 합니다.

```cpp
// C4706a.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a  = b ) // C4706
   {
   }
}
```

이 경고는 테스트 조건 주위에 괄호를 두는 경우에도 발생 합니다.

```cpp
// C4706b.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a  =  b ) ) // C4706
   {
   }
}
```

관계를 테스트 하 고 할당 하지 않으려면 연산자를 사용 `==` 합니다. 예를 들어, 다음 줄은 a와 b가 동일한 지를 테스트 합니다.

```cpp
// C4706c.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a == b )
   {
   }
}
```

테스트 값을 할당의 결과로 만들려면를 테스트 하 여 할당이 0이 아니거나 null이 아닌지 확인 합니다. 예를 들어 다음 코드는이 경고를 생성 하지 않습니다.

```cpp
// C4706d.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a = b ) != 0 )
   {
   }
}
```
