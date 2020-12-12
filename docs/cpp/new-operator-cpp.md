---
description: '자세히 알아보기: new 연산자 (c + +)'
title: new 연산자 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: 5bfc6fdc59348defc87d26dae1056ae80dab3ec5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268628"
---
# <a name="new-operator-c"></a>new 연산자 (C++)

사용 가능한 저장소에서 *형식 이름* 의 개체 또는 개체 배열에 대 한 메모리를 할당 하 고 개체에 대 한 적절 한 형식의 0이 아닌 포인터를 반환 합니다.

> [!NOTE]
> Microsoft c + + 구성 요소 확장은 **`new`** 키워드를 지원 하 여 vtable 슬롯 항목을 추가 합니다. 자세한 내용은 [new (vtable의 새 슬롯)](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md) 를 참조 하세요.

## <a name="syntax"></a>구문

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>설명

실패 한 경우는 **`new`** 0을 반환 하거나 예외를 throw 합니다. 자세한 내용은 [new 및 delete 연산자](../cpp/new-and-delete-operators.md) 를 참조 하세요. 사용자 지정 예외 처리 루틴을 작성 하 고 함수 이름을 인수로 사용 하 여 [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) 런타임 라이브러리 함수를 호출 하 여이 기본 동작을 변경할 수 있습니다.

관리 되는 힙에서 개체를 만드는 방법에 대 한 자세한 내용은 [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md)를 참조 하십시오.

**`new`** 를 사용 하 여 c + + 클래스 개체에 대 한 메모리를 할당 하는 경우 메모리를 할당 한 후 개체의 생성자가 호출 됩니다.

연산자를 사용 하 여 할당 된 메모리를 할당 해제 하려면 [delete](../cpp/delete-operator-cpp.md) 연산자를 사용 **`new`** 합니다.

다음 예제에서는 크기가 `dim`의 10배인 2차원 문자 배열을 할당한 다음 해제합니다. 다차원 배열을 할당할 때는 첫 번째를 제외한 모든 차원이 양수 값으로 계산되는 상수 식이어야 합니다. 맨 왼쪽 배열 차원은 양수 값으로 계산되는 임의의 식일 수 있습니다. 연산자를 사용 하 여 배열을 할당 하는 경우 **`new`** 첫 번째 차원이 0이 될 수 있습니다 **`new`** . 연산자는 고유한 포인터를 반환 합니다.

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

*형식 이름* 에는 **`const`** , **`volatile`** , 클래스 선언 또는 열거형 선언을 포함할 수 없습니다. 따라서 다음 식은 올바르지 않습니다.

```cpp
volatile char *vch = new volatile char[20];
```

**`new`** 연산자는 개체가 아니므로 참조 형식을 할당 하지 않습니다.

**`new`** 연산자는 함수를 할당 하는 데 사용할 수 없지만 함수에 대 한 포인터를 할당 하는 데 사용할 수 있습니다. 다음 예제에서는 정수를 반환하는 함수에 대한 7개의 포인터 배열을 할당한 다음 해제합니다.

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

추가 인수 없이 연산자를 사용 하 **`new`** 고 [/Gx](../build/reference/gx-enable-exception-handling.md), [/eha](../build/reference/eh-exception-handling-model.md)또는 [/EHs](../build/reference/eh-exception-handling-model.md) 옵션으로 컴파일하는 경우 생성자가 예외를 throw 하는 경우 컴파일러는 연산자를 호출 하는 코드를 생성 합니다 **`delete`** .

다음 목록에서는의 문법 요소에 대해 설명 합니다 **`new`** .

*배치가*<br/>
오버 로드 하는 경우 추가 인수를 전달 하는 방법을 제공 **`new`** 합니다.

*유형-이름*<br/>
기본 제공 또는 사용자 정의 형식 중에서 할당할 형식을 지정합니다. 형식 사양이 복잡한 경우 괄호로 묶어 바인딩 순서를 강제로 지정할 수 있습니다.

*initializer*<br/>
초기화된 개체의 값을 제공합니다. 배열에 대한 이니셜라이저는 지정할 수 없습니다. 이 **`new`** 연산자는 클래스에 기본 생성자가 있는 경우에만 개체의 배열을 만듭니다.

## <a name="example-allocate-and-free-a-character-array"></a>예: 문자 배열 할당 및 해제

다음 코드 예제는 문자 배열 및 `CName` 클래스 개체를 할당한 다음 해제합니다.

