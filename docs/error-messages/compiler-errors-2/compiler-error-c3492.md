---
description: '자세한 정보: 컴파일러 오류 C3492'
title: 컴파일러 오류 C3492
ms.date: 11/04/2016
f1_keywords:
- C3492
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
ms.openlocfilehash: bceeded1de628604c29ef124adacc23ded72f15b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113157"
---
# <a name="compiler-error-c3492"></a>컴파일러 오류 C3492

'var': 익명 공용 구조체의 멤버를 캡처할 수 없습니다.

명명되지 않은 공용 구조체의 멤버를 캡처할 수 없습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 공용 구조체에 이름을 지정하고 완전한 공용 구조체를 람다 식의 캡처 목록에 전달합니다.

## <a name="examples"></a>예제

다음 예제에서는 익명 공용 구조체의 멤버를 캡처하므로 C3492를 생성합니다.

```cpp
// C3492a.cpp

int main()
{
   union
   {
      char ch;
      int x;
   };

   ch = 'y';
   [&x](char ch) { x = ch; }(ch); // C3492
}
```

다음 예제에서는 공용 구조체에 이름을 지정하고 완전한 공용 구조체를 람다 식의 캡처 목록에 전달하여 C3492를 해결합니다.

```cpp
// C3492b.cpp

int main()
{
   union
   {
      char ch;
      int x;
   } u;

   u.ch = 'y';
   [&u](char ch) { u.x = ch; }(u.ch);
}
```

## <a name="see-also"></a>참조

[람다 식](../../cpp/lambda-expressions-in-cpp.md)
