---
description: '자세한 정보: C 및 c + +에 대 한 Microsoft 확장'
title: C 및 C++에 대한 Microsoft 확장
ms.date: 06/14/2018
helpviewer_keywords:
- or_eq operator
- ~ operator, extensions to C/C++
- '& operator, extensions to C/C++'
- '&= operator'
- iso646.h header
- Xor operator, Microsoft extensions to C/C++
- '!= operator'
- '! operator, extension to C++'
- Or operator, Microsoft extensions to C/C++
- ^ operator, extensions to C/C++
- ^= operator, C++ extensions
- xor_eq operator
- and_eq operator
- Microsoft extensions to C/C++
- '|= operator'
- '|| operator'
- And operator, extensions to C/C++
- NOT operator
- '&& operator'
- extensions, C language
- Visual C++, extensions to C/C++
- '| operator, extensions'
- not_eq operator
- Visual C, Microsoft extensions
- extensions
- compl method
ms.assetid: e811a74a-45ba-4c00-b206-2f2321b8689a
ms.openlocfilehash: fac6edbdfd559f3cebd18dcdc3b8cfca2a9336dd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190694"
---
# <a name="microsoft-extensions-to-c-and-c"></a>C 및 C++에 대한 Microsoft 확장

Visual C++는 다음과 같이 ANSI C 및 ANSI C++ 표준을 확장합니다.

## <a name="keywords"></a>키워드가

여러 키워드가 추가되었습니다. [키워드](../../cpp/keywords-cpp.md)목록에서 두 개의 선행 밑줄이 있는 키워드는 Visual C++ 확장명입니다.

## <a name="out-of-class-definition-of-static-const-integral-or-enum-members"></a>정적 const 정수 (또는 열거형) 멤버의 클래스 정의가 부족 합니다.

표준 (**/za**)에서 다음과 같이 데이터 멤버에 대 한 클래스 외부 정의를 만들어야 합니다.

```cpp
class CMyClass  {
   static const int max = 5;
   int m_array[max];
}
// . . .
const int CMyClass::max;   // out of class definition
```

**/Ze** 에서 클래스 외부 정의는 static, const 정수 및 const 열거형 데이터 멤버의 경우 선택 사항입니다. static 및 const인 열거형 및 정수만 클래스에서 이니셜라이저를 포함할 수 있습니다. 초기화 식은 const 식이어야 합니다.

헤더 파일에 클래스 외부 정의가 제공 되 고 헤더 파일이 여러 소스 파일에 포함 된 경우 오류를 방지 하려면 [selectany](../../cpp/selectany.md)을 사용 합니다. 예를 들어:

```cpp
__declspec(selectany) const int CMyClass::max = 5;
```

## <a name="casts"></a>캐스팅

C++ 컴파일러 및 C 컴파일러는 모두 이러한 종류의 비ANSI 캐스트를 지원합니다.

- l-value를 생성하기 위한 비ANSI 캐스트. 예를 들어:

   ```C
   char *p;
   (( int * ) p )++;
   ```

   > [!NOTE]
   > 이 확장은 C 언어에서만 사용할 수 있습니다. C++ 코드에서 다음 ANSI C 표준 형식을 사용해서 다른 형식에 대한 포인터인 것처럼 포인터를 수정할 수 있습니다.

   앞의 예제는 ANSI C 표준을 따르도록 다음과 같이 다시 작성할 수 있습니다.

   ```C
   p = ( char * )(( int * )p + 1 );
   ```

- 데이터 포인터에 대한 함수 포인터의 비ANSI 캐스트. 예를 들어:

   ```C
   int ( * pfunc ) ();
   int *pdata;
   pdata = ( int * ) pfunc;
   ```

   동일한 캐스트를 수행하고 ANSI 호환성을 유지 관리하려면 데이터 포인터로 캐스팅하기 전에 함수 포인터를 `uintptr_t`로 캐스팅할 수 있습니다.

   ```C
   pdata = ( int * ) (uintptr_t) pfunc;
   ```

## <a name="variable-length-argument-lists"></a>가변 길이 인수 목록

C++ 컴파일러와 C 컴파일러는 모두 대신 형식을 제공하는 함수 정의 다음에 인수의 변수 수를 지정하는 함수 선언자를 지정합니다.

```cpp
void myfunc( int x, ... );
void myfunc( int x, char * c )
{ }
```

## <a name="single-line-comments"></a>한 줄로 된 주석

