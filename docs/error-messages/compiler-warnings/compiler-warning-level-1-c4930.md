---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4930'
title: 컴파일러 경고(수준 1) C4930
ms.date: 11/04/2016
f1_keywords:
- C4930
helpviewer_keywords:
- C4930
ms.assetid: 89a206c9-c536-4186-8e81-1cde3e7f4f5b
ms.openlocfilehash: 9111b87ee2b281c7781e7115330634daefb14cc4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328064"
---
# <a name="compiler-warning-level-1-c4930"></a>컴파일러 경고(수준 1) C4930

' prototype ': 프로토타입화 된 함수를 호출 하지 않았습니다 (변수 정의가 의도 되었습니까?).

컴파일러가 사용 되지 않는 함수 프로토타입을 검색 했습니다. 프로토타입이 변수 선언으로 작성 된 경우에는 여는 괄호와 닫는 괄호를 제거 합니다.

다음 샘플에서는 C4930를 생성 합니다.

```cpp
// C4930.cpp
// compile with: /W1
class Lock {
public:
   int i;
};

void f() {
   Lock theLock();   // C4930
   // try the following line instead
   // Lock theLock;
}

int main() {
}
```

C4930는 컴파일러에서 함수 프로토타입 선언과 함수 호출을 구별할 수 없는 경우에도 발생할 수 있습니다.

다음 샘플에서는 C4930를 생성 합니다.

```cpp
// C4930b.cpp
// compile with: /EHsc /W1

class BooleanException
{
   bool _result;

public:
   BooleanException(bool result)
      : _result(result)
   {
   }

   bool GetResult() const
   {
      return _result;
   }
};

template<class T = BooleanException>
class IfFailedThrow
{
public:
   IfFailedThrow(bool result)
   {
      if (!result)
      {
         throw T(result);
      }
   }
};

class MyClass
{
public:
   bool MyFunc()
   {
      try
      {
         IfFailedThrow<>(MyMethod()); // C4930

         // try one of the following lines instead
         // IfFailedThrow<> ift(MyMethod());
         // IfFailedThrow<>(this->MyMethod());
         // IfFailedThrow<>((*this).MyMethod());

         return true;
      }
      catch (BooleanException e)
      {
         return e.GetResult();
      }
   }

private:
   bool MyMethod()
   {
      return true;
   }
};

int main()
{
   MyClass myClass;
   myClass.MyFunc();
}
```

위의 샘플에서 0 개 인수를 사용 하는 메서드의 결과는 명명 되지 않은 로컬 클래스 변수의 생성자에 인수로 전달 됩니다. 로컬 변수의 이름을 지정 하거나 적절 한 멤버 포인터 연산자와 함께 개체 인스턴스와 함께 메서드 호출에 접두사를 지정 하 여 호출을 명확 하 게 할 수 있습니다.
