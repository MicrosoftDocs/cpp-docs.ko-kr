---
description: '자세한 정보: 컴파일러 오류 C2248'
title: 컴파일러 오류 C2248
ms.date: 11/04/2016
f1_keywords:
- C2248
helpviewer_keywords:
- C2248
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
ms.openlocfilehash: f2d840195fd6cdeb4cc8e1e90a06a502378ac634
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337605"
---
# <a name="compiler-error-c2248"></a>컴파일러 오류 C2248

'*member*': '*class*' 클래스에 선언 된 '*access_level*' 멤버에 액세스할 수 없습니다.

파생 클래스의 멤버는 **`private`** 기본 클래스의 멤버에 액세스할 수 없습니다. **`private`** 또는 **`protected`** 클래스 인스턴스의 멤버에는 액세스할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 클래스 외부에서 클래스의 private 또는 protected 멤버에 액세스할 때 C2248를 생성 합니다. 이 문제를 해결 하려면 클래스 외부에서 이러한 멤버에 직접 액세스 하지 마십시오. Public 멤버 데이터 및 멤버 함수를 사용 하 여 클래스와 상호 작용 합니다.

```cpp
// C2248_access.cpp
// compile with: cl /EHsc /W4 C2248_access.cpp
#include <stdio.h>

class X {
public:
    int  m_publicMember;
    void setPrivateMember( int i ) {
        m_privateMember = i;
        printf_s("\n%d", m_privateMember);
    }
protected:
    int  m_protectedMember;

private:
    int  m_privateMember;
} x;

int main() {
    x.m_publicMember = 4;
    printf_s("\n%d", x.m_publicMember);
    x.m_protectedMember = 2; // C2248 m_protectedMember is protected
    x.m_privateMember = 3;   // C2248  m_privMemb is private
    x.setPrivateMember(0);   // OK uses public access function
}
```

C2248를 노출 하는 또 다른 규칙 문제는 템플릿 친구 및 전문화를 사용 하는 것입니다. 이 문제를 해결 하려면 빈 템플릿 매개 변수 목록 <> 또는 특정 템플릿 매개 변수를 사용 하 여 friend 템플릿 함수를 선언 합니다.

```cpp
// C2248_template.cpp
// compile with: cl /EHsc /W4 C2248_template.cpp
template<class T>
void f(T t) {
    t.i;   // C2248
}

struct S {
private:
    int i;

public:
    S() {}
    friend void f(S);   // refer to the non-template function void f(S)
    // To fix, comment out the previous line and
    // uncomment the following line.
    // friend void f<S>(S);
};

int main() {
    S s;
    f<S>(s);
}
```

C2248를 노출 하는 또 다른 규칙 문제는 클래스의 friend를 선언 하려고 시도 하 고 클래스가 클래스 범위의 friend 선언에 표시 되지 않는 경우입니다. 이 문제를 해결 하려면 바깥쪽 클래스에 관계를 부여 합니다.

```cpp
// C2248_enclose.cpp
// compile with: cl /W4 /c C2248_enclose.cpp
class T {
    class S {
        class E {};
    };
    friend class S::E;   // C2248
};

class A {
    class S {
        class E {};
        friend class A;  // grant friendship to enclosing class
    };
    friend class S::E;   // OK
};
```
