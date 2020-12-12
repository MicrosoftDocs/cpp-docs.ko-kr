---
description: '자세히 알아보기: protected (c + +)'
title: protected (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 17b74db6ae257e757253c12fdfeb4fa9bac2a3db
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299113"
---
# <a name="protected-c"></a>protected (C++)

## <a name="syntax"></a>구문

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>설명

**`protected`** 키워드는 다음 액세스 지정자 (  **`public`** 또는 **`private`** ) 또는 클래스 정의의 끝까지 멤버 목록의 클래스 멤버에 대 한 액세스를 지정 합니다. 로 선언 된 클래스 멤버 **`protected`** 는 다음 에서만 사용할 수 있습니다.

- 원래 이 멤버를 선언한 클래스의 멤버 함수

- 원래 이 멤버를 선언한 클래스의 friend

- 원래 이 멤버를 선언한 클래스에서 공용 또는 보호된 액세스로 파생된 클래스

- 보호된 멤버에 대해 전용 액세스 권한이 있으며 전용으로 직접 파생된 클래스

기본 클래스의 이름 앞에 **`protected`** 오는 키워드는 기본 클래스의 공용 및 보호 된 멤버가 파생 클래스의 보호 된 멤버 임을 지정 합니다.

Protected 멤버는 **`private`** 선언 된 클래스의 멤버에만 액세스할 수 있는 멤버로 서는 안 되지만 **`public`** 모든 함수에서 액세스할 수 있는 멤버 처럼 public이 아닙니다.

로 선언 된 보호 된 멤버는 **`static`** 파생 클래스의 friend 또는 멤버 함수에서 액세스할 수 있습니다. 로 선언 되지 않은 보호 된 멤버 **`static`** 는 파생 클래스의 포인터, 참조 또는 개체를 통해서만 파생 된 클래스의 friend 및 멤버 함수에 액세스할 수 있습니다.

관련 정보는 [friend](../cpp/friend-cpp.md), [public](../cpp/public-cpp.md), [private](../cpp/private-cpp.md)및 [클래스 멤버에 대 한 액세스 제어](member-access-control-cpp.md)의 멤버 액세스 테이블을 참조 하세요.

## <a name="clr-specific"></a>/clr 관련

CLR 형식에서 c + + 액세스 지정자 키워드 ( **`public`** , **`private`** 및 **`protected`** )는 어셈블리와 관련 하 여 형식과 메서드를 표시 하는 데 영향을 줄 수 있습니다. 자세한 내용은 [Member Access Control](member-access-control-cpp.md)를 참조 하세요.

> [!NOTE]
> [/LN](../build/reference/ln-create-msil-module.md) 로 컴파일된 파일은이 동작의 영향을 받지 않습니다. 이 경우 관리되는 클래스(공용 또는 전용)가 모두 표시됩니다.

## <a name="end-clr-specific"></a>END /clr 관련

## <a name="example"></a>예제

```cpp
// keyword_protected.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class X {
public:
   void setProtMemb( int i ) { m_protMemb = i; }
   void Display() { cout << m_protMemb << endl; }
protected:
   int  m_protMemb;
   void Protfunc() { cout << "\nAccess allowed\n"; }
} x;

class Y : public X {
public:
   void useProtfunc() { Protfunc(); }
} y;

int main() {
   // x.m_protMemb;         error, m_protMemb is protected
   x.setProtMemb( 0 );   // OK, uses public access function
   x.Display();
   y.setProtMemb( 5 );   // OK, uses public access function
   y.Display();
   // x.Protfunc();         error, Protfunc() is protected
   y.useProtfunc();      // OK, uses public access function
                        // in derived class
}
```

## <a name="see-also"></a>참고 항목

[클래스 멤버에 대한 액세스 제어](member-access-control-cpp.md)<br/>
[키워드](../cpp/keywords-cpp.md)
