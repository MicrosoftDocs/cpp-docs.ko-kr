---
description: '다음에 대 한 자세한 정보: User-Defined 연산자 (c + +/CLI)'
title: 사용자 정의 연산자(C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined operators under /clr
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
ms.openlocfilehash: e94a4d28517fc253fb8284a604b01a5f9d76de22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204227"
---
# <a name="user-defined-operators-ccli"></a>사용자 정의 연산자(C++/CLI)

관리 되는 형식에 대 한 사용자 정의 연산자는 정적 멤버 또는 인스턴스 멤버 또는 전역 범위에서 허용 됩니다. 그러나 Visual C++ 이외의 언어로 작성 된 클라이언트에 대 한 메타 데이터를 통해 정적 연산자만 액세스할 수 있습니다.

참조 형식에서 정적 사용자 정의 연산자의 매개 변수 중 하나는 다음 중 하나 여야 합니다.

- `type`바깥쪽 형식의 인스턴스에 대 한 핸들 (^)입니다.

- 참조 형식 간접 참조 ( `type` ^& 또는 형식 ^%) 바깥쪽 형식의 인스턴스에 대 한 핸들입니다.

값 형식에서 정적 사용자 정의 연산자의 매개 변수 중 하나는 다음 중 하나 여야 합니다.

- 바깥쪽 값 형식과 동일한 형식입니다.

- 바깥쪽 형식에 대 한 포인터 형식 간접 참조 ( `type` ^)입니다.

- 바깥쪽 형식에 대 한 참조 형식 간접 참조 ( `type` % 또는 `type`&)입니다.

- 핸들에 대 한 참조 형식 간접 참조 ( `type` ^% 또는 `type` ^&)입니다.

다음 연산자를 정의할 수 있습니다.

|연산자|단항/이진 형식 인가요?|
|--------------|--------------------------|
|!|단항|
|!=|이진|
|%|이진|
|&|단항 및 이항|
|&&|이진|
|*|단항 및 이항|
|+|단항 및 이항|
|++|단항|
|,|이진|
|-|단항 및 이항|
|--|단항|
|->|단항|
|/|이진|
|<|이진|
|<<|이진|
|\<=|이진|
|=|이진|
|==|이진|
|>|이진|
|>=|이진|
|>>|이진|
|^|이진|
|false|단항|
|true|단항|
|&#124;|이진|
|&#124;&#124;|이진|
|~|단항|

## <a name="example-user-defined-operators"></a>예: 사용자 정의 연산자

```cpp
// mcppv2_user-defined_operators.cpp
// compile with: /clr
using namespace System;
public ref struct X {
   X(int i) : m_i(i) {}
   X() {}

   int m_i;

   // static, binary, user-defined operator
   static X ^ operator + (X^ me, int i) {
      return (gcnew X(me -> m_i + i));
   }

   // instance, binary, user-defined operator
   X^ operator -( int i ) {
      return gcnew X(this->m_i - i);
   }

   // instance, unary, user-defined pre-increment operator
   X^ operator ++() {
      return gcnew X(this->m_i++);
   }

   // instance, unary, user-defined post-increment operator
   X^ operator ++(int i) {
      return gcnew X(this->m_i++);
   }

   // static, unary user-defined pre- and post-increment operator
   static X^ operator-- (X^ me) {
      return (gcnew X(me -> m_i - 1));
   }
};

int main() {
   X ^hX = gcnew X(-5);
   System::Console::WriteLine(hX -> m_i);

   hX = hX + 1;
   System::Console::WriteLine(hX -> m_i);

   hX = hX - (-1);
   System::Console::WriteLine(hX -> m_i);

   ++hX;
   System::Console::WriteLine(hX -> m_i);

   hX++;
   System::Console::WriteLine(hX -> m_i);

   hX--;
   System::Console::WriteLine(hX -> m_i);

   --hX;
   System::Console::WriteLine(hX -> m_i);
}
```

```Output
-5
-4
-3
-2
-1
-2
-3
```

## <a name="example-operator-synthesis"></a>예: 연산자 합성

다음 샘플에서는 **/clr** 을 사용 하 여 컴파일하는 경우에만 사용할 수 있는 연산자 합성을 보여 줍니다. 연산자 합성은 이항 연산자의 할당 형식 (정의 되지 않은 경우)을 만듭니다. 여기서 할당 연산자의 왼쪽에는 CLR 형식이 있습니다.

```cpp
// mcppv2_user-defined_operators_2.cpp
// compile with: /clr
ref struct A {
   A(int n) : m_n(n) {};
   static A^ operator + (A^ r1, A^ r2) {
      return gcnew A( r1->m_n + r2->m_n);
   };
   int m_n;
};

int main() {
   A^ a1 = gcnew A(10);
   A^ a2 = gcnew A(20);

   a1 += a2;   // a1 = a1 + a2   += not defined in source
   System::Console::WriteLine(a1->m_n);
}
```

```Output
30
```

## <a name="see-also"></a>참조

[클래스 및 구조체](../extensions/classes-and-structs-cpp-component-extensions.md)