```cpp
// expre_new_Operator.cpp
// compile with: /EHsc
#include <string.h>

class CName {
public:
   enum {
      sizeOfBuffer = 256
   };

   char m_szFirst[sizeOfBuffer];
   char m_szLast[sizeOfBuffer];

public:
   void SetName(char* pszFirst, char* pszLast) {
     strcpy_s(m_szFirst, sizeOfBuffer, pszFirst);
     strcpy_s(m_szLast, sizeOfBuffer, pszLast);
   }

};

int main() {
   // Allocate memory for the array
   char* pCharArray = new char[CName::sizeOfBuffer];
   strcpy_s(pCharArray, CName::sizeOfBuffer, "Array of characters");

   // Deallocate memory for the array
   delete [] pCharArray;
   pCharArray = NULL;

   // Allocate memory for the object
   CName* pName = new CName;
   pName->SetName("Firstname", "Lastname");

   // Deallocate memory for the object
   delete pName;
   pName = NULL;
}
```

## <a name="example-new-operator"></a>예: `new` 연산자

연산자의 배치 새로운 형태를 사용 하는 경우 **`new`** 할당 크기 외에 인수를 포함 하는 폼에는 생성자가 예외를 throw 하는 경우 컴파일러에서 연산자의 배치 형태를 지원 하지 않습니다 **`delete`** . 예를 들어:

```cpp
// expre_new_Operator2.cpp
// C2660 expected
class A {
public:
   A(int) { throw "Fail!"; }
};
void F(void) {
   try {
      // heap memory pointed to by pa1 will be deallocated
      // by calling ::operator delete(void*).
      A* pa1 = new A(10);
   } catch (...) {
   }
   try {
      // This will call ::operator new(size_t, char*, int).
      // When A::A(int) does a throw, we should call
      // ::operator delete(void*, char*, int) to deallocate
      // the memory pointed to by pa2.  Since
      // ::operator delete(void*, char*, int) has not been implemented,
      // memory will be leaked when the deallocation cannot occur.

      A* pa2 = new(__FILE__, __LINE__) A(20);
   } catch (...) {
   }
}

int main() {
   A a;
}
```

## <a name="initializing-object-allocated-with-new"></a>new로 할당된 개체 초기화

선택적 *이니셜라이저* 필드는 연산자의 문법에 포함 됩니다 **`new`** . 사용자 정의 생성자를 사용하여 새 개체를 초기화할 수 있습니다. 초기화를 수행 하는 방법에 대 한 자세한 내용은 [이니셜라이저](../cpp/initializers.md)를 참조 하십시오. 다음 예에서는 연산자를 사용 하 여 초기화 식을 사용 하는 방법을 보여 줍니다 **`new`** .

```cpp
// expre_Initializing_Objects_Allocated_with_new.cpp
class Acct
{
public:
    // Define default constructor and a constructor that accepts
    //  an initial balance.
    Acct() { balance = 0.0; }
    Acct( double init_balance ) { balance = init_balance; }
private:
    double balance;
};

int main()
{
    Acct *CheckingAcct = new Acct;
    Acct *SavingsAcct = new Acct ( 34.98 );
    double *HowMuch = new double ( 43.0 );
    // ...
}
```

이 예제에서 개체는 `CheckingAcct` 연산자를 사용 하 여 할당 **`new`** 되지만 기본 초기화는 지정 되지 않습니다. 따라서 클래스의 기본 생성자인 `Acct()`가 호출됩니다. 그런 다음 명시적으로 34.98로 초기화된다는 점을 제외하고 `SavingsAcct` 개체가 같은 식으로 할당됩니다. 34.98는 형식 이므로 **`double`** 해당 형식의 인수를 사용 하는 생성자가 초기화를 처리 하기 위해 호출 됩니다. 마지막으로 비클래스 형식 `HowMuch`가 43.0으로 초기화됩니다.

개체가 클래스 형식이 고 해당 클래스에 생성자가 있는 경우 (앞의 예제에서와 같이) **`new`** 다음 조건 중 하나가 충족 되는 경우에만 연산자를 통해 개체를 초기화할 수 있습니다.

- 이니셜라이저에 제공된 인수는 생성자의 인수와 일치합니다.

- 클래스에 기본 생성자(인수 없이 호출할 수 있는 생성자)가 있습니다.

연산자를 사용 하 여 배열을 할당할 때 요소당 명시적 초기화를 수행할 수 없습니다 **`new`** . 기본 생성자 (있는 경우)만 호출 됩니다. 자세한 내용은 [기본 인수](../cpp/default-arguments.md) 를 참조 하세요.

메모리 할당이 실패 하는 경우 (**operator new** 는 값 0을 반환 함) 초기화를 수행 하지 않습니다. 존재하지 않는 데이터를 초기화하려는 시도를 막을 수 있습니다.

함수 호출과 마찬가지로 초기화된 식이 계산되는 순서가 정의되지 않습니다. 또한 메모리 할당을 수행하기 전에 완전히 계산되는 이 식에 의존하지 마십시오. 메모리 할당이 실패 하 고 연산자가 **`new`** 0을 반환 하는 경우 이니셜라이저의 일부 식이 완전히 계산 되지 않을 수 있습니다.

