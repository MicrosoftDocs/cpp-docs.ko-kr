---
title: 컴파일러 오류 C2666
ms.date: 11/04/2016
f1_keywords:
- C2666
helpviewer_keywords:
- C2666
ms.assetid: 78364d15-c6eb-439a-9088-e04a0176692b
ms.openlocfilehash: ebe41a4c4aa090e609d3352635d4e1fc06e22454
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743219"
---
# <a name="compiler-error-c2666"></a>컴파일러 오류 C2666

' identifier ': 숫자 오버 로드에 비슷한 변환이 있습니다.

오버 로드 된 함수 또는 연산자가 모호 합니다.   컴파일러가 모호성을 해결 하기 위해 정식 매개 변수 목록이 너무 유사할 수 있습니다.  이 오류를 해결 하려면 하나 이상의 실제 매개 변수를 명시적으로 캐스팅 합니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2666를 생성 합니다.

```cpp
// C2666.cpp
struct complex {
   complex(double);
};

void h(int,complex);
void h(double, double);

int main() {
   h(3,4);   // C2666
}
```

이 오류는 Visual Studio .NET 2003에 대해 수행 된 컴파일러 규칙 작업의 결과로 생성 될 수도 있습니다.

- 포인터 형식에 대 한 이진 연산자 및 사용자 정의 변환

- 자격 변환이 항등 변환과 동일 하지 않습니다.

이항 연산자 \<, > , =의 경우 \<=, and > 전달 된 매개 변수는 이제 피연산자의 형식으로 변환 하기 위해 사용자 정의 변환 연산자를 정의 하는 경우 피연산자의 형식으로 암시적으로 변환 됩니다. 이제 모호성이 발생할 수 있습니다.

Visual Studio .NET 2003 및 Visual Studio .NET 버전 Visual C++ 모두에서 유효한 코드의 경우 함수 구문을 사용 하 여 클래스 연산자를 명시적으로 호출 합니다.

```cpp
// C2666b.cpp
#include <string.h>
#include <stdio.h>

struct T
{
    T( const T& copy )
    {
        m_str = copy.m_str;
    }

    T( const char* str )
    {
        int iSize = (strlen( str )+ 1);
        m_str = new char[ iSize ];
        if (m_str)
            strcpy_s( m_str, iSize, str );
    }

    bool operator<( const T& RHS )
    {
        return m_str < RHS.m_str;
    }

    operator char*() const
    {
        return m_str;
    }

    char* m_str;
};

int main()
{
    T str1( "ABCD" );
    const char* str2 = "DEFG";

    // Error - Ambiguous call to operator<()
    // Trying to convert str1 to char* and then call
    // operator<( const char*, const char* )?
    //  OR
    // trying to convert str2 to T and then call
    // T::operator<( const T& )?

    if( str1 < str2 )   // C2666

    if ( str1.operator < ( str2 ) )   // Treat str2 as type T
        printf_s("str1.operator < ( str2 )\n");

    if ( str1.operator char*() < str2 )   // Treat str1 as type char*
        printf_s("str1.operator char*() < str2\n");
}
```

다음 샘플에서는 C2666를 생성 합니다.

```cpp
// C2666c.cpp
// compile with: /c

enum E
{
    E_A,   E_B
};

class A
{
    int h(const E e) const {return 0; }
    int h(const int i) { return 1; }
    // Uncomment the following line to resolve.
    // int h(const E e) { return 0; }

    void Test()
    {
        h(E_A);   // C2666
        h((const int) E_A);
        h((int) E_A);
    }
};
```
