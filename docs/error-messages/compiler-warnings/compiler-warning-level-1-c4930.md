---
title: 컴파일러 경고 (수준 1) C4930 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4930
dev_langs:
- C++
helpviewer_keywords:
- C4930
ms.assetid: 89a206c9-c536-4186-8e81-1cde3e7f4f5b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33c202cc6f062ac13bef3a73e4509e4ba870e2d6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090193"
---
# <a name="compiler-warning-level-1-c4930"></a>컴파일러 경고(수준 1) C4930

'프로토타입': 프로토타입 함수가 호출 되지 않습니다 (의도 되는 변수 정의 었 나요?)

컴파일러는 사용 되지 않는 함수 프로토타입을 발견 했습니다. 변수 선언으로 프로토타입을 사용 된 경우 열기/닫기 괄호를 제거 합니다.

다음 샘플에서는 C4930 오류가 생성 됩니다.

```
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

컴파일러는 함수 프로토타입 선언 하 고 함수 호출을 구별할 수 없습니다 하는 경우에 C4930 발생할 수 있습니다.

다음 샘플에서는 C4930 오류가 생성 됩니다.

```
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

위 예제에서 인수를 사용 하는 메서드의 결과 변수를 명명 되지 않은 로컬 클래스의 생성자에 인수로 전달 됩니다. 지역 변수 이름을 지정 하거나 적절 한 멤버 포인터 연산자와 함께 개체 인스턴스를 사용 하 여 메서드 호출을 접두사로 하 여 호출 명확 하 게 지정할 수 있습니다.