## <a name="lifetime-of-objects-allocated-with-new"></a>new로 할당된 개체 수명

연산자를 사용 하 여 할당 된 개체는 해당 개체가 **`new`** 정의 된 범위가 종료 될 때 제거 되지 않습니다. 연산자가 **`new`** 할당 하는 개체에 대 한 포인터를 반환 하기 때문에 프로그램은 이러한 개체에 액세스 하는 데 적합 한 범위의 포인터를 정의 해야 합니다. 예를 들어:

```cpp
// expre_Lifetime_of_Objects_Allocated_with_new.cpp
// C2541 expected
int main()
{
    // Use new operator to allocate an array of 20 characters.
    char *AnArray = new char[20];

    for( int i = 0; i < 20; ++i )
    {
        // On the first iteration of the loop, allocate
        //  another array of 20 characters.
        if( i == 0 )
        {
            char *AnotherArray = new char[20];
        }
    }

    delete [] AnotherArray; // Error: pointer out of scope.
    delete [] AnArray;      // OK: pointer still in scope.
}
```

`AnotherArray` 포인터가 예제 범위를 벗어나면 개체를 더 이상 삭제할 수 없습니다.

## <a name="how-new-works"></a>new 작동 방식

연산자를 포함 하는 식인 *할당 식* 은 다음 **`new`** 세 가지 작업을 수행 합니다.

- 할당할 개체에 대한 스토리지를 찾고 예약합니다. 이 단계가 완료되면 올바른 양의 스토리지가 할당되지만 아직 개체는 아닙니다.

- 개체를 초기화합니다. 초기화가 완료되면 할당된 스토리지가 개체가 되는 데 충분한 정보가 있습니다.

- *새 형식 이름* 또는 *형식 이름* 에서 파생 된 포인터 형식의 개체에 대 한 포인터를 반환 합니다. 프로그램에서는 이 포인터를 사용하여 새로 할당된 개체에 액세스합니다.

**`new`** 연산자는 **new** 함수를 호출 합니다. 모든 형식의 배열 및, 또는 형식이 아닌 개체에 대해 **`class`** **`struct`** **`union`** 전역 함수인 **:: operator new** 가 호출 되어 저장소를 할당 합니다. 클래스 형식 개체는 클래스 별로 고유한 **operator 새** 정적 멤버 함수를 정의할 수 있습니다.

컴파일러가 형식 형식의 개체를 **`new`** 할당 하는 연산자를 발견 하면  `type` **:: operator new (sizeof (** ))에 대 한 호출을 발생 `type`  하거나, 사용자 정의 **연산자 new** 가 정의 되지 않은 경우 **:: operator new (sizeof (** `type` **))** 를 호출 합니다. 따라서 연산자는 **`new`** 개체에 대해 올바른 크기의 메모리를 할당할 수 있습니다.

> [!NOTE]
> **Operator new** 에 대 한 인수는 형식입니다 `size_t` . 이 형식은,,,,,,, 및에 정의 되어 \<direct.h> \<malloc.h> \<memory.h> \<search.h> \<stddef.h> \<stdio.h> \<stdlib.h> \<string.h> \<time.h> 있습니다.

문법의 옵션은 *배치* 지정을 허용 합니다 ( [new 연산자](../cpp/new-operator-cpp.md)에 대 한 문법 참조). *Placement* 매개 변수는 **operator new** 의 사용자 정의 구현에만 사용할 수 있습니다. 추가 정보를 **operator new** 에 전달할 수 있습니다. 와 같은 *배치* 필드가 있는 식은 `T *TObject = new ( 0x0040 ) T;` `T *TObject = T::operator new( sizeof( T ), 0x0040 );` 클래스 T에 멤버 연산자 new가 있는 경우로 변환 되 고, 그렇지 않으면로 변환 됩니다 `T *TObject = ::operator new( sizeof( T ), 0x0040 );` .

*배치* 필드의 원래 용도는 하드웨어 종속 개체가 사용자 지정 주소에서 할당 되도록 허용 하는 것입니다.

> [!NOTE]
> 앞의 예제에서는 *배치* 필드에 인수를 하나만 표시 하지만 이러한 방식으로 **연산자** 에 전달할 수 있는 추가 인수 개수에는 제한이 없습니다.

**Operator new** 가 클래스 형식에 대해 정의 된 경우에도이 예제의 형태를 사용 하 여 전역 연산자를 사용할 수 있습니다.

```cpp
T *TObject =::new TObject;
```

범위 결정 연산자 ()는 `::` 전역 연산자를 강제로 사용 합니다 **`new`** .

## <a name="see-also"></a>참조

[단항 연산자가 있는 식](../cpp/expressions-with-unary-operators.md)<br/>
[키워드](../cpp/keywords-cpp.md)<br/>
[new 및 delete 연산자](../cpp/new-and-delete-operators.md)
