---
description: '자세한 정보: 컴파일러 오류 C3490'
title: 컴파일러 오류 C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: 03896872fd0c683e3011aa7edbacb6a0a01ceaef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113365"
---
# <a name="compiler-error-c3490"></a>컴파일러 오류 C3490

'var'는 const 개체를 통해 액세스되고 있으므로 수정할 수 없습니다.

메서드에서 선언 된 람다 식은 **`const`** 변경할 수 없는 멤버 데이터를 수정할 수 없습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- **`const`** 메서드 선언에서 한정자를 제거 합니다.

## <a name="examples"></a>예제

다음 예제에서는 메서드의 멤버 변수를 수정 하기 때문에 C3490를 생성 합니다 `_i` **`const`** .

```cpp
// C3490a.cpp
// compile with: /c

class C
{
   void f() const
   {
      auto x = [=]() { _i = 20; }; // C3490
   }

   int _i;
};
```

다음 예제에서는 **`const`** 메서드 선언에서 한정자를 제거 하 여 C3490를 확인 합니다.

```cpp
// C3490b.cpp
// compile with: /c

class C
{
   void f()
   {
      auto x = [=]() { _i = 20; };
   }

   int _i;
};
```

## <a name="see-also"></a>참조

[람다 식](../../cpp/lambda-expressions-in-cpp.md)