C 컴파일러는 2개의 슬래시(//) 문자를 사용해서 시작되는 한 줄로 된 주석을 지원합니다.

```C
// This is a single-line comment.
```

## <a name="scope"></a>범위

C 컴파일러는 다음과 같은 범위 관련 기능을 지원합니다.

- 재정의의 extern 항목:

   ```C
   extern int clip();
   static int clip()
   {}
   ```

- 동일한 범위 내에서 무해 한 typedef 재정의 사용:

   ```C
   typedef int INT;
   typedef int INT;
   ```

- 함수 선언 자에는 파일 범위가 있습니다.

   ```C
   void func1()
   {
       extern int func2( double );
   }
   int main( void )
   {
       func2( 4 );    //  /Ze passes 4 as type double
   }                  //  /Za passes 4 as type int
   ```

- 비상수 식을 사용해서 초기화된 블록 범위 변수의 사용:

   ```C
   int clip( int );
   int bar( int );
   int main( void )
   {
       int array[2] = { clip( 2 ), bar( 4 ) };
   }
   int clip( int x )
   {
       return x;
   }
   int bar( int x )
   {
       return x;
   }
   ```

## <a name="data-declarations-and-definitions"></a>데이터 선언 및 정의

C 컴파일러는 다음과 같은 데이터 선언 및 정의 기능을 지원합니다.

- 이니셜라이저의 혼합 문자 및 문자열 상수:

   ```C
   char arr[5] = {'a', 'b', "cde"};
   ```

- 또는 이외의 기본 형식이 있는 비트 필드입니다 **`unsigned int`** **`signed int`** .

- 형식을 포함하지 않는 선언자:

   ```C
   x;
   int main( void )
   {
       x = 1;
   }
   ```

- 구조체 및 공용 구조체의 마지막 필드로 배열을 크기 배열 합니다.

   ```C
   struct zero
   {
       char *c;
       int zarray[];
   };
   ```

- 명명 되지 않은 (익명) 구조체:

   ```C
   struct
   {
       int i;
       char *s;
   };
   ```

- 명명 되지 않은 (익명) 공용 구조체:

   ```C
   union
   {
       int i;
       float fl;
   };
   ```

- 명명 되지 않은 멤버:

   ```C
   struct s
   {
      unsigned int flag : 1;
      unsigned int : 31;
   }
   ```

## <a name="intrinsic-floating-point-functions"></a>내장 부동 소수점 함수

C + + 컴파일러 및 c 컴파일러는 모두 `atan` `atan2` `cos` `exp` `log` `log10` `sin` `sqrt` `tan` **/oi** 가 지정 된 경우,,,,,,, 및 함수의 인라인 생성을 지원 합니다. C 컴파일러의 경우, 이러한 내장 함수는 `errno` 변수를 설정하지 않기 때문에 이러한 내장 함수가 사용될 경우 ANSI 규칙을 준수할 수 없게 됩니다.

## <a name="passing-a-non-const-pointer-parameter-to-a-function-that-expects-a-reference-to-a-const-pointer-parameter"></a>Const 포인터 매개 변수에 대 한 참조가 필요한 함수에 const가 아닌 포인터 매개 변수 전달

C + +에 대 한 확장입니다. 이 코드는 **/ze** 를 사용 하 여 컴파일합니다.

```cpp
typedef   int   T;

const T  acT = 9;      // A constant of type 'T'
const T* pcT = &acT;   // A pointer to a constant of type 'T'

void func2 ( const T*& rpcT )   // A reference to a pointer to a constant of type 'T'
{
   rpcT = pcT;
}

T*   pT;               // A pointer to a 'T'

void func ()
{
   func2 ( pT );      // Should be an error, but isn't detected
   *pT   = 7;         // Invalidly overwrites the constant 'acT'
}
```

## <a name="iso646h-not-enabled"></a>ISO646. H 사용 안 함

다음 연산자의 텍스트 형식을 사용 하려면 **/ze** 에서 iso646를 포함 해야 합니다.

- &&(및)

- &= (and_eq)

- & (bitand)

- &#124; (bitor)

- ~ (compl)

- ! 나타내지

- ! = (not_eq)

- &#124;&#124;(또는)

- &#124;= (or_eq)

- ^ (xor)

- ^ = (xor_eq)

## <a name="address-of-string-literal-has-type-const-char--not-const-char--"></a>문자열 리터럴의 주소에 const char [], const char (*) []가 아닌 형식이 있습니다.

다음 예제는 `char const (*)[4]` **/za** 아래에 있지만/ze에서 출력 됩니다 `char const [4]` . 

```cpp
#include <stdio.h>
#include <typeinfo>

int main()
{
    printf_s("%s\n", typeid(&"abc").name());
}
```

## <a name="see-also"></a>참고 항목

- [/Za,/Ze (언어 확장 사용 안 함)](za-ze-disable-language-extensions.md)
- [MSVC 컴파일러 옵션](compiler-options.md)
- [MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
