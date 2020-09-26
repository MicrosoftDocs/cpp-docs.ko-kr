---
title: Visual C++ 2003 ~ 2015의 새로운 기능
ms.date: 07/02/2019
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
ms.openlocfilehash: eb76e5455f053717859d0ac571b9d1110d11c33b
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352637"
---
# <a name="visual-c-what39s-new-2003-through-2015"></a>Visual C++ 2003 ~ 2015의 새로운 기능

이 페이지에는 Visual Studio 2015에서 2003까지 모든 버전의 Visual C++에 대한 "새로운 기능" 페이지가 모두 수집되어 있습니다. 이 정보는 이전 버전의 Visual Studio에서 업그레이드하는 데 유용한 경우에 편의를 위해 제공됩니다.

> [!NOTE]
> 현재 버전의 Visual Studio에 대한 자세한 내용은 [Visual Studio의 Visual C++에 대한 새로운 기능](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) 및 [Visual Studio의 Visual C++에서 규칙 향상](../overview/cpp-conformance-improvements.md)을 참조하세요.

## <a name="whats-new-for-c-in-visual-studio-2015"></a>Visual Studio 2015의 새로운 C++ 기능

Visual Studio 2015 이상 버전에서 컴파일러 규칙이 지속적으로 향상됨으로써 컴파일러에서 기존의 소스 코드를 인식하는 방식이 변경되는 경우가 있습니다. 이로 인해 빌드 중 새로운 오류 또는 다른 오류가 발생하거나, 이전에 빌드되어 올바르게 실행되는 것처럼 보이는 코드가 다르게 동작할 수도 있습니다.

다행히 이러한 차이는 대부분의 소스 코드에 거의 또는 전혀 영향을 주지 않으며, 차이를 해결하기 위해 소스 코드 변경이나 기타 변경이 필요한 경우에도 대체로 간단히 처리할 수 있는 사소한 수정입니다. 이전에는 허용되는 소스 코드였지만 변경해야 할 수 있는 코드 *(이전)* 및 수정 코드 *(이후)* 의 많은 예가 포함되어 있습니다.

이러한 차이가 소스 코드나 다른 빌드 아티팩트에 영향을 줄 수도 있지만 Visual C++ 버전 업데이트 간의 이진 호환성에는 영향을 주지 않습니다. 보다 심각한 종류의 변경인 *주요 변경 내용*은 이진 호환성에 영향을 줄 수 있지만 이러한 종류의 이진 호환성 중단은 Visual C++의 주 버전 간에만 발생합니다. 예를 들어 Visual C++ 2013과 Visual C++ 2015 간에 발생합니다. Visual C++ 2013과 Visual C++ 2015 사이에 발생한 주요 변경 내용에 대한 자세한 내용은 [Visual C++ 변경 기록 2003 - 2015](../porting/visual-cpp-change-history-2003-2015.md)를 참조하세요.

- [Visual Studio 2015의 규칙 향상](#VS_RTM)

- [Visual Studio 2015 업데이트 1의 규칙 향상](#VS_Update1)

- [Visual Studio 2015 업데이트 2의 규칙 향상](#VS_Update2)

- [Visual Studio 2015 업데이트 3의 규칙 향상](#VS_Update3)

### <a name="conformance-improvements-in-visual-studio-2015"></a><a name="VS_RTM"></a> Visual Studio 2015의 규칙 향상

- **/Zc:forScope- 옵션**

   `/Zc:forScope-` 컴파일러 옵션은 더 이상 사용되지 않으므로 이후 릴리스에서 제거될 예정입니다.

   ```output
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
   ```

   옵션은 대개 표준에 따라 범위를 벗어나야 하는 지점 뒤에서 루프 변수를 사용하는 비표준 코드를 허용하려고 사용됩니다. `/Za`를 사용하지 않으면 루프 끝에 for 루프 변수를 항상 사용할 수 있으므로 `/Za` 옵션으로 컴파일할 경우에만 필요합니다. 표준 준수가 중요하지 않으면(예: 코드가 다른 컴파일러에 이식 가능하지 않은 경우) `/Za` 옵션을 해제하거나 **언어 확장 사용 안 함** 속성을 **아니요**로 설정할 수 있습니다. 이식 가능한 표준 규격 코드를 작성해야 하면 변수의 선언을 루프 외부 지점으로 이동하여 표준을 따르도록 코드를 다시 작성해야 합니다.

   ```cpp
    // zc_forScope.cpp
    // compile with: /Zc:forScope- /Za
    // C2065 expected
    int main() {
       // Uncomment the following line to resolve.
       // int i;
       for (int i =0; i < 1; i++)
          ;
       i = 20;   // i has already gone out of scope under /Za
    }
   ```

- **/Zg 컴파일러 옵션**

   `/Zg` 컴파일러 옵션(함수 프로토타입 생성)은 더 이상 사용할 수 없습니다. 이 컴파일러 옵션은 이미 사용되지 않습니다.

- mstest.exe를 사용하여 명령줄에서 C++/CLI에 대한 단위 테스트를 더 이상 실행할 수 없습니다. 대신 vstest.console.exe를 사용합니다.

- **mutable 키워드**

   **`mutable`** 이전에 오류 없이 컴파일된 위치에서는 저장소 클래스 지정 자가 더 이상 허용 되지 않습니다. 현재 컴파일러에서는 오류 C2071(스토리지 클래스가 잘못되었습니다.)을 표시합니다. 표준에 따라 mutable 지정자는 클래스 데이터 멤버의 이름에만 적용되고 const 또는 static으로 선언된 이름과 참조 멤버에는 적용할 수 없습니다.

   예를 들어, 다음 코드를 고려하세요.

   ```cpp
    struct S {
        mutable int &r;
    };
   ```

   이전 Microsoft C++ 컴파일러 버전에서는 이를 허용했으나 현재 컴파일러에서는 다음 오류를 표시합니다.

   ```Output
    error C2071: 'S::r': illegal storage class
   ```

   오류를 해결 하려면 중복 키워드를 제거 하면 됩니다 **`mutable`** .

- **char_16_t 및 char32_t**

   **`char16_t`** **`char32_t`** 이러한 형식은 이제 기본 제공으로 처리 되므로 typedef에서 또는 별칭으로 더 이상 사용할 수 없습니다. 일반적으로 사용자와 라이브러리 작성자는 **`char16_t`** 및 **`char32_t`** `uint16_t` 를 각각 및의 별칭으로 정의 하는 것이 일반적 이었습니다 `uint32_t` .

   ```cpp
    #include <cstdint>

    typedef uint16_t char16_t; //C2628
    typedef uint32_t char32_t; //C2628

    int main(int argc, char* argv[])
    {
    uint16_t x = 1; uint32_t y = 2;
    char16_t a = x;
    char32_t b = y;
    return 0;
    }
   ```

   코드를 업데이트 하려면 선언을 제거 하 **`typedef`** 고 이러한 이름과 충돌 하는 다른 식별자의 이름을 바꿉니다.

- **비형식 템플릿 매개 변수**

   이제는 비형식 템플릿 매개 변수가 포함된 특정 코드에 명시적 템플릿 인수를 제공하면 형식 호환성 검사가 정확하게 수행됩니다. 예를 들어 다음 코드는 이전 Visual C++ 버전에서는 오류 없이 컴파일되었습니다.

   ```cpp
    struct S1
    {
        void f(int);
        void f(int, int);
    };

    struct S2
    {
        template <class C, void (C::*Function)(int) const> void f() {}
    };

    void f()
    {
        S2 s2;
        s2.f<S1, &S1::f>();
    }
   ```

   템플릿 매개 변수 형식이 템플릿 인수와 일치하지 않기 때문에 현재 컴파일러에서 제대로 오류를 표시합니다. 매개 변수는 const 멤버의 포인터이나 f 함수는 비const입니다.

   ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
   ```

   코드에서 이 오류를 해결하려면 사용하는 템플릿 인수 형식이 템플릿 매개 변수의 선언된 형식과 일치해야 합니다.

- **`__declspec(align)`**

   컴파일러가 함수에서 `__declspec(align)` 을 더 이상 허용하지 않습니다. 이는 항상 무시되었지만 현재는 컴파일러 오류가 생성됩니다.

   ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
   ```

   이 문제를 수정하려면 함수 선언에서 `__declspec(align)` 을 제거합니다. 아무런 영향이 없으므로 제거해도 아무것도 변경되지 않습니다.

- **예외 처리**

   예외 처리에 대한 몇 가지 변경 내용이 있습니다. 먼저 예외 개체는 복사 가능하거나 이동 가능해야 합니다. 다음 코드는 Visual Studio 2013에서 컴파일되지만 Visual Studio 2015에서는 컴파일되지 않습니다.

   ```cpp
    struct S {
    public:
        S();
    private:
        S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
   ```

   문제는 복사 생성자가 private이라는 점이므로 일반적인 예외 처리 과정으로는 개체를 복사할 수 없습니다. 복사 생성자가 선언 된 경우에도 마찬가지 **`explicit`** 입니다.

   ```cpp
    struct S {
        S();
        explicit S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
   ```

   코드를 업데이트 하려면 예외 개체에 대 한 복사 생성자가 public이 고 표시 되지 않았는지 확인 **`explicit`** 합니다.

   값으로 예외를 catch하려면 예외 개체가 복사 가능해야 합니다. 다음 코드는 Visual Studio 2013에서 컴파일되지만 Visual Studio 2015에서는 컴파일되지 않습니다.

   ```cpp
    struct B {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {
    };

    int main()
    {
        try
        {
        }
        catch (D d) // error
        {
        }
    }
   ```

   에 대 한 매개 변수 형식을 참조로 변경 하면이 문제를 해결할 수 있습니다 **`catch`** .

   ```cpp
    catch(D& d)
    {
    }
   ```

- **매크로 뒤의 문자열 리터럴**

   현재 컴파일러는 사용자 정의 리터럴을 지원합니다. 따라서 중간 공백 없이 매크로 뒤의 문자열 리터럴은 오류나 예기치 않은 결과를 생성할 수 있는 사용자 정의 리터럴로 해석됩니다. 예를 들어 이전 컴파일러에서는 다음 코드가 성공적으로 컴파일되었습니다.

   ```cpp
    #define _x "there"
    char* func() {
        return "hello"_x;
    }
    int main()
    {
        char * p = func();
        return 0;
    }
   ```

   컴파일러에서 이 코드는 매크로 뒤의 문자열 리터럴 "hello"로 해석되고 “there”로 확장되었고 두 문자열 리터럴은 하나로 연결되었습니다. Visual Studio 2015에서 컴파일러는 이 코드를 사용자 정의 리터럴로 해석하지만 일치하는 사용자 정의 리터럴 _x가 정의되지 않았으므로 오류가 발생합니다.

   ```cpp
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?

   ```

   이 문제를 수정하려면 문자열 리터럴과 매크로 사이에 공백을 추가합니다.

- **인접 문자열 리터럴**

   이전과 비슷하게 문자열 구문 분석의 관련 변경 내용 때문에 공백이 없는 인접 문자열 리터럴(전각 또는 반각 문자 문자열 리터럴)은 이전 Visual C++ 릴리스에서 하나의 연결된 문자열로 해석되었습니다. Visual Studio 2015에서는 현재 두 문자열 사이에 공백을 추가해야 합니다. 예를 들어 다음 코드를 변경해야 합니다.

   ```cpp
    char * str = "abc""def";
   ```

   두 문자열 사이에 공백을 추가하면 됩니다.

   ```cpp
    char * str = "abc" "def";
   ```

- **Placement new 및 delete**

   **`delete`** 연산자가 c + + 14 표준을 준수 하도록 변경 되었습니다. 표준 변경에 대한 자세한 내용은 [C++ 크기 지정된 할당 해제](https://isocpp.org/files/papers/n3778.html)(영문)를 참조하세요. 변경 내용에는 **`delete`** 크기 매개 변수를 사용 하는 전역 연산자의 폼이 추가 됩니다. 주요 변경 내용은 이전에 배치 new 연산자와 일치 하는 것과 같은 서명을 사용 하 여 이전에 배치 new 연산자를 사용 하는 경우 컴파일러 **`delete`** 오류 (C2956)를 받게 됩니다 .이는 컴파일러가 적절 **placement new** 한 일치 연산자를 식별 하는 코드의 위치 이기 때문입니다 **placement new** **`delete`** .

   `void operator delete(void *, size_t)` 함수는 C++11의 **placement new** 함수 `void * operator new(size_t, size_t)`에 해당하는 **placement delete** 연산자였습니다. C + + 14 크기 할당 취소를 사용 하는 경우이 **`delete`** 함수는 이제 *일반적인 할당 취소 함수* (global **`delete`** 연산자)입니다. 표준에서는 **배치 new** 를 사용 하 여 해당 함수를 조회 하 **`delete`** 고 일반적인 할당 취소 함수를 찾으면 프로그램의 형식이 잘못 됩니다.

   예를 들어 코드에서 **placement new** 및 **placement delete**를 둘 다 정의한다고 가정합니다.

   ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
   ```

   사용자가 정의한 **배치 delete** 연산자와 새 전역 크기 연산자 사이에 함수 서명이 일치 하기 때문에 문제가 발생 합니다 **`delete`** . `size_t` **배치 new** 및 연산자에 대해 이외의 다른 형식을 사용할 수 있는지 여부를 고려 **`delete`** 합니다.  의 형식은 `size_t` **`typedef`** 컴파일러에 따라 다르며 **`typedef`** Visual C++의에 대 한입니다 **`unsigned int`** . 이 문제를 해결하려면 다음과 같은 열거된 형식을 사용하는 것이 좋습니다.

   ```cpp
    enum class my_type : size_t {};
   ```

   그런 다음 배치의 정의를 변경 하 **`new`** 고 **`delete`** 이 유형을 대신 두 번째 인수로 사용 `size_t` 합니다. 새 형식 (예:를 사용 하 여 **placement new** `static_cast<my_type>` 정수 값에서 변환)을 전달 하 고, 및의 정의를 업데이트 하 여 **`new`** **`delete`** 다시 정수 형식으로 캐스팅 하는 경우에는 placement new에 대 한 호출도 업데이트 해야 합니다. 이를 위해를 사용할 필요는 없습니다. **`enum`** 멤버를 포함 하는 클래스 형식 `size_t` 도 작동 합니다.

   또 다른 솔루션은 **placement new**를 함께 제거하는 것입니다. 코드에서 placement **new** 를 사용 하 여 배치 인수가 할당 되거나 삭제 되는 개체의 크기인 메모리 풀을 구현 하는 경우 크기가 지정 된 할당 해제 기능이 사용자 지정 메모리 풀 코드를 대체 하는 데 적합할 수 있으며 배치 함수를 제거 하 고 배치 함수 대신 고유한 두 인수 연산자를 사용할 수 있습니다 **`delete`** .

   코드를 바로 업데이트하지 않으려면 컴파일러 옵션 `/Zc:sizedDealloc-`를 사용하여 이전 동작으로 되돌릴 수 있습니다. 이 옵션을 사용 하는 경우 두 인수 **`delete`** 함수가 존재 하지 않으며 **placement delete** 연산자와 충돌 하지 않습니다.

- **공용 구조체 데이터 멤버**

   공용 구조체의 데이터 멤버는 더 이상 참조 형식을 포함할 수 없습니다. 다음 코드는 Visual Studio 2013에서 성공적으로 컴파일되지만 Visual Studio 2015에서는 오류를 생성합니다.

   ```cpp
    union U1 {
        const int i;
    };
    union U2 {
       int &i;
    };
    union U3 {
        struct {int &i;};
    };
   ```

   앞의 코드에서 발생하는 오류는 다음과 같습니다.

   ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
   ```

   이 문제를 해결하려면 참조 형식을 포인터 또는 값으로 변경합니다. 형식을 포인터로 변경하려면 공용 구조체 필드를 사용하는 코드를 변경해야 합니다. 코드를 값으로 변경하면 공용 구조체에 저장된 데이터가 변경되며, union 형식의 필드는 같은 메모리를 공유하므로 이 변경이 다른 필드에 영향을 미칩니다. 값 크기에 따라 공용 구조체 크기도 변경할 수 있습니다.

- **익명 공용 구조체**

   이제 표준을 더 잘 준수합니다. 이전 컴파일러 버전에서는 익명 공용 구조체에 대한 명시적 생성자 및 소멸자를 생성했습니다. 이러한 항목은 Visual Studio 2015에서 삭제됩니다.

   ```cpp
   struct S {
      S();
   };

   union {
      struct {
         S s;
      };
   } u; // C2280
   ```

   앞의 코드는 Visual Studio 2015에서 다음 오류를 생성합니다.

   ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
   ```

   이 문제를 해결하려면 생성자 및/또는 소멸자의 정의를 제공하세요.

   ```cpp
    struct S {
       // Provide a default constructor by adding an empty function body.
       S() {}
    };

    union {
       struct {
          S s;
       };
    } u;
   ```

- **익명 구조체가 있는 공용 구조체**

   공용 구조체에서 익명 구조체 멤버의 런타임 동작이 표준을 준수하도록 변경되었습니다. 해당 공용 구조체가 생성될 때 공용 구조체의 익명 구조체 멤버에 대한 생성자가 더 이상 암시적으로 호출되지 않습니다. 또한 공용 구조체가 범위를 벗어날 때 공용 구조체의 익명 구조체 멤버에 대한 소멸자가 더 이상 암시적으로 호출되지 않습니다. 소멸자가 있는 명명된 구조체 S 멤버가 포함된 익명 구조체가 공용 구조체 U에 들어 있는 다음 코드를 고려하세요.

   ```cpp
    #include <stdio.h>
    struct S {
        S() { printf("Creating S\n"); }
        ~S(){ printf("Destroying S\n"); }
    };
    union U {
        struct {
        S s;
    };
        U() {}
        ~U(){}
    };

    void f()
    {
        U u;
        // Destructor implicitly called here.
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
   ```

   Visual Studio 2013에서 S에 대한 생성자는 공용 구조체가 생성될 때 호출되고 S에 대한 소멸자는 f 함수의 스택이 정리될 때 호출됩니다. 그러나 Visual Studio 2015에서는 생성자와 소멸자가 호출되지 않습니다. 컴파일러에서 이 동작 변경에 대해 경고를 표시합니다.

   ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
   ```

   원래 동작을 복원하려면 익명 구조체에 이름을 지정합니다. 익명이 아닌 구조체의 런타임 동작은 컴파일러 버전과 관계없이 동일합니다.

   ```cpp
    #include <stdio.h>

    struct S {
        S() { printf("Creating S.\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U {
        struct {
            S s;
        } namedStruct;
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
   ```

   또는 생성자 및 소멸자 코드를 새 함수로 이동하고 공용 구조체에 대한 생성자 및 소멸자에서 이들 함수에 호출을 추가하세요.

   ```cpp
    #include <stdio.h>

    struct S {
        void Create() { printf("Creating S.\n"); }
        void Destroy() { printf("Destroying S\n"); }
    };
    union U {
        struct {
            S s;
        };
        U() { s.Create();  }
        ~U() { s.Destroy(); }
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

    char s[1024];
    printf("Press any key.\n");
    gets_s(s);
    return 0;
    }
   ```

- **템플릿 확인**

   템플릿의 이름 확인에 대한 변경 내용이 있습니다. C++에서 이름을 확인할 후보를 고려할 때 잠재적인 일치 항목으로 고려 중인 하나 이상의 이름에서 잘못된 템플릿 인스턴스화가 생성될 수 있습니다. 보통 이들 잘못된 인스턴스화 때문에 컴파일러 오류가 발생하지는 않습니다. 이 원칙을 SFINAE(Substitution Failure Is Not An Error)라고 합니다.

   현재 SFINAE에 따라 컴파일러가 클래스 템플릿의 특수화를 인스턴스화해야 하면 이 프로세스 중에 발생하는 오류는 컴파일러 오류입니다. 이전 버전에서는 컴파일러가 해당 오류를 무시합니다. 예를 들어, 다음 코드를 고려하세요.

   ```cpp
    #include <type_traits>

    template<typename T>
    struct S
    {
    S() = default;
    S(const S&);
    S(S&&);

    template<typename U, typename = typename std::enable_if<std::is_base_of<T, U>::value>::type>
    S(S<U>&&);
    };

    struct D;

    void f1()
    {
    S<D> s1;
        S<D> s2(s1);
    }

    struct B
    {
    };

    struct D : public B
    {
    };

    void f2()
    {
    S<D> s1;
        S<D> s2(s1);
    }
   ```

   현재 컴파일러로 컴파일할 경우 다음 오류가 발생합니다.

   ```Output
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'
    ..\t331.cpp(14): note: see declaration of 'D'
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled
            with
            [
                T=D,
                U=D
            ]
   ```

   이는 is_base_of의 첫 번째 호출 지점에서 'D' 클래스가 아직 정의되지 않았기 때문입니다.

   이 경우 문제를 해결하려면 클래스가 정의될 때까지 이러한 형식 특성을 사용하지 마세요. B 및 D의 정의를 코드 파일의 시작 부분으로 이동하면 오류가 해결됩니다. 정의가 헤더 파일에 있으면 헤더 파일의 include 문 순서를 확인하여 문제가 있는 템플릿이 사용되기 전에 클래스 정의가 컴파일되는지 확인합니다.

- **복사 생성자**

   Visual Studio 2013 및 Visual Studio 2015에서 클래스에 사용자 정의 이동 생성자가 있지만 사용자 정의 복사 생성자가 없는 경우 컴파일러는 해당 클래스에 대한 복사 생성자를 생성합니다. Dev14에서는 생성된 복사 생성자가 "= delete"로 표시됩니다.

### <a name="conformance-improvements-in-visual-studio-2015-update-1"></a><a name="VS_Update1"></a> Visual Studio 2015 업데이트 1의 규칙 향상

- **개인 가상 기본 클래스 및 간접 상속**

   이전 버전의 컴파일러에서는 파생 클래스에서 *간접적으로 파생된* `private virtual` 기본 클래스의 멤버 함수를 호출할 수 있었습니다. 이 이전 동작은 올바르지 않으며 C++ 표준을 따르지 않습니다. 컴파일러는 이러한 방식으로 작성된 코드를 더 이상 허용하지 않으며, 결과적으로 컴파일러 오류 C2280이 발생합니다.

   ```Output
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function
   ```

   예제(이전)

   ```cpp
    class base
    {
    protected:
        base();
        ~base();
    };

    class middle: private virtual base {};class top: public virtual middle {};

    void destroy(top *p)
    {
        delete p;  //
    }
   ```

   예제(이후)

   ```cpp
    class base;  // as above

    class middle: protected virtual base {};
    class top: public virtual middle {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

  \-또는-

   ```cpp
    class base;  // as above

    class middle: private virtual base {};
    class top: public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

- **오버로드된 operator new 및 operator delete**

   이전 버전의 컴파일러는 비멤버 **operator new** 및 비멤버 **operator delete**를 정적으로 선언하고 글로벌 네임스페이스 이외의 네임스페이스에서 선언할 수 있었습니다.  이 이전 동작은 프로그램에서 **`new`** 프로그래머가 의도 한 또는 연산자 구현을 호출 하지 않아서 잘못 된 자동 런타임 동작이 발생 하는 위험을 생성 **`delete`** 했습니다. 컴파일러는 이러한 방식으로 작성된 코드를 더 이상 허용하지 않으며, 대신 컴파일러 오류 C2323이 발생합니다.

   ```Output
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.
   ```

   예제(이전)

   ```cpp
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323
   ```

   예제(이후)

   ```cpp
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'
   ```

   또한 컴파일러가 특정 진단을 제공하지는 않지만, 인라인 operator new는 잘못된 형식으로 간주됩니다.

- **비클래스 형식에서 'operator *type*()'(사용자 정의 변환) 호출** 이전 버전의 컴파일러는 'operator *type*()'을 자동으로 무시하면서 비클래스 형식에서 호출할 수 있었습니다. 이 이전 동작으로 잘못된 코드가 자동으로 생성되어 예기치 않은 런타임 동작이 발생하는 위험이 초래되었습니다. 컴파일러는 이러한 방식으로 작성된 코드를 더 이상 허용하지 않으며, 대신 컴파일러 오류 C2228이 발생합니다.

   ```Output
    error C2228: left of '.operator type' must have class/struct/union
   ```

   예제(이전)

   ```cpp
    typedef int index_t;

    void bounds_check(index_t index);

    void login(int column)
    {
        bounds_check(column.operator index_t());  // error C2228
    }
   ```

   예제(이후)

   ```cpp
    typedef int index_t;

    void bounds_check(index_t index);

    void login(int column)
    {
         bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'
    }
   ```

- **상세 형식 지정자의 중복 typename**  이전 버전의 컴파일러에서는 **`typename`** 상세 형식 지정자를 사용할 수 있습니다. 이러한 방식으로 작성 된 코드는 의미 체계가 잘못 되었습니다. 컴파일러는 이러한 방식으로 작성된 코드를 더 이상 허용하지 않으며, 대신 컴파일러 오류 C3406이 발생합니다.

   ```Output
    error C3406: 'typename' cannot be used in an elaborated type specifier
   ```

   예제(이전)

   ```cpp
    template <typename class T>
    class container;
   ```

   예제(이후)

   ```cpp
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case
    class container;
   ```

- **이니셜라이저 목록에서 배열의 형식 추론** 이전 버전의 컴파일러는 이니셜라이저 목록에서 배열의 형식 추론을 지원하지 않았습니다. 이제 컴파일러가 이러한 형태의 형식 추론을 지원합니다. 결과적으로 이니셜라이저 목록을 사용한 함수 템플릿 호출은 이제 모호하거나 이전 버전의 컴파일러와 다른 오버로드가 선택될 수 있습니다. 이러한 문제를 해결하려면 이제 프로그램에서 프로그래머가 의도한 오버로드를 명시적으로 지정해야 합니다.

   이 새로운 동작으로 오버로드 확인에서 기록 후보와 똑같이 우수한 추가 후보를 고려하게 되는 경우, 호출이 모호해지며 결과적으로 컴파일러에서 컴파일러 오류 C2668이 발생합니다.

   ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
   ```

   예제 1: 오버로드된 함수에 대한 호출이 모호합니다(이전).

   ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)
    template <typename... Args>
    void f(int, Args...);  //

    template <int N, typename... Args>
    void f(const int (&)[N], Args...);

    int main()
    {
        // The compiler now considers this call ambiguous, and issues a compiler error
        f({3});  error C2668: 'f' ambiguous call to overloaded function
    }
   ```

   예제 1: 오버로드된 함수에 대한 호출이 모호합니다(이후).

   ```cpp
    template <typename... Args>
    void f(int, Args...);  //

    template <int N, typename... Args>
    void f(const int (&)[N], Args...);

    int main()
    {
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.
        f(3);
    }
   ```

   이 새로운 동작으로 오버로드 확인에서 기록 후보보다 더 일치되는 추가 후보를 고려하게 되는 경우, 호출이 새 후보로 명확하게 확인되므로 프로그래머가 의도한 것과 다른 프로그램 동작 변경을 초래할 수 있습니다.

   예제 2: 오버로드 확인의 변경(이전)

   ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)
    struct S
    {
        int i;
        int j;
    };

    template <typename... Args>
    void f(S, Args...);

    template <int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead
        f({1, 2});
    }
   ```

   예제 2: 오버로드 확인의 변경(이후)

   ```cpp
    struct S;  // as before

    template <typename... Args>
    void f(S, Args...);

    template <int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.
        f(S{1, 2});
    }
   ```

- **switch 문 경고의 복원**

   이전 버전의 컴파일러에서는 문과 관련 된 기존 경고를 제거 했습니다. **`switch`** 이제 이러한 경고가 복원 되었습니다. 이제 컴파일러에서 복원된 경고가 발생합니다. 이제 특정 사례(기본 사례 포함)와 관련된 경고가 switch 문의 마지막 줄 대신, 잘못된 사례가 포함된 줄에서 발생합니다. 이제 과거와는 다른 줄에서 해당 경고가 발생하므로 이전에 `#pragma warning(disable:####)` 을 사용하면 표시되지 않았던 경고가 더 이상 의도한 대로 숨겨지지 않을 수 있습니다. 이러한 경고를 의도한 대로 표시하지 않으려면 `#pragma warning(disable:####)` 지시문을 잠재적으로 잘못된 첫 번째 사례 위의 줄로 이동해야 할 수 있습니다. 다음은 복원된 경고입니다.

   ```Output
    warning C4060: switch statement contains no 'case' or 'default' labels
   ```

   ```Output
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label
   ```

   ```Output
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled
   ```

   ```Output
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'
   ```

   ```Output
    warning C4064: switch of incomplete enum 'flags'
   ```

   ```Output
    warning C4065: switch statement contains 'default' but no 'case' labels
   ```

   ```Output
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'
   ```

   ```Output
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given
   ```

   C4063의 예제(이전)

   ```cpp
    class settings
    {
    public:
        enum flags
        {
            bit0 = 0x1,
            bit1 = 0x2,
            ...
        };
        ...
    };

    int main()
    {
        auto val = settings::bit1;

        switch (val)
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // warning C4063
            break;
        }
    };
   ```

   C4063의 예제(이후)

   ```cpp
    class settings {...};  // as above

    int main()
    {
        // since C++11, use std::underlying_type to determine the underlying type of an enum
        typedef std::underlying_type<settings::flags>::type flags_t;

        auto val = settings::bit1;

        switch (static_cast<flags_t>(val))
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // ok
            break;
        }
    };
   ```

   복원된 다른 경고의 예는 해당 설명서에 제공됩니다.

- **#include: 경로 이름에 부모 디렉터리 지정자 '..' 사용**(`/Wall` `/WX`에만 영향을 줌)

   이전 버전의 컴파일러에서는 `#include` 지시문의 경로 이름에서 부모 디렉터리 지정자('..')의 사용을 검색하지 못했습니다. 이러한 방식으로 작성된 코드는 일반적으로 프로젝트 상대 경로를 부정확하게 사용하여 프로젝트의 외부에 존재하는 헤더를 포함합니다. 이 이전 동작은 프로그램이 프로그래머가 의도한 것과 다른 소스 파일을 포함하여 컴파일되거나 이러한 상대 경로가 다른 빌드 환경으로 이식되지 않는 위험을 초래했습니다. 이제 컴파일러는 이러한 방식으로 작성된 코드를 검색하여 프로그래머에게 알립니다. 그리고 사용하도록 설정된 경우 선택적으로 컴파일러 경고 C4464가 발생합니다.

   ```Output
    warning C4464: relative include path contains '..'
   ```

   예제(이전)

   ```cpp
    #include "..\headers\C4426.h"  // emits warning C4464
   ```

   예제(이후)

   ```cpp
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories
   ```

   또한 컴파일러가 특정 진단을 제공하지는 않지만, 프로젝트의 Include 디렉터리를 지정하는 데 부모 디렉터리 지정자("..")를 사용하지 않는 것이 좋습니다.

- **#pragma optimize()에서 헤더 파일의 끝을 넘어 확장**(`/Wall` `/WX`에만 영향을 줌)

   이전 버전의 컴파일러에서는 변환 단위 내에 포함된 헤더 파일을 이스케이프하는 최적화 플래그 설정에 대한 변경 내용을 검색하지 못했습니다. 이제 컴파일러는 이러한 방식으로 작성된 코드를 검색하여 프로그래머에게 알립니다. 그리고 사용하도록 설정된 경우 잘못된 `#include`의 위치에서 선택적으로 컴파일러 경고 C4426이 발생합니다. 이 경고는 변경 내용이 명령줄 인수에 의해 컴파일러에 설정된 최적화 플래그와 충돌하는 경우에만 발생합니다.

   ```Output
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()
   ```

   예제(이전)

   ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"  // warning C4426
   ```

   예제(이후)

   ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"
   ```

- **#pragma warning(push)** 및 **#pragma warning(pop)**(`/Wall` `/WX`에만 영향을 줌)

   이전 버전의 컴파일러는 다른 소스 파일에서 `#pragma warning(push)` 상태 변경이 `#pragma warning(pop)` 상태 변경과 쌍을 이루는 것(의도되는 경우가 드묾)을 검색하지 못했습니다. 이 이전 동작으로 프로그램이 프로그래머가 의도한 것과 다르게 설정된 경고 집합으로 컴파일되어 잘못된 자동 런타임 동작이 발생하는 위험이 초래됩니다. 이제 컴파일러는 이러한 방식으로 작성된 코드를 검색하여 프로그래머에게 알립니다. 그리고 사용하도록 설정된 경우 일치하는 `#pragma warning(pop)`의 위치에서 선택적으로 컴파일러 경고 C5031이 발생합니다. 이 경고에는 해당 `#pragma warning(push)`의 위치를 참조하는 참고가 포함되어 있습니다.

   ```Output
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file
   ```

   예제(이전)

   ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    ...
    #pragma warning(pop)  // pops a warning state not pushed in this source file
    ...
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'
    ...
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031
    ...
   ```

   예제(이후)

   ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)  // pops the warning state pushed in this source file
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    #pragma warning(push)  // pushes the warning state pushed in this source file
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.
    ...
    #include "C5031_part2.h"
    ...
   ```

   드물긴 하지만 의도적으로 이러한 코드를 작성하는 경우가 있습니다. 이러한 방식으로 작성된 코드는 `#include` 순서의 변경에 민감합니다. 가능한 경우 소스 코드 파일에서 자동으로 포함된 방식으로 경고 상태를 관리하는 것이 좋습니다.

- **#pragma warning(push) 불일치**(`/Wall` `/WX`에만 영향을 줌)

   이전 버전의 컴파일러는 변환 단위의 끝에서 `#pragma warning(push)` 상태 변경 불일치를 검색하지 못했습니다. 이제 컴파일러는 이러한 방식으로 작성된 코드를 검색하여 프로그래머에게 알립니다. 그리고 사용하도록 설정된 경우 일치하지 않는 `#pragma warning(push)`의 위치에서 선택적으로 컴파일러 경고 C5032가 발생합니다. 이 경고는 변환 단위에 컴파일 오류가 없는 경우에만 발생합니다.

   ```Output
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)
   ```

   예제(이전)

   ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5032.h ends without #pragma warning(pop)

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h
   ```

   예제(이후)

   ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop) // matches #pragma warning (push) on line 1
    // C5032.h ends

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)
   ```

- **개선된 #pragma warning 상태 추적의 결과로 추가 경고가 발생할 수 있습니다.**

   이전 버전의 컴파일러는 의도된 모든 경고를 발생시키기에는 불충분한 수준으로 `#pragma warning` 상태 변경을 추적했습니다. 이 동작으로 프로그래머가 의도한 것과 다른 상황에서 특정 경고가 효과적으로 표시되지 않는 위험이 초래됩니다. 이제 컴파일러는 `#pragma warning` 상태(특히 템플릿 내부의 `#pragma warning` 상태 변경과 관련된 내용)를 더욱 강력하게 추적하며, 선택적으로 새로운 경고 C5031 및 C5032가 발생합니다. 이러한 경고는 프로그래머가 `#pragma warning(push)` 및 `#pragma warning(pop)`의 의도하지 않은 사용을 찾는 데 도움이 됩니다.

   개선된 `#pragma warning` 상태 변경 추적의 결과로, 이전에 제대로 표시되지 않은 경고 또는 이전에 잘못 진단된 문제와 관련된 경고가 이제 발생할 수 있습니다.

- **접근할 수 없는 코드의 개선된 ID**

   C++ 표준 라이브러리의 변경 및 이전 버전의 컴파일러에 비해 향상된 인라인 함수 호출 기능을 통해 컴파일러가 이제 특정 코드에 접근할 수 없음을 증명할 수 있습니다. 이 새로운 동작으로 경고 C4720의 인스턴스가 새로 그리고 더욱 자주 발생할 수 있습니다.

   ```Output
    warning C4720: unreachable code
   ```

   최적화 프로세스에서 더 많은 함수 호출을 인라인하거나 중복 코드를 제거하거나 특정 코드에 접근할 수 없는지 확인할 수 있도록 하므로, 이 경고는 대개 최적화를 사용하면서 컴파일할 경우에만 발생할 수 있습니다. 경고 C4720의 새 인스턴스가 특히 [std::find](../standard-library/algorithm-functions.md#find)의 사용과 관련하여 **try/catch** 블록에서 자주 발생했음을 관찰했습니다.

   예제(이전)

   ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch(...)
    {
        do_something();  // ok
    }
   ```

   예제(이후)

   ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch(...)
    {
        do_something();  // warning C4702: unreachable code
    }
   ```

### <a name="conformance-improvements-in-visual-studio-2015-update-2"></a><a name="VS_Update2"></a> Visual Studio 2015 업데이트 2의 규칙 향상

- **SFINAE 식에 대한 부분 지원으로 인해 추가 경고 및 오류가 발생할 수 있습니다.**

   이전 버전의 컴파일러는 **`decltype`** SFINAE 식에 대 한 지원 부족으로 지정자 내의 특정 식 종류를 구문 분석 하지 않았습니다. 이 이전 동작은 올바르지 않으며 C++ 표준을 따르지 않습니다. 지속적인 규칙 향상으로 인해 이제 컴파일러는 이러한 식을 구문 분석하고 SFINAE 식에 대한 부분 지원을 합니다. 결과적으로 이제 컴파일러는 이전 버전의 컴파일러가 구문 분석하지 않았던 식에서 경고 및 오류를 발생합니다.

   이 새로운 동작이 **`decltype`** 아직 선언 되지 않은 형식을 포함 하는 식을 구문 분석 하는 경우 컴파일러는 C2039 컴파일러 오류를 발생 시킵니다.

   ```Output
    error C2039: 'type': is not a member of '`global namespace''
   ```

   예제 1: 선언되지 않은 형식 사용(이전)

   ```cpp
    struct s1
    {
      template <typename T>
      auto f() -> decltype(s2<T>::type::f());  // error C2039

      template<typename>
      struct s2 {};
    }
   ```

   예제 1(이후)

   ```cpp
    struct s1
    {
      template <typename>  // forward declare s2struct s2;

      template <typename T>
      auto f() -> decltype(s2<T>::type::f());

      template<typename>
      struct s2 {};
    }
   ```

   이 새 동작에서 키워드를 **`decltype`** 사용 하 여 종속성 이름이 형식이 되도록 지정 하는 식을 구문 분석할 때 컴파일러는 컴파일러 **`typename`** 오류 C2923과 함께 컴파일러 경고 C4346을 발생 시킵니다.

   ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
   ```

   ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
   ```

   예제 2: 종속 이름이 형식이 아님(이전)

   ```cpp
    template <typename T>
    struct s1
    {
      typedef T type;
    };

    template <typename T>
    struct s2
    {
      typedef T type;
    };

    template <typename T>
    T declval();

    struct s
    {
      template <typename T>
      auto f(T t) -> decltype(t(declval<S1<S2<T>::type>::type>()));  // warning C4346, error C2923
    };
   ```

   예제 2(이후)

   ```cpp
    template <typename T> struct s1 {...};  // as above
    template <typename T> struct s2 {...};  // as above

    template <typename T>
    T declval();

    struct s
    {
      template <typename T>
      auto f(T t) -> decltype(t(declval<S1<typename S2<T>::type>::type>()));
    };
   ```

- **`volatile`****멤버 변수가 암시적으로 정의 된 생성자 및 대입 연산자를 방지** 합니다. 이전 버전의 컴파일러에서는 **`volatile`** 멤버 변수가 있는 클래스가 기본 복사/이동 생성자 및 기본 복사/이동 할당 연산자를 자동으로 생성 하도록 허용 했습니다. 이 이전 동작은 올바르지 않으며 C++ 표준을 따르지 않습니다. 이제 컴파일러는 volatile 멤버 변수가 있는 클래스는 특수한 생성자 및 대입 연산자가 있는 것으로 간주하여 이러한 연산자의 기본 구현이 자동으로 생성되는 것을 막습니다. 이러한 클래스가 공용 구조체(또는 클래스 내의 익명 공용 구조체)의 멤버이면 공용 구조체(또는 익명 공용 구조체를 포함하는 클래스)의 복사/이동 생성자 및 복사/이동 대입 연산자는 삭제된 것으로 암시적으로 정의됩니다. 명시적으로 정의하지 않고 공용 구조체(또는 익명 공용 구조체를 포함하는 클래스)를 만들거나 복사하려 하면 오류가 발생하며 컴파일러에서 결과적으로 컴파일러 오류 C2280을 발생합니다.

   ```Output
    error C2280: 'B::B(const B &)': attempting to reference a deleted function
   ```

   예제(이전)

   ```cpp
    struct A
    {
      volatile int i;
      volatile int j;
    };

    extern A* pa;

    struct B
    {
      union
      {
        A a;
        int i;
      };
    };

    B b1 {*pa};
    B b2 (b1);  // error C2280
   ```

   예제(이후)

   ```cpp
    struct A
    {
      int i;int j;
    };

    extern volatile A* pa;

    A getA()  // returns an A instance copied from contents of pa
    {
      A a;
      a.i = pa->i;
      a.j = pa->j;
      return a;
    }

    struct B;  // as above

    B b1 {GetA()};
    B b2 (b1);  // error C2280
   ```

- **정적 멤버 함수는 cv 한정자를 지원하지 않습니다.**

   이전 버전의 Visual C++ 2015는 정적 멤버 함수에 cv 한정자가 포함되는 것을 허용했습니다. 이 동작은 Visual C++ 2015 및 Visual C++ 2015 업데이트 1에서의 문제 재발로 인한 것입니다. Visual C++ 2013 및 이전 버전의 Visual C++는 이런 식으로 작성된 코드를 거부합니다. Visual C++ 2015 및 Visual C++ 2015 업데이트 1의 동작은 잘못되었으며 C++ 표준과 일치하지 않습니다.  Visual Studio 2015 업데이트 2는 이런 식으로 작성된 코드를 거부하며 대신 컴파일러 오류 C2511을 발생합니다.

   ```Output
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'
   ```

   예제(이전)

   ```cpp
    struct A
    {
      static void func();
    };

    void A::func() const {}  // C2511
   ```

   예제(이후)

   ```cpp
    struct A
    {
      static void func();
    };

    void A::func() {}  // removed const
   ```

- **열거형의 정방향 선언은 WinRT 코드에서 허용되지 않습니다**(`/ZW`에만 영향을 줌).

   Windows 런타임 (WinRT)에 대해 컴파일된 코드는 **`enum`** 관리 되는 c + + 코드가 컴파일러 스위치를 사용 하 여 .Net Framework에 대해 컴파일되는 경우와 마찬가지로 형식을 전방으로 선언할 수 없습니다 `/clr` . 이 동작은 열거형의 크기를 항상 알 수 있으며 WinRT 형식 시스템에 올바르게 프로젝션될 수 있음을 확인합니다. 컴파일러는 이러한 방식으로 작성된 코드를 거부하고 컴파일러 오류 C3197과 함께 컴파일러 오류 C2599를 발생합니다.

   ```Output
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed
   ```

   ```Output
    error C3197: 'public': can only be used in definitions
   ```

   예제(이전)

   ```cpp
    namespace A {
      public enum class CustomEnum: int32;  // forward declaration; error C2599, error C3197
    }

    namespace A {
      public enum class CustomEnum: int32
      {
        Value1
      };
    }

    public ref class Component sealed
    {
    public:
      CustomEnum f()
      {
        return CustomEnum::Value1;
      }
    };
   ```

   예제(이후)

   ```cpp
              // forward declaration of CustomEnum removed
    namespace A {
      public enum class CustomEnum: int32
      {
        Value1
      };
    }

    public ref class Component sealed
    {
    public:
      CustomEnum f()
      {
        return CustomEnum::Value1;
      }
    };
   ```

- **오버로드된 멤버가 아닌 연산자 new 및 연산자 delete는 인라인으로 선언할 수 없습니다**(수준 1(`/W1`)이 기본적으로 설정되어 있음).

   이전 버전의 컴파일러는 멤버가 아닌 **연산자 new** 및 **연산자 delete** 함수가 인라인으로 선언될 때 경고를 발생하지 않습니다. 이 방식으로 작성된 코드는 형식이 잘못되었으며(진단이 필요하지 않음) 진단하기 힘들 수 있는 일치하지 않는 new 및 delete 연산자로 인해 특히 크기가 지정된 할당 해제와 함께 사용 시 메모리 문제를 일으킬 수 있습니다. 이제 컴파일러는 이런 식으로 작성된 코드를 식별하기 위해 경고 C4595를 발생합니다.

   ```Output
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline
   ```

   예제(이전)

   ```cpp
    inline void* operator new(size_t sz)  // warning C4595
    {
      ...
    }
   ```

   예제(이후)

   ```cpp
    void* operator new(size_t sz)  // removed inline
    {
      ...
    }
   ```

   이러한 방식으로 작성된 코드를 수정하려면 연산자 정의를 헤더 파일에서 해당하는 소스 파일로 이동해야 합니다.

### <a name="conformance-improvements-in-visual-studio-2015-update-3"></a><a name="VS_Update3"></a> Visual Studio 2015 업데이트 3의 규칙 향상

- **std::is_convertable에서 자체 할당을 검색함**(표준 라이브러리) 복사 생성자가 삭제되거나 private인 경우 이전 버전의 `std::is_convertable` 형식 특성에서 class 형식의 자체 할당을 올바르게 검색하지 못했습니다. 이제 `std::is_convertable<>::value` 는 **`false`** 삭제 된 또는 전용 복사 생성자를 사용 하 여 클래스 형식에 적용 될 때로 올바르게 설정 됩니다.

   이 변경과 관련된 컴파일러 진단은 없습니다.

   예제

   ```cpp
    #include <type_traits>

    class X1
    {
    public:
        X1(const X1&) = delete;
    };

    class X2
    {
    private:
        X2(const X2&);
    };

    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");
   ```

   이전 버전의 Visual C++에서는가로 잘못 설정 되었기 때문에이 예제의 맨 아래에 있는 정적 어설션이 전달 `std::is_convertable<>::value` **`true`** 됩니다. 이제 `std::is_convertable<>::value` 이로 올바르게 설정 되어 **`false`** 정적 어설션이 실패 합니다.

- **기본값으로 설정되었거나 삭제된 trivial 복사 및 이동 생성자가 액세스 지정자를 따름**

   이전 버전의 컴파일러에서는 호출을 허용하기 전에 기본값으로 설정되었거나 삭제된 trivial 복사 및 이동 생성자의 액세스 지정자를 확인하지 않았습니다. 이 이전 동작은 올바르지 않으며 C++ 표준을 따르지 않습니다. 경우에 따라 이 이전 동작으로 잘못된 코드가 자동으로 생성되어 예기치 않은 런타임 동작이 발생하는 위험이 초래되었습니다. 이제 컴파일러에서 기본값으로 설정되었거나 삭제된 간단한 복사 및 이동 생성자의 액세스 지정자를 검사하여 호출 가능 여부를 확인하고, 호출할 수 없는 경우 결과로 컴파일러 경고 C2248을 실행합니다.

   ```Output
    error C2248: 'S::S' cannot access private member declared in class 'S'
   ```

   예제(이전)

   ```cpp
    class S {
    public:
       S() = default;
    private:
        S(const S&) = default;
    };

    void f(S);  // pass S by value

    int main()
    {
        S s;
        f(s);  // error C2248, can't invoke private copy constructor
    }
   ```

   예제(이후)

   ```cpp
    class S {
    public:
       S() = default;
    private:
        S(const S&) = default;
    };

    void f(const S&);  // pass S by reference

    int main()
    {
        S s;
        f(s);
    }
   ```

- **특성 사용 ATL 코드 지원 중단**(수준 1(`/W1`)이 기본적으로 설정되어 있음)

   이전 버전의 컴파일러에서는 특성 사용 ATL 코드를 지원했습니다. [Visual C++ 2008부터 시작](#whats-new-for-c-in-visual-studio-2008)된 특성 사용 ATL 코드 지원 제거의 다음 단계로 특성 사용 ATL 코드가 더 이상 사용되지 않습니다. 이제 컴파일러에서 사용되지 않는 이러한 종류의 코드를 식별하기 위해 컴파일러 경고 C4467을 실행합니다.

   ```Output
    warning C4467: Usage of ATL attributes is deprecated
   ```

   컴파일러에서 지원이 제거될 때까지 특성 사용 ATL 코드를 계속 사용하려는 경우 `/Wv:18` 또는 `/wd4467` 명령줄 인수를 컴파일러에 전달하거나 소스 코드에 `#pragma warning(disable:4467)`을 추가하여 이 경고를 해제할 수 있습니다.

   예제 1(이전)

   ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
   ```

   예제 1(이후)

   ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
   ```

   사용되지 않는 ATL 특성의 사용을 방지하기 위해 아래 예제 코드와 같이 IDL 파일을 만들 수 있습니다.

   예제 2(이전)

   ```cpp
    [emitidl];
    [module(name="Foo")];

    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
    __interface ICustom {
        HRESULT Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
    class CFoo : public ICustom
    {
        // ...
    };
   ```

   먼저 *.idl 파일을 만듭니다. 생성된 vc140.idl 파일을 사용하여 인터페이스와 주석이 포함된 \*.idl 파일을 가져올 수 있습니다.

   그런 다음 빌드에 MIDL 단계를 추가하여 C++ 인터페이스 정의가 생성되었는지 확인합니다.

   예제 2 IDL(이후)

   ```cpp
    import "docobj.idl";

    [
        object,local,uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)
    ]

    interface ICustom : IUnknown {
        HRESULT  Custom([in] long l, [out,retval] long *pLong);
        [local] HRESULT  CustomLocal([in] long l, [out,retval] long *pLong);
    };

    [ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
    library Foo
    {
        importlib("stdole2.tlb");
        importlib("olepro32.dll");
            [
                version(1.0),
                appobject,uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)
            ]

        coclass CFoo {
            interface ICustom;
        };
    }
   ```

   아래 예제 코드와 같이 구현 파일에서 직접 ATL을 사용합니다.

   예제 2 구현(이후)

   ```cpp
    #include <idl.header.h>
    #include <atlbase.h>

    class ATL_NO_VTABLE CFooImpl :
        public ICustom,
        public ATL::CComObjectRootEx<CComMultiThreadModel>
    {
    public:
        BEGIN_COM_MAP(CFooImpl)
        COM_INTERFACE_ENTRY(ICustom)
        END_COM_MAP()
    };
   ```

- **미리 컴파일된 헤더(PCH) 파일 및 일치하지 않는 #include 지시문**(`/Wall` `/WX`에만 영향을 줌)

   이전 버전의 컴파일러에서는 미리 컴파일된 헤더(PCH) 파일을 사용할 때 `-Yc` 및 `-Yu` 컴파일 간에 일치하지 않는 소스 파일의 `#include` 지시문을 허용했습니다. 이런 방식으로 작성된 코드는 컴파일러에서 더 이상 허용되지 않습니다. PCH 파일 사용 시 일치하지 않는 `#include` 지시문을 식별하기 위해 이제 컴파일러에서 컴파일러 경고 CC4598을 실행합니다.

   ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
   ```

   예제(이전):

   X.cpp(-Ycc.h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

   Z.cpp(-Yuc.h)

   ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
   ```

   예제(이후)

   X.cpp(-Ycc.h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

   Z.cpp(-Yuc.h)

   ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
   ```

- **미리 컴파일된 헤더(PCH) 파일 및 일치하지 않는 include 디렉터리**(`/Wall` `/WX`에만 영향을 줌)

   이전 버전의 컴파일러에서는 미리 컴파일된 헤더(PCH) 파일을 사용할 때 `-Yc` 및 `-Yu` 컴파일 간에 일치하지 않는 컴파일러의 include 디렉터리(`-I`) 명령줄 인수를 허용했습니다. 이런 방식으로 작성된 코드는 컴파일러에서 더 이상 허용되지 않습니다.   PCH 파일 사용 시 일치하지 않는 include 디렉터리(`-I`) 명령줄 인수를 식별하기 위해 이제 컴파일러에서 컴파일러 경고 CC4599를 실행합니다.

   ```Output
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position
   ```

   예제(이전)

   ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h Z.cpp
   ```

   예제(이후)

   ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h -I.. Z.cpp
   ```

## <a name="whats-new-for-c-in-visual-studio-2013"></a>Visual Studio 2013의 새로운 C++ 기능

### <a name="improved-iso-cc-standards-support"></a>향상된 ISO C/C++ 표준 지원

#### <a name="compiler"></a>컴파일러

MSVC는 다음과 같은 ISO C++11 언어 기능을 지원합니다.

- 함수 템플릿의 기본 템플릿 인수
- 위임 생성자
- 명시적 변환 연산자
- 이니셜라이저 목록 및 균일 초기화
- 원시 문자열 리터럴
- variadic 템플릿
- 별칭 템플릿
- 삭제된 함수
- NSDMI(비정적 데이터 멤버 이니셜라이저)
- 기본값으로 설정된 함수 \*
- 다음과 같은 ISO C99 언어 기능을 지원합니다.
- _Bool
- 복합 리터럴
- 지정된 이니셜라이저
- 코드 혼합 선언
- 새 컴파일러 옵션 `/Zc:strictStrings`를 사용하여 수정할 수 있는 값으로 문자열 리터럴 변환을 허용하지 않을 수 있습니다. C + + 98에서 문자열 리터럴과로의 변환 **`char*`** (및 와이드 문자열 리터럴은로 `wchar_t*` )은 사용 되지 않습니다. C++11에서 변환이 완전히 제거되었습니다. 컴파일러가 표준을 엄격하게 준수할 수 있지만 대신 사용자가 변환을 제어할 수 있도록 `/Zc:strictStrings` 옵션을 제공합니다. 기본적으로 이 옵션은 해제되어 있습니다. 디버그 모드에서 이 옵션을 사용하면 STL은 컴파일되지 않습니다.
- rvalue/lvalue 참조 캐스트. rvalue 참조를 사용하여 C++11은 lvalue와 rvalue를 명확하게 구별할 수 있습니다. 이전에는 컴파일러가 특정 캐스팅 시나리오에서 이 기능을 제공하지 않았습니다. 새 컴파일러 옵션인 `/Zc:rvalueCast`가 추가되어 C++ Language Working Paper에서 컴파일러를 준수합니다(5.4단원, [expr.cast]/1 참조). 이 옵션이 지정되지 않은 경우 기본 동작은 Visual Studio 2012와 동일합니다.

> [!NOTE]
> 기본 설정된 함수의 경우 멤버 수준 이동 생성자 및 이동 대입 연산자를 요청하기 위한 =default 사용은 지원되지 않습니다.

### <a name="c99-libraries"></a>C99 라이브러리

누락된 함수에 대한 선언과 구현이 math.h, ctype.h, wctype.h, stdio.h, stdlib.h 및 wchar.h 헤더에 추가되었습니다. 또한 새로운 complex.h, stdbool.h, fenv.h 및 inttypes.h 헤더가 추가되었고 모든 함수에 대한 구현이 여기에 선언되었습니다. 새로운 C++ 래퍼 헤더(ccomplex, cfenv, cinttypes, ctgmath)가 있고, 다른 많은 헤더(ccomplex, cctype, clocale, cmath, cstdint, cstdio, cstring, cwchar 및 cwctype)가 업데이트되었습니다.

### <a name="standard-template-library"></a>표준 템플릿 라이브러리

C++11 명시적 변환 연산자, 이니셜라이저 목록, 범위가 지정된 열거형 및 variadic 템플릿을 지원합니다.
이제 모든 컨테이너가 C++11의 세부적인 요소 요구 사항을 지원합니다.
다음과 같은 C++14 기능을 지원합니다.

- 투명 연산자 구조 함수(less<>, greater<>, plus<>, multiplies<> 등)
- make_unique\<T>(args...) 및 make_unique<T[]>(n)
- cbegin()/cend(), rbegin()/rend(), 및 crbegin()/crend() 비멤버 함수
- \<atomic> 다양 한 성능 향상을 받았습니다.
- \<type_traits> 주요 안정화 및 코드 수정을 받았습니다.

### <a name="breaking-changes"></a>주요 변경 내용

이와 같이 향상된 ISO C/C++ 표준 지원 기능을 사용하려면 C++11을 따르고 Visual Studio 2013의 Visual C++에서 올바르게 컴파일되도록 기존 코드를 변경해야 할 수 있습니다.

### <a name="visual-c-library-enhancements"></a>Visual C++ 라이브러리 향상

- C++ REST SDK가 추가되었습니다. 이 SDK에는 REST 서비스의 최신 C++ 구현이 포함되어 있습니다.
- C++ AMP 질감 지원이 향상되었습니다. 이제 밉 맵 및 새로운 샘플링 모드를 지원합니다.
- PPL 작업에서 여러 일정 관리 기술 및 비동기 디버깅을 지원합니다. 새 API를 사용하면 정상 결과 및 예외 조건 둘 다에 대한 PPL 작업을 만들 수 있습니다.

### <a name="c-application-performance"></a>C++ 애플리케이션 성능

- 자동 벡터화 도우미에서 더 많은 C++ 패턴을 인식하고 최적화하므로 코드를 더 빠르게 실행할 수 있습니다.
- ARM 플랫폼 및 Atom 마이크로 아키텍처 코드 품질이 향상되었습니다.
- __vectorcall 호출 규칙이 추가되었습니다. 백터 레지스터를 사용하는 __vectorcall 호출 규칙을 통해 벡터 형식 인수를 전달합니다.
- 새 링커 옵션이 제공됩니다. `/Gw`(컴파일러) 및 `/Gy`(어셈블러) 스위치를 사용하면 링커 최적화에서 간결한 이진 파일을 생성할 수 있습니다.
- C++ AMP 공유 메모리를 지원하여 CPU와 GPU 간의 데이터 복사를 줄이거나 제거합니다.

### <a name="profile-guided-optimization-pgo-enhancements"></a>향상된 PGO(프로필 기반 최적화)

- PGO 사용으로 최적화된 응용 프로그램 작업 집합의 감소로 인한 성능 향상
- Windows 런타임 앱 개발을 위한 새로운 PGO

### <a name="windows-runtime-app-development-support"></a>Windows 런타임 앱 개발 지원

- **값 구조체에서 boxed 형식 지원**

   이제와는 달리 null 일 수 있는 필드를 사용 하 여 값 형식을 정의할 수 있습니다 `IBox<int>^` **`int`** . 즉, 필드에 값을 포함 하거나와 같을 수 있습니다 **`nullptr`** .

- **다양한 예외 정보**

   C++/CX는 ABI(애플리케이션 이진 인터페이스)에서 자세한 예외 정보를 캡처하고 전파할 수 있도록 하는 새로운 Windows 오류 모델을 지원합니다. 여기에는 호출 스택과 사용자 지정 메시지 문자열이 포함됩니다.

- **가상 형식의 Object::ToString()**

   사용자 정의 Windows 런타임 ref 형식에서 ToString을 재정의할 수 있습니다.

- **사용되지 않는 API 지원**

   공용 Windows 런타임 API는 이제 사용되지 않는 것으로 표시되고 빌드 경고로 나타나는 사용자 지정 메시지가 제공될 수 있으며, 마이그레이션 지침을 제공할 수 있습니다.

- **향상 된 디버거.**

   네이티브/JavaScript interop 디버깅, Windows 런타임 예외 진단 및 비동기 코드 디버깅(Windows 런타임 및 PPL)을 지원합니다.

> [!NOTE]
> 이 섹션에서 설명한 C++ 관련 기능 및 향상된 기능 외에도, 향상된 다른 Visual Studio 기능을 사용하면 Windows 런타임 앱을 더 효과적으로 작성할 수 있습니다.

### <a name="diagnostics-enhancements"></a>진단 향상

- 향상된 디버거. 비동기 디버깅 및 [내 코드만] 디버깅을 지원합니다.
- 코드 분석 범주. 이제 코드 분석기에서 분류된 출력을 보고 코드 결함을 찾아 수정할 수 있습니다.
- XAML 진단. 이제 XAML에서 UI 응답성 및 배터리 사용 문제를 진단할 수 있습니다.
- 그래픽 및 GPU 디버깅 향상
- 원격 캡처 및 실제 디바이스에서의 재생
- C++ AMP 및 CPU 동시 디버깅
- 향상된 C++ AMP 런타임 진단
- HLSL 컴퓨팅 셰이더 추적 디버깅

### <a name="3-d-graphics-enhancements"></a>3차원 그래픽 향상

- 미리 곱한 알파 DDS 형식에 대한 이미지 콘텐츠 파이프라인 지원
- 이미지 편집기에서 렌더링을 위해 내부적으로 미리 곱한 알파를 사용하며, 이에 따라 짙은 후광과 같은 렌더링 아티팩트를 방지합니다.
- 이미지 및 모델 편집기. 이미지 편집기 및 모델 편집기의 셰이더 디자이너에서 사용자 정의 필터 만들기가 지원됩니다.

### <a name="ide-and-productivity"></a>IDE 및 생산성

**향상된 코드 서식 지정** C++ 코드에 보다 다양한 서식 설정을 적용할 수 있습니다. 이러한 설정을 사용하여 중괄호 및 키워드의 새 줄 배치, 들여쓰기, 공백 및 줄 바꿈을 제어할 수 있습니다. 문과 블록을 완료할 때와 파일에 코드를 붙여 넣을 때 코드의 서식이 자동으로 지정됩니다.

**중괄호 완성** C++ 코드는 이제 다음 여는 문자에 해당하는 닫는 문자를 자동으로 완성합니다.

- {(중괄호)
- [(대괄호)
- ((괄호)
- '(작은따옴표)
- "(큰따옴표)

**추가 C++ 자동 완성 기능**

- 클래스 형식에 세미콜론을 추가합니다.
- 원시 문자열 리터럴에 대한 괄호를 완성합니다.
- 여러 줄 주석 (/ \* /)을 완료 합니다. \*

**모든 참조 찾기**에서 텍스트 일치 목록을 표시한 후 백그라운드에서 참조를 자동으로 확인하고 필터링합니다.

**컨텍스트 기반 멤버 목록 필터링** 액세스할 수 없는 멤버는 IntelliSense 멤버 목록에서 필터링됩니다. 예를 들어 형식을 구현하는 코드를 수정하지 않으면 개인 멤버는 멤버 목록에 표시되지 않습니다. 멤버 목록이 열려 있는 동안 **ctrl** + **J** 를 눌러 한 수준의 필터링을 제거할 수 있습니다 (현재 멤버 목록 창에만 적용 됨). **Ctrl** + **J** 를 다시 눌러 텍스트 필터링을 제거 하 고 모든 멤버를 표시할 수 있습니다.

**매개 변수 도움말 스크롤** 매개 변수 도움말 도구 설명에 표시된 함수 시그니처는 임의의 시그니처를 표시하고 현재 컨텍스트에 따라 업데이트하는 것이 아니라 실제로 입력한 매개 변수의 수에 따라 변경됩니다. 매개 변수 도움말도 중첩된 함수에 표시될 때 올바르게 작동합니다.

**헤더/코드 파일 전환** 이제 바로 가기 메뉴 또는 바로 가기 키의 명령을 사용하여 헤더와 해당 코드 파일 사이를 전환할 수 있습니다.

**크기 조정 가능한 C++ 프로젝트 속성 창**

**C++/CX 및 C++/CLI에서 이벤트 처리기 코드 자동 생성**  C++/CX 또는 C++/CLI 코드 파일에 이벤트 처리기를 추가하는 코드를 입력하는 경우 편집기는 대리자 인스턴스와 이벤트 처리기 정의를 자동으로 생성할 수 있습니다. 도구 설명 창은 이벤트 처리기 코드를 자동으로 생성할 수 있을 때 나타납니다.

**향상된 DPI 인식** 이제 애플리케이션 매니페스트 파일의 DPI 인식 설정에서 &quot;모니터 단위 높은 DPI 인식&quot; 설정을 지원합니다.

**더 빠른 구성 전환** 대규모 애플리케이션에서 특히 후속 전환 작업과 같은 구성 전환이 훨씬 더 빠르게 실행됩니다.

**빌드 시간 효율성** 다양한 최적화 및 멀티 코어 활용으로 특히 대규모 프로젝트에서 빌드를 보다 빠르게 수행합니다. C++ WinMD에 대한 참조가 있는 C++ 애플리케이션의 증분 빌드도 훨씬 더 빠릅니다.

## <a name="whats-new-for-c-in-visual-studio-2012"></a>Visual Studio 2012의 새로운 C++ 기능

### <a name="improved-c11-standards-support"></a>향상된 C++11 표준 지원

#### <a name="standard-template-library"></a>표준 템플릿 라이브러리

- 새 STL 헤더에 대 한 지원:,,,,,, \<atomic> \<chrono> \<condition_variable> \<filesystem> \<future> \<mutex> \<ratio> 및 \<thread>
- 메모리 리소스 사용을 최적화하기 위해 컨테이너가 더 작아졌습니다. 예를 들어 기본 설정이 있는 x86 릴리스 모드에서 `std::vector`는 Visual Studio 2010의 16바이트에서 Visual Studio 2012의 12바이트로 축소되었으며, `std::map`은 Visual Studio 2010의 16바이트에서 Visual Studio 2012의 8바이트로 축소되었습니다.
- C++11 표준에서 허용되었지만 필요하지 않은 SCARY 반복기가 구현되었습니다.

#### <a name="other-c11-enhancements"></a>기타 향상된 C++11 기능

- 범위 기반 for 루프. 배열, STL 컨테이너 및 Windows 런타임 컬렉션과 함께 작동하는 더 강력한 루프를 for (for-range-declaration : expression) 형식으로 작성할 수 있습니다. 핵심 언어 지원에 포함됩니다.
- 빈 람다 도입자([])로 시작하고 로컬 변수를 갭처하지 않는 코드 블록인 상태 비저장 람다는 이제 C++11 표준에 필요한 함수 포인터로 암시적으로 변환됩니다.
- 범위가 지정된 열거형 지원 C++ enum class 열거형-키가 지원됩니다. 다음 코드에서는 이 열거형-키가 이전 열거형 동작과 다른 점을 보여 줍니다.

   ```cpp
  enum class Element { Hydrogen, Helium, Lithium, Beryllium };
  void func1(Element e);
  func1(Hydrogen); // error C2065: 'Hydrogen' : undeclared identifier
  func1(Element::Helium); // OK
   ```

### <a name="windows-runtime-app-development-support"></a>Windows 런타임 앱 개발 지원

- **네이티브 XAML 기반 UI 모델** Windows 런타임 앱의 경우 새로운 네이티브 XAML 기반 UI 모델을 사용할 수 있습니다.
- **구성 요소 확장을 Visual C++** 합니다. 이러한 확장은 Windows 런타임 앱의 필수 구성 요소인 Windows 런타임 개체의 사용을 간소화합니다. 자세한 내용은 C++ [및 Visual C++ 언어 참조(C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)를 [사용하는 Windows 런타임 앱에 대한 로드맵을 참조하세요.](../cppcx/universal-windows-apps-cpp.md)
- **DirectX 게임** Windows 런타임 앱에 대한 새로운 DirectX 지원을 사용하여 흥미로운 게임을 개발할 수 있습니다.
- **XAML/DirectX interop** XAML과 DirectX를 모두 사용하는 Windows 런타임 앱이 효율적으로 상호 운용됩니다.
- **Windows 런타임 구성 요소 DLL 개발** 구성 요소 DLL 개발을 통해 Windows 런타임 환경을 확장할 수 있습니다.

### <a name="compiler-and-linker"></a>컴파일러 및 링커

- **자동 벡터화 도우미** 컴파일러는 코드에서 루프를 분석하고, 가능한 경우 모든 최신 프로세서에 있는 벡터 레지스터와 명령을 사용하는 명령을 내보냅니다. 이렇게 하면 루프가 더 빨리 실행됩니다. (스트리밍 SIMD 확장에 대한 프로세서 명령은 SSE로 알려져 있습니다.) 이 최적화는 자동으로 적용되므로 사용하도록 설정하거나 요청할 필요가 없습니다.
- **자동 평행화 도우미** 컴파일러는 코드에서 루프를 분석하고, 계산을 여러 코어 또는 프로세서에 분산시키는 명령을 내보냅니다. 이렇게 하면 루프가 더 빠르게 실행될 수 있습니다. 이 최적화는 기본적으로 사용하도록 설정되지 않으므로 요청해야 합니다. 대부분의 경우 코드에서 병렬화하려는 루프 바로 앞에 `#pragma loop(hint_parallel(N))`를 포함하는 것이 좋습니다.
- 자동 벡터화 도우미와 자동 평행화 도우미는 함께 작동하여 계산이 여러 코어에 분산되고 각 코어의 코드에서 벡터 레지스터를 사용합니다.

### <a name="new-in-visual-studio-2012-update-1"></a>Visual Studio 2012 업데이트 1의 새로운 기능

C++ 코드를 작성할 때 Windows XP를 대상으로 지정합니다.
Microsoft C++ 컴파일러 및 라이브러리를 사용하여 Windows XP 및 Windows Server 2003을 대상으로 지정할 수 있습니다.

#### <a name="parallel-programming-support"></a>병렬 프로그래밍 지원

##### <a name="c-accelerated-massive-parallelism-amp"></a>C++ AMP(Accelerated Massive Parallelism)

C++ AMP는 일반적으로 개별 그래픽 카드에서 GPU로 존재하는 데이터 병렬 하드웨어를 활용하여 C++ 코드의 실행을 가속화합니다. C++ AMP 프로그래밍 모델에는 다차원 배열, 인덱싱, 메모리 전송, 바둑판식 배열 및 수학 함수 라이브러리가 포함됩니다. C++ AMP 언어 확장 및 컴파일러 제한을 사용하여 CPU에서 GPU로 데이터를 이동하는 방법을 제어할 수 있습니다.

**디버깅할.** C++ AMP를 사용하여 GPU를 대상으로 하는 앱에 대한 디버깅 환경은 다른 C++ 앱의 디버깅과 같습니다. 여기에는 앞서 언급한 새로운 병렬 디버깅 추가 기능이 포함됩니다.

**작성.** C++ AMP 및 다른 Direct3D 기반 프로그래밍 모델을 기반으로 하는 GPU 작업에 대한 프로파일링 지원이 있습니다.

#### <a name="general-parallel-programming-enhancements"></a>향상된 일반 병렬 프로그래밍

다중 코어 및 다중 코어 아키텍처로 이동하는 하드웨어를 사용하면 개발자는 더 이상 단일 코어에서 증가하는 클럭 속도를 맞출 수 없습니다. 개발자는 동시성 런타임의 병렬 프로그래밍 지원을 통해 이러한 새 아키텍처를 활용할 수 있습니다.
Visual Studio 2010에는 정교한 데이터 흐름 파이프라인을 표현하여 동시성을 활용하는 기능과 함께 병렬 패턴 라이브러리와 같은 강력한 C++ 병렬 처리 라이브러리가 도입되었습니다. Visual Studio 2012에서 이러한 라이브러리는 개발자에게 가장 필요한 병렬 패턴에 대해 더 효율적인 성능, 더 많은 제어 및 더 다양한 지원을 제공하도록 확장되었습니다. 이제 제품에 포함된 기능은 다음과 같습니다.

- 비동기 및 연속성을 지원하는 풍부한 작업 기반 프로그래밍 모델
- 병렬 알고리즘은 분기 조인 병렬 처리(parallel_for, parallel_for with affinity, parallel_for_each, parallel_sort, parallel_reduce, parallel_transform)를 지원합니다.
- 동시성 안전 컨테이너 - priority_queue, queue, vector 및 map과 같은 std 데이터 구조의 스레드 안전 버전을 제공합니다.
- 비동기 에이전트 라이브러리 - 개발자가 동시 단위로 자연스럽게 분해하는 데이터 흐름 파이프라인을 표현하는 데 사용할 수 있습니다.
- 이 목록에 있는 패턴의 원활한 구성을 용이하게 하는 사용자 지정 가능한 스케줄러 및 리소스 관리자

##### <a name="general-parallel-debugging-enhancements"></a>향상된 일반 병렬 디버깅

Visual Studio 2012에서는 **병렬 태스크** 창과 **병렬 스택** 창 외에도 새로운 **병렬 조사식** 창을 제공하여 모든 스레드와 프로세스에서 식의 값을 검사하고 결과를 정렬 및 필터링할 수 있습니다. 또한 사용자 고유의 시각화 도우미를 사용하여 창을 확장할 수 있으며, 모든 도구 창에서 새로운 다중 프로세스 지원을 활용할 수 있습니다.

### <a name="ide"></a>IDE

**Visual Studio 템플릿 지원** Visual Studio 템플릿 기술을 사용하여 C++ 프로젝트 및 항목 템플릿을 작성할 수 있습니다.

**비동기 솔루션 로드** 프로젝트는 비동기적으로 로드됩니다. 즉, 솔루션의 주요 부분이 먼저 로드되어 작업을 더 빨리 시작할 수 있습니다.

**원격 디버깅을 위한 자동화된 배포** Visual C++에서 원격 디버깅을 위한 파일 배포가 간소화되었습니다. 프로젝트 상황에 맞는 메뉴의 **배포** 옵션은 디버깅 구성 속성에 지정된 파일을 원격 컴퓨터에 자동으로 복사합니다. 더 이상 파일을 원격 컴퓨터에 수동으로 복사할 필요가 없습니다.

**C++/CLI IntelliSense** C++/CLI는 IntelliSense를 완벽하게 지원합니다. 요약 정보, 매개 변수 도움말, 멤버 목록 및 자동 완성과 같은 IntelliSense 기능이 이제 C++/CLI에서 작동합니다. 또한 이 문서에 나오는 향상된 다른 IntelliSense 및 IDE 기능도 C++/CLI에서 작동합니다.

**더 다양한 IntelliSense 도구 설명** C++ IntelliSense 요약 정보 도구 설명에 더 다양한 XML 문서 주석 스타일 정보가 표시됩니다. XML 문서 주석이 있는 라이브러리의 API(예: C++ AMP)를 사용하는 경우 IntelliSense 도구 설명에 선언보다 더 많은 정보가 표시됩니다. 또한 코드에 XML 문서 주석이 있는 경우 IntelliSense 도구 설명에는 더 많은 정보가 표시됩니다.

**C++ 코드 구문** switch, if-else, for 루프 및 다른 기본 코드 구문에 대한 구조 코드는 멤버 목록 드롭다운 목록에서 사용할 수 있습니다. 목록에서 코드 부분을 선택하여 코드에 삽입한 다음 필요한 논리를 입력합니다. 또한 편집기에서 사용할 사용자 고유의 사용자 지정 코드 조각을 만들 수도 있습니다.

**향상된 멤버 목록** **멤버 목록** 드롭다운 목록은 코드 편집기에 코드를 입력할 때 자동으로 표시됩니다. 결과가 필터링되어 사용자가 입력하는 대로 관련 멤버만 표시됩니다. 멤버 목록에서 사용되는 필터링 논리의 종류는 **텍스트 편집기, C/C++** > **C/C++** > **고급** 아래의 **옵션** 대화 상자에서 제어할 수 있습니다.

**의미 체계 색 지정** 형식, 열거형, 매크로 및 다른 C++ 토큰에 대한 색이 기본적으로 지정됩니다.

**참조 강조 표시** 기호를 선택하면 현재 파일에서 기호의 모든 인스턴스가 강조 표시됩니다. **Ctrl** + **Shift** + **Up Arrow** **Ctrl** + **Shift** + 강조 표시 된 참조 간에 이동 하려면 ctrl shift 위쪽 화살표 또는 ctrl shift**아래쪽 화살표** 를 누릅니다. 이 기능은 **텍스트 편집기** > **C/C++** > **고급** 아래의 **옵션** 대화 상자에서 해제할 수 있습니다.

### <a name="application-lifecycle-management-tools"></a>Application Lifecycle Management 도구

#### <a name="static-code-analysis"></a>정적 코드 분석

C++에 대한 정적 분석은 더 다양한 오류 컨텍스트 정보, 더 많은 분석 규칙 및 더 나은 분석 결과를 제공하도록 업데이트되었습니다. 새 코드 분석 창에서 키워드, 프로젝트 및 심각도별로 메시지를 필터링할 수 있습니다. 창에서 메시지를 선택하면 코드 편집기에서 메시지가 트리거된 코드의 해당 줄이 강조 표시됩니다. 특정 C++ 경고의 경우 메시지에는 경고로 연결되는 실행 경로를 보여 주는 소스 줄이 나열됩니다. 의사 결정 지점 및 해당 특정 경로를 선택한 이유가 강조 표시됩니다.
코드 분석은 대부분의 Visual Studio 2012 버전에 포함되어 있습니다. Professional, Premium 및 Ultimate 버전에는 모든 규칙이 포함되어 있습니다. Windows 8 및 Windows Phone용 Express 버전에는 가장 중요한 경고가 포함되어 있습니다. Web Express 버전에는 코드 분석이 포함되어 있지 않습니다.
다른 코드 분석에 대해 향상된 기능 중 몇 가지는 다음과 같습니다.

- 새로운 동시성 경고를 사용하면 다중 스레드 C/C++ 프로그램에서 올바른 잠금 분야를 사용하고 있는지 확인하여 동시성 버그를 방지할 수 있습니다. 분석기에서 잠재적 경쟁 조건, 잠금 순서 반전, 호출자/호출 수신자 잠금 계약 위반, 일치 하지 않는 동기화 작업 및 기타 동시성 버그를 검색합니다.
- 규칙 집합을 사용하여 코드 분석 실행에 적용하려는 C++ 규칙을 지정할 수 있습니다.
- **코드 분석** 창에서 선택한 경고를 표시하지 않는 pragma를 소스 코드에 삽입할 수 있습니다.
- 새 버전의 Microsoft SAL(소스 코드 주석 언어)을 사용하여 함수에서 매개 변수를 사용하는 방법, 해당 매개 변수에 적용되는 가정 및 함수가 완료될 때 해당 함수에서 수행하는 보장을 설명하여 정적 코드 분석의 정확성과 완성도를 높일 수 있습니다.
- 64비트 C++ 프로젝트를 지원합니다.

#### <a name="updated-unit-test-framework"></a>업데이트된 단위 테스트 프레임워크

Visual Studio에서 새로운 C++ 단위 테스트 프레임워크를 사용하여 C++ 단위 테스트를 작성합니다. 새 프로젝트 대화 상자의 Visual C++ 범주 아래에 C++ 단위 테스트 프로젝트 템플릿을 배치하여 기존 C++ 솔루션에 새 단위 테스트 프로젝트를 추가합니다. Unittest1.cpp 파일에 생성된 TEST_METHOD 코드 스텁에 단위 테스트를 작성합니다. 테스트 코드가 작성되면 솔루션을 빌드합니다. 테스트를 실행하려면 **보기** > **다른 창** > **단위 테스트 탐색기** 등을 선택하여 **단위 테스트 탐색기** 창을 연 다음, 원하는 테스트 사례에 대한 바로 가기 메뉴에서 **선택한 테스트 실행**을 선택합니다. 테스트 실행이 완료되면 동일한 창에서 테스트 결과와 추가 스택 추적 정보를 볼 수 있습니다.

#### <a name="architecture-dependency-graphs"></a>아키텍처 종속성 그래프

코드를 더 잘 이해하기 위해 솔루션의 이진 파일, 클래스, 네임스페이스 및 포함 파일에 대한 종속성 그래프를 생성할 수 있습니다. 메뉴 모음에서 **아키텍처**  >  **생성 종속성 그래프**를 선택 하 고 **솔루션** 또는 **포함 파일** 에 대 한 종속성 그래프를 생성 합니다. 그래프 생성이 완료되면 각 노드를 펼치고, 노드 간을 이동하여 종속성 관계를 알아보고, 노드의 바로 가기 메뉴에서 **콘텐츠 보기**를 선택하여 소스 코드를 탐색할 수 있습니다. 포함 파일에 대 한 종속성 그래프를 생성 하려면 \* .cpp 소스 코드 파일 또는 .h 헤더 파일에 대 한 바로 가기 메뉴에서 \* **포함 파일의 그래프 생성**을 선택 합니다.

#### <a name="architecture-explorer"></a>아키텍처 탐색기

**아키텍처 탐색기**를 사용하여 C++ 솔루션, 프로젝트 또는 파일의 자산을 탐색할 수 있습니다. 메뉴 모음에서 **아키텍처**  >  **Windows**  >  **아키텍처 탐색기**를 선택 합니다. 관심 있는 노드(예: **클래스 뷰**)를 선택할 수 있습니다. 이 경우 도구 창의 오른쪽이 네임스페이스 목록으로 확장됩니다. 네임스페이스를 선택하면 이 네임스페이스의 클래스, 구조체 및 열거형 목록이 새 열에 표시됩니다. 이러한 자산을 계속 탐색하거나 맨 왼쪽의 열로 돌아가서 다른 쿼리를 시작할 수 있습니다. **아키텍처 탐색기로 코드 찾기**를 참조하세요.

#### <a name="code-coverage"></a>코드 검사

코드 검사에서 런타임에 이진 파일을 동적으로 계측하도록 업데이트되었습니다. 이렇게 하면 구성 오버헤드가 줄어들고 성능이 향상됩니다. 또한 C++ 앱에 대한 단위 테스트에서 코드 검사 데이터를 수집할 수도 있습니다. C++ 단위 테스트를 만들었으면 **단위 테스트 탐색기**를 사용하여 솔루션의 테스트를 검색할 수 있습니다. 단위 테스트를 실행하고 이 테스트에 대한 코드 검사 데이터를 수집하려면 **단위 테스트 탐색기**에서 **코드 검사 분석**을 선택합니다. 메뉴 모음의 **코드 검사 결과** 창에서 코드 적용 결과를 검사하고, **테스트** > **창** > **코드 검사 결과**를 차례로 선택할 수 있습니다.

## <a name="whats-new-for-c-in-visual-studio-2010"></a>Visual Studio 2010의 새로운 C++ 기능

### <a name="c-compiler-and-linker"></a>C++ 컴파일러 및 링커

**auto 키워드입니다.** 키워드에는 **`auto`** 새로운 용도가 있습니다. 키워드의 기본 의미를 사용 **`auto`** 하 여 변수 선언의 초기화 식에서 형식이 추론 되는 변수를 선언 합니다. `/Zc:auto`컴파일러 옵션은 키워드의 새 의미 또는 이전 의미를 호출 합니다 **`auto`** .

**decltype 형식 지정자** **`decltype`** 형식 지정자는 지정 된 식의 형식을 반환 합니다. **`decltype`** 키워드와 함께 형식 지정자를 사용 **`auto`** 하 여 컴파일러 에서만 사용 되는 복합 형식 또는 알려진 형식을 선언 합니다. 예를 들어 조합을 사용하여 반환 형식이 해당 템플릿 인수의 형식에 따라 달라지는 템플릿 함수를 선언합니다. 또는 다른 함수를 호출하는 템플릿 함수를 선언한 다음 호출된 함수의 반환 형식을 반환합니다.

**람다 식.** 람다 함수에는 함수 본문만 있고 이름이 없습니다. 람다 함수는 함수 포인터와 함수 개체의 가장 좋은 특성을 결합합니다. 람다 함수 자체를 함수 개체가 아닌 템플릿 함수 매개 변수로 사용 하거나 키워드와 함께 사용 **`auto`** 하 여 형식이 람다 인 변수를 선언 합니다.

**Rvalue 참조** rvalue 참조 선언자(&&)는 rvalue에 대한 참조를 선언합니다. rvalue 참조를 사용하면 이동 의미 체계 및 완벽한 전달을 통해 더 효율적인 생성자, 함수 및 템플릿을 작성할 수 있습니다.

**static_assert 선언** **`static_assert`** 선언은 런타임에 테스트 하는 다른 어설션 메커니즘과 달리 컴파일 타임에 소프트웨어 어설션을 테스트 합니다. 어설션이 실패하면 컴파일이 실패하고 지정된 오류 메시지가 발생됩니다.

**nullptr 및 __nullptr 키워드** MSVC를 사용 하면 **`nullptr`** 네이티브 코드 또는 관리 코드와 함께 키워드를 사용할 수 있습니다. **`nullptr`** 키워드는 개체 핸들, 내부 포인터 또는 네이티브 포인터 형식이 개체를 가리키지 않음을 나타냅니다. 컴파일러 **`nullptr`** 옵션을 사용 하는 경우 컴파일러는 관리 코드로 해석 하 `/clr` 고, 옵션을 사용 하지 않는 경우 네이티브 코드를 해석 합니다 `/clr` .
Microsoft 관련 **__nullptr** 키워드는와 동일한 의미를 **`nullptr`** 갖지만 네이티브 코드에만 적용 됩니다. 컴파일러 옵션을 사용 하 여 네이티브 C/c + + 코드를 컴파일하는 경우 `/clr` 컴파일러는 **`nullptr`** 키워드가 네이티브 또는 관리 용어 인지 여부를 확인할 수 없습니다. 컴파일러에 대한 의도를 명확히 하려면, nullptr 키워드를 사용하여 관리되는 용어를 지정하고, **__nullptr**을 사용하여 네이티브 용어를 지정합니다.

**`/Zc:trigraphs` 컴파일러 옵션입니다.** 삼중자는 기본적으로 지원되지 않습니다. **`/Zc:trigraphs`** 삼중 자 지원을 사용 하려면 컴파일러 옵션을 사용 합니다.
삼중자는 두 개의 연속 물음표(??) 뒤에 고유한 세 번째 문자로 구성됩니다. 컴파일러는 삼중자를 해당 문장 부호 문자로 바꿉니다. 예를 들어 컴파일러는 ??= 삼중자를 #(숫자 기호) 문자로 바꿉니다. 특정 문장 부호 문자가 포함되지 않은 문자 집합을 사용하는 C 소스 파일에서 삼중자를 사용합니다.

**새 프로필 기반 최적화 옵션** PogoSafeMode는 애플리케이션을 최적화할 때 안전 모드 또는 고속 모드를 사용할지 여부를 지정할 수 있는 새로운 프로필 기반 최적화 옵션입니다. 안전 모드는 스레드로부터 안전하지만 고속 모드보다 더 느립니다. 고속 모드가 기본 동작입니다.

**새 /clr:nostdlib CLR(공용 언어 런타임) 옵션** `/clr`(공용 언어 런타임 컴파일)에 대한 새 옵션이 추가되었습니다. 동일한 라이브러리의 서로 다른 버전이 포함되면 컴파일 오류가 발생합니다. 새 옵션을 사용하면 프로그램에서 지정된 버전을 사용할 수 있도록 기본 CLR 라이브러리를 제외할 수 있습니다.

**새 pragma 지시문 detect_mismatch** detect_mismatch pragma 지시문을 사용하면 동일한 이름을 가진 다른 태그와 비교되는 태그를 파일에 추가할 수 있습니다. 같은 이름에 대해 여러 값이 있으면 링커에서 오류가 발생합니다.

**XOP, FMA4 및 LWP 내장 함수** Visual Studio 2010 SP1 프로세서 기술용으로 추가된 XOP, FMA4 및 LWP 내장 함수를 지원하는 새로운 내장 함수가 추가되었습니다. 특정 컴퓨터에서 지원되는 프로세서 기술을 확인하려면 __cpuid, __cpuidex를 사용합니다.

### <a name="visual-studio-c-projects-and-the-build-system"></a>Visual Studio C++ 프로젝트 및 빌드 시스템

**MSBuild.** VCBuild.exe를 대체하는 MSBuild.exe를 사용하여 Visual C++ 솔루션과 프로젝트를 빌드합니다. MSBuild는 다른 Visual Studio 언어 및 프로젝트 형식에서 사용되는 것과 동일한 유연하고 확장할 수 있는 XML 기반 빌드 도구입니다. 이러한 변경에 따라 이제 Visual Studio C++ 프로젝트 파일은 XML 파일 형식을 사용하고 .vcxproj 파일 이름 확장명을 갖습니다. Visual Studio 이전 버전의 Visual Studio C++ 프로젝트 파일은 자동으로 새 파일 형식으로 변환됩니다.

**VC++ 디렉터리** VC++ 디렉터리 설정이 두 위치에 있습니다. 프로젝트 속성 페이지를 사용하여 VC++ 디렉터리에 대한 프로젝트별 값을 설정합니다. **속성 관리자** 및 속성 시트를 사용하여 VC++ 디렉터리에 대한 구성별 글로벌 값을 설정합니다.

**프로젝트 간 종속성** 이전 릴리스에서는 정의된 프로젝트 간 종속성이 솔루션 파일에 저장되었습니다. 이러한 솔루션을 새 프로젝트 파일 형식으로 변환하면 종속성이 프로젝트 간 참조로 변환됩니다. 솔루션 종속성 및 프로젝트 간 참조 개념이 다르기 때문에 이러한 변경으로 인해 애플리케이션에 영향을 줄 수 있습니다.

**매크로 및 환경 변수** 새로운 _ITERATOR_DEBUG_LEVEL 매크로는 반복기에 대한 디버깅 지원을 호출합니다. 이 매크로는 이전의 _SECURE_SCL 및 _HAS_ITERATOR_DEBUGGING 매크로 대신 사용합니다.

### <a name="visual-c-libraries"></a>Visual C++ 라이브러리

**동시성 런타임 라이브러리** 동시성 런타임 프레임워크는 동시에 실행되는 애플리케이션과 구성 요소를 지원하며, Visual C++에서 동시 애플리케이션을 프로그래밍하기 위한 프레임워크입니다. 동시 애플리케이션 프로그래밍을 지원하기 위해 PPL(병렬 패턴 라이브러리)에서 세분화된 병렬 처리를 수행하기 위한 범용 컨테이너와 알고리즘을 제공합니다. 비동기 에이전트 라이브러리는 정교하지 않은 데이터 흐름 및 파이프라인 작업에 행위자 기반 프로그래밍 모델 및 메시지 전달 인터페이스를 제공합니다.

**표준 C++ 라이브러리** 다음 목록에서는 표준 C++ 라이브러리에 적용된 다양한 변경 내용에 대해 설명합니다.

- 새로운 rvalue 참조 C++ 언어 기능이 표준 템플릿 라이브러리의 다양한 기능에 대한 이동 의미 체계 및 완벽한 전달을 구현하는 데 사용됩니다. 이동 의미 체계 및 완벽한 전달은 변수 또는 매개 변수를 할당하는 작업의 성능을 크게 향상시킵니다.
- rvalue 참조는 `auto_ptr` 클래스보다 더 안전한 스마트 포인터 형식인 `unique_ptr` 클래스를 구현하는 데에도 사용됩니다. `unique_ptr` 클래스는 이동할 수 있지만 복사할 수는 없으며, 안전성에 영향을 주지 않고 엄격한 소유권 의미 체계를 구현하고, rvalue 참조를 인식하는 컨테이너에서 잘 작동합니다. `auto_ptr` 클래스는 사용되지 않습니다.
- , 및와 같은 15 개의 새 `find_if_not` 함수가 `copy_if` `is_sorted` 헤더에 추가 되었습니다 \<algorithm> .
- 헤더에서 \<memory> 새로운 make_shared 함수는 개체를 생성할 때 개체에 대 한 공유 포인터를 편리 하 고 강력 하 고 효율적으로 만드는 방법입니다.
- 단일 연결 된 목록은 헤더에서 지원 됩니다 \<forward_list> .
- 새 `cbegin`, `cend`, `crbegin` 및 `crend` 멤버 함수는 컨테이너를 통해 앞뒤로 이동하는 `const_iterator`를 제공합니다.
- \<system_error>헤더 및 관련 템플릿은 하위 수준 시스템 오류를 처리 하도록 지원 합니다. `exception_ptr` 클래스의 멤버는 스레드 간에 예외를 전송하는 데 사용할 수 있습니다.
- \<codecvt>헤더는 유니코드 문자의 다양 한 인코딩을 다른 인코딩으로 변환 하는 것을 지원 합니다.
- \<allocators>헤더는 노드 기반 컨테이너의 메모리 블록을 할당 하 고 해제 하는 데 도움이 되는 몇 가지 템플릿을 정의 합니다.
- 헤더에 대 한 여러 업데이트가 있습니다 \<random> .

### <a name="microsoft-foundation-class-mfc-library"></a>MFC(Microsoft Foundation Class) 라이브러리

**Windows 7 기능** MFC는 리본 UI(사용자 인터페이스), 작업 표시줄, 점프 목록, 탭 미리 보기, 축소판 그림 미리 보기, 진행률 표시줄, 아이콘 오버레이 및 검색 인덱싱과 같은 다양한 Windows 7 기능을 지원합니다. MFC에서 다양한 Windows 7 기능을 자동으로 지원하므로 기존 애플리케이션을 수정할 필요가 없습니다. 새 애플리케이션의 다른 기능을 지원하려면 MFC 애플리케이션 마법사를 사용하여 사용하려는 기능을 지정합니다.

**멀티 터치 인식** MFC는 멀티 터치 사용자 인터페이스가 있는 애플리케이션(예: Microsoft Surface 운영 체제용으로 작성된 애플리케이션)을 지원합니다. 멀티 터치 애플리케이션에서 터치 메시지의 조합인 Windows 터치 메시지와 제스처 메시지를 처리할 수 있습니다. 터치 및 제스처 이벤트에 대한 애플리케이션을 등록하기만 하면 운영 체제에서 멀티 터치 이벤트를 이벤트 처리기로 라우팅합니다.

**높은 DPI 인식** MFC 애플리케이션은 기본적으로 높은 DPI를 인식합니다. 애플리케이션이 높은 DPI(인치당 높은 도트 수)를 인식하는 경우 운영 체제에서 창, 텍스트 및 다른 UI 요소를 현재 화면 해상도에 맞게 조정할 수 있습니다. 즉 배율이 지정된 이미지가 올바르게 배치되고 클리핑되거나 픽셀화되지 않을 수 있습니다.

**다시 시작 관리자** 예기치 않게 닫히거나 다시 시작되는 경우 다시 시작 관리자에서 자동으로 문서를 저장하고 애플리케이션을 다시 시작합니다. 예를 들어 자동 업데이트로 인해 애플리케이션이 닫히면 다시 시작 관리자를 사용하여 해당 애플리케이션을 시작할 수 있습니다. 다시 시작 관리자를 사용하도록 애플리케이션을 구성하는 방법에 대한 자세한 내용은 **방법: 다시 시작 관리자 지원 추가**를 참조하세요.

**CTaskDialog.** `CTaskDialog` 클래스는 표준 `AfxMessageBox` 메시지 상자 대신 사용할 수 있습니다. `CTaskDialog` 클래스는 표준 메시지 상자보다 자세한 정보를 표시하고 수집합니다.

#### <a name="safeint-library"></a>SafeInt 라이브러리

새로운 SafeInt 라이브러리는 정수 오버플로를 고려하는 안전한 산술 연산을 수행합니다. 또한 이 라이브러리는 다른 종류의 정수도 비교합니다.

#### <a name="new-active-template-library-atl-macros"></a>새로운 ATL(액티브 템플릿 라이브러리) 매크로

PROP_ENTRY_TYPE 및 PROP_ENTRY_TYPE_EX 기능을 확장하기 위해 새 매크로가 ATL에 추가되었습니다. PROP_ENTRY_INTERFACE 및 PROP_ENTRY_INTERFACE_EX를 사용하면 유효한 CLSID 목록을 추가할 수 있습니다. PROP_ENTRY_INTERFACE_CALLBACK 및 PROP_ENTRY_INTERFACE_CALLBACK_EX를 사용하면 CLSID가 유효한지 여부를 결정하는 콜백 함수를 지정할 수 있습니다.

#### <a name="analyze-warnings"></a>/analyze 경고

대부분의 **`/analyze`** (엔터프라이즈 코드 분석) 경고는 CRT (C 런타임), MFC 및 ATL 라이브러리에서 제거 되었습니다.

#### <a name="animation-and-d2d-support"></a>애니메이션 및 D2D 지원

MFC는 애니메이션과 Direct2D 그래픽을 지원합니다. MFC 라이브러리에는 이 기능을 지원하는 몇 가지 새로운 MFC 클래스와 함수가 있습니다. 또한 D2D 개체와 애니메이션 개체를 프로젝트에 추가하는 방법을 보여 주는 두 가지의 새로운 연습이 있습니다. 이러한 연습은 **연습: MFC 프로젝트에 D2D 개체 추가** 및 **연습: MFC 프로젝트에 애니메이션 추가**입니다.

### <a name="ide"></a>IDE

**향상된 IntelliSense** Visual C++용 IntelliSense는 더 빠르고 정확하며 더 큰 프로젝트를 처리할 수 있도록 완전히 새롭게 디자인되었습니다. 이러한 향상을 얻기 위해 IDE에서는 개발자가 소스 코드를 보고 수정하는 방법과 IDE에서 소스 코드 및 프로젝트 설정을 사용하여 솔루션을 빌드하는 방법을 구분합니다.
이러한 업무 분리에 따라 검색 기능(예: **클래스 뷰** 및 새 **탐색 대상** 대화 상자)이 컴파일되지 않는 이전의 찾아보기 파일(.ncb)을 대체하는 새로운 SQL Server 데스크톱 데이터베이스 파일(.sdf)을 기반으로 하는 시스템에서 처리됩니다. 요약 정보, 자동 완성 및 매개 변수 도움말과 같은 IntelliSense 기능은 필요한 경우에만 변환 단위를 구문 분석합니다. 새로운 **호출 계층 구조** 창과 같은 하이브리드 기능은 찾아보기와 IntelliSense 기능을 결합하여 사용합니다.
IntelliSense는 현재 필요한 정보만 처리하므로 IDE의 응답성이 향상됩니다. 또한 최신 정보이므로 IDE 뷰 및 창이 더욱 정확합니다. 마지막으로 IDE 인프라가 더 효율적으로 구성되고, 관련 기능이 다양하고, 확장성이 뛰어나므로 더 큰 프로젝트를 처리할 수 있습니다.

**향상된 IntelliSense 오류** IDE는 IntelliSense가 손실될 수 있는 오류를 더 효율적으로 검색하고 그 아래에 빨간색 물결선 밑줄을 표시합니다. 또한 IDE는 IntelliSense 오류를 **오류 목록 창**에 보고합니다. 문제가 발생되는 코드를 표시하려면 **오류 목록 창**에서 해당 오류를 두 번 클릭합니다.

**#include 자동 완성 기능** IDE는 `#include` 키워드에 대한 자동 완성 기능을 지원합니다. `#include`를 입력하면 IDE에서 유효한 헤더 파일의 드롭다운 목록 상자를 만듭니다. 파일 이름을 입력하여 계속하면 IDE에서 입력한 내용에 기반하여 목록을 필터링합니다. 언제든지 목록에서 포함할 파일을 선택할 수 있습니다. 이렇게 하면 정확한 파일 이름을 알지 못해도 파일을 빠르게 포함할 수 있습니다.

**로 이동 합니다.** **탐색 대상** 대화 상자를 사용하면 프로젝트에서 지정된 문자열과 일치하는 모든 기호와 파일을 검색할 수 있습니다. 검색 문자열에 추가 문자를 입력하는 대로 검색 결과가 바로 수정됩니다. **결과** 피드백 필드에는 찾은 항목의 수가 표시되고, 이를 통해 검색을 제한할지 여부를 결정할 수 있습니다. **종류/범위**, **위치** 및 **미리 보기** 피드백 필드를 사용하면 비슷한 이름의 항목을 쉽게 구분할 수 있습니다. 또한 이 기능을 확장하여 다른 프로그래밍 언어도 지원할 수 있습니다.

**병렬 디버깅 및 프로파일링** Visual Studio 디버거는 동시성 런타임을 인식하고 병렬 처리 애플리케이션의 문제를 해결하는 데 도움을 줍니다. 새 동시성 프로파일러 도구를 사용하여 애플리케이션의 전체 동작을 시각화할 수 있습니다. 또한 새 도구 창을 사용하여 작업 및 해당 호출 스택의 상태도 시각화할 수 있습니다.

**리본 디자이너.** **리본 디자이너**는 MFC 리본 UI를 만들고 수정할 수 있는 그래픽 편집기입니다. 최종 리본 UI는 XML 기반 리소스 파일(.mfcribbon-ms)로 표현됩니다. 기존 애플리케이션의 경우 몇 줄의 코드를 임시로 추가한 다음, **리본 디자이너**를 호출하여 현재 리본 UI를 캡처할 수 있습니다. 리본 리소스 파일이 만들어지면 손으로 쓴 리본 UI 코드를 리본 리소스가 로드되는 몇 개의 명령문으로 바꿀 수 있습니다.

**호출 계층 구조입니다.** **호출 계층 구조** 창에서는 특정 함수 또는 특정 함수를 호출 하는 모든 함수에 의해 호출 되는 모든 함수를 탐색할 수 있습니다.

### <a name="tools"></a>도구

**MFC 클래스 마법사.** Visual C++ 2010에서는 잘 알려진 MFC 클래스 마법사 도구를 다시 가져옵니다. MFC 클래스 마법사는 소스 파일 집합을 수동으로 수정하지 않고도 클래스, 메시지 및 변수를 프로젝트에 추가할 수 있는 편리한 방법입니다.

**ATL 컨트롤 마법사.** ATL 컨트롤 마법사는 더 이상 `ProgID` 필드를 자동으로 채우지 않습니다. ATL 컨트롤에 `ProgID`가 없으면 다른 도구가 이 도구와 작동하지 않을 수 있습니다. 컨트롤에 `ProgID`가 있어야 하는 도구의 한 예로 **활성 컨트롤 삽입** 대화 상자가 있습니다. 대화 상자에 대 한 자세한 내용은 [ActiveX 컨트롤 삽입](../windows/adding-editing-or-deleting-controls.md#insert-activex-controls)을 참조 하세요.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft 매크로 어셈블러 참조

YMMWORD 데이터 형식을 추가하면 Intel AVX(고급 벡터 확장) 명령에 포함된 256비트 멀티미디어 피연산자를 지원합니다.

## <a name="whats-new-for-c-in-visual-studio-2008"></a>Visual Studio 2008의 새로운 C++ 기능

### <a name="visual-c-integrated-development-environment-ide"></a>Visual C# IDE(통합 개발 환경)

- ATL, MFC 및 Win32 애플리케이션에서 만든 대화 상자는 이제 Windows Vista 스타일 지침을 준수합니다. Visual Studio 2008을 사용하여 새 프로젝트를 만드는 경우 애플리케이션에 삽입하는 모든 대화 상자는 Windows Vista 스타일 지침을 따릅니다. 이전 버전의 Visual Studio를 사용하여 만든 프로젝트를 다시 컴파일하면 기존 대화 상자에서 이전과 동일한 모양을 유지합니다. 대화 상자를 애플리케이션에 삽입하는 방법에 대한 자세한 내용은 **대화 상자 편집기**를 참조하세요.

- **ATL 프로젝트** 마법사에는 이제 모든 사용자에 대한 구성 요소를 등록하는 옵션이 있습니다. Visual Studio 2008부터는 **모든 사용자에 대한 구성 요소 등록**을 선택하지 않으면, **ATL 프로젝트** 마법사에서 만든 COM 구성 요소 및 형식 라이브러리가 레지스트리의 HKEY_CURRENT_USER 노드에 등록됩니다.
- **ATL 프로젝트** 마법사는 더 이상 특성 사용 ATL 프로젝트를 만드는 옵션을 제공하지 않습니다. Visual Studio 2008부터 **ATL 프로젝트** 마법사에는 새 프로젝트의 특성 사용 상태를 변경할 수 있는 옵션이 없습니다. 이제 마법사에서 만드는 새 ATL 프로젝트는 모두 특성을 사용하지 않습니다.
- 레지스트리에 대한 쓰기를 리디렉션할 수 있습니다. Windows Vista가 도입됨에 따라 레지스트리의 특정 영역에 대한 쓰기에서는 프로그램을 관리자 모드에서 실행해야 합니다. 항상 관리자 모드에서 Visual Studio를 실행하지 않는 것이 좋습니다. 사용자별 리디렉션은 프로그래밍을 변경하지 않고 자동으로 레지스트리 쓰기를 HKEY_CLASSES_ROOT에서 HKEY_CURRENT_USER로 리디렉션합니다.
- **클래스 디자이너**에서는 네이티브 C++ 코드에 대한 지원을 제한합니다. 이전 버전의 Visual Studio에서 **클래스 디자이너**는 Visual C # 및 Visual Basic에서만 작동했습니다. 이제 c + + 사용자가 **클래스 디자이너**를 사용할 수 있지만 읽기 전용 모드 에서만 가능 합니다. C++에서 **클래스 디자이너**를 사용하는 방법에 대한 자세한 내용은 **클래스 디자이너에서 Visual C++ 코드로 작업**을 참조하세요.
- 프로젝트 마법사에는 더 이상 C++ SQL Server 프로젝트를 만들 수 있는 옵션이 없습니다. Visual Studio 2008부터 새 프로젝트 마법사에 C++ SQL Server 프로젝트를 만드는 옵션이 없습니다. 이전 버전의 Visual Studio를 사용하여 만든 SQL Server 프로젝트는 제대로 컴파일되고 작동합니다.

### <a name="visual-c-libraries"></a>Visual C++ 라이브러리

#### <a name="general"></a>일반

- 애플리케이션은 특정 버전의 Visual C++ 라이브러리에 바인딩될 수 있습니다. 경우에 따라 릴리스 후에 Visual C++ 라이브러리의 업데이트에 따라 애플리케이션이 달라집니다. 이 경우 이전 버전의 라이브러리가 있는 컴퓨터에서 애플리케이션을 실행하면 예기치 않은 동작이 발생할 수 있습니다. 이제 애플리케이션을 특정 버전의 라이브러리에 바인딩하여 이전 버전의 라이브러리가 있는 컴퓨터에서 실행되지 않도록 할 수 있습니다.

#### <a name="stlclr-library"></a>STL/CLR 라이브러리

- 이제 STL/CLR 라이브러리가 Visual C++에 포함되어 있습니다. STL/CLR 라이브러리는 C++ 및 .NET Framework CLR(공용 언어 런타임)에서 사용하기 위한 표준 C++ 라이브러리의 하위 집합인 STL(표준 템플릿 라이브러리) 패키지입니다. STL/CLR을 사용하면 관리되는 환경에서 STL의 모든 컨테이너, 반복기 및 알고리즘을 사용할 수 있습니다.

#### <a name="mfc-library"></a>MFC 라이브러리

- Windows Vista는 일반 컨트롤을 지원합니다. Windows Vista의 기능을 지원하거나 현재 MFC 클래스의 기능을 향상시키기 위해 18개의 새 클래스 또는 기존 클래스에 150개 이상의 메서드가 추가되었습니다.
- 새 `CNetAddressCtrl` 클래스를 사용하면 IPv4 및 IPv6 주소 또는 DNS 이름을 입력하고 유효성을 검사할 수 있습니다.
- 새 `CPagerCtrl` 클래스는 Windows Pager 컨트롤의 사용을 간소화합니다.
- 새 `CSplitButton` 클래스를 사용하면 Windows SplitButton 컨트롤을 사용하여 기본 또는 선택적 작업을 쉽게 선택할 수 있습니다.

#### <a name="c-support-library"></a>C++ 지원 라이브러리

- C++은 마샬링 라이브러리를 도입했습니다. 마샬링 라이브러리는 네이티브 환경과 관리되는 환경 간에 데이터를 마샬링하는 쉽고 최적화된 방법을 제공합니다. 이 라이브러리는 PInvoke 사용과 같이 더 복잡하고 덜 효율적인 방법에 대한 대안입니다. 자세한 내용은 **C++ 마샬링 개요**를 참조하세요.

#### <a name="atl-server"></a>ATL 서버

- ATL 서버는 공유 소스 프로젝트로 릴리스됩니다.
- 대부분의 ATL Server 코드베이스는 CodePlex에서 공유 소스 프로젝트로 릴리스되었으며, Visual Studio 2008의 일부로는 설치되지 않습니다. ATL 서버와 관련된 여러 파일이 더 이상 Visual Studio의 일부로 제공되지 않습니다. 제거된 파일 목록은 **제거된 ATL 서버 파일**을 참조하세요.
- atlenc.h의 데이터 인코딩 및 디코딩 클래스와 atlutil.h 및 atlpath.h의 유틸리티 함수 및 클래스는 이제 ATL 라이브러리의 일부입니다.
- 이전 버전의 Visual Studio 버전이 지원되는 한 이러한 버전에 포함된 ATL Server 버전은 계속 지원됩니다. CodePlex에서는 ATL 서버 코드가 커뮤니티 프로젝트로 계속 개발됩니다. Microsoft는 ATL Server의 CodePlex 버전을 지원하지 않습니다.

### <a name="visual-c-compiler-and-linker"></a>Visual C++ 컴파일러 및 링커

#### <a name="compiler-changes"></a>컴파일러 변경 내용

- 컴파일러는 관리되는 증분 빌드를 지원합니다. 이 옵션을 지정하면 참조된 어셈블리가 변경될 때 컴파일러에서 코드를 다시 컴파일하지 않습니다. 대신 증분 빌드를 수행합니다. 변경 내용이 종속 코드에 적용되는 경우에만 파일이 다시 컴파일됩니다.
- ATL 서버와 관련된 특성은 더 이상 지원되지 않습니다. 컴파일러는 ATL 서버와 직접 관련된 여러 특성을 더 이상 지원하지 않습니다. 제거된 특성의 전체 목록은 "주요 변경 내용"을 참조하세요.
- 컴파일러는 Intel Core microarchitecture를 지원합니다. 컴파일러에는 코드 생성 중에 Intel Core microarchitecture 튜닝이 포함됩니다. 이 튜닝은 기본적으로 사용되며 Pentium 4 및 다른 프로세서에도 도움이 되므로 비활성화할 수 없습니다.
- 내장 함수에는 최신 AMD 및 Intel 프로세서가 지원됩니다. 몇 가지 새로운 내장 명령이 최신 AMD 및 Intel 프로세서에서 더 많은 기능을 지원합니다. 새로운 내장 함수에 대한 자세한 내용은 **보충 스트리밍 SIMD 확장 3 지침**, **스트리밍 SIMD 확장 4 지침**, **SSE4A 및 고급 비트 조작 내장 함수**, **AES 내장 함수**, **_mm_clmulepi64_si128** 및 **__rdtscp**를 참조하세요.
- `__cpuid` 함수가 업데이트됩니다. `__cpuid`, `__cpuidex` 함수는 AMD 및 Intel 프로세서의 최신 수정 버전에서 몇 가지 새로운 기능을 지원합니다. `__cpuidex` 내장 함수는 최신 프로세서에서 자세한 정보를 수집합니다.
- `/MP` 컴파일러 옵션은 전체 빌드 시간을 줄여줍니다. `/MP` 옵션을 사용하면 파일을 동시에 컴파일하는 여러 프로세스를 만들어 여러 원본 파일을 컴파일하는 데 걸리는 총 시간을 크게 줄일 수 있습니다. 이 옵션은 특히 하이퍼스레딩, 다중 프로세서 또는 다중 코어를 지원하는 컴퓨터에서 특히 유용합니다.
- `/Wp64`컴파일러 옵션 및 **`__w64`** 키워드는 사용 되지 않습니다. `/Wp64` **`__w64`** 64 비트 이식성 문제를 검색 하는 컴파일러 옵션 및 키워드는 더 이상 사용 되지 않으며 이후 버전의 컴파일러에서 제거 될 예정입니다. 이 컴파일러 옵션과 키워드 대신 64비트 플랫폼을 대상으로 하는 MSVC를 사용합니다.
- `/Qfast_transcendentals`는 초월 함수에 대한 인라인 코드를 생성합니다.
- `/Qimprecise_fwaits`는 `/fp:except` 컴파일러 옵션을 사용할 때 블록을 사용하는 fwait 내부 명령을 제거합니다.

### <a name="linker-changes"></a>링커 변경 내용

- 사용자 계정 컨트롤 정보가 Visual C++ 링커(link.exe)를 통해 실행 파일에 대한 매니페스트 파일에 포함됩니다. 이 기능은 기본적으로 사용하도록 설정됩니다. 이 기능을 사용 하지 않도록 설정하는 방법 또는 기본 동작을 수정하는 방법에 대한 자세한 내용은 `/MANIFESTUAC`(매니페스트에 UAC 정보 포함)를 참조하세요.
- 링커에는 Windows Vista의 ASLR(Address Space Layout Randomization) 기능을 사용하도록 설정할 수 있는 `/DYNAMICBASE` 옵션이 있습니다. 이 옵션은 로드 시 애플리케이션을 임의로 다시 지정하는지 여부를 나타내기 위해 실행 파일의 헤더를 수정합니다.

## <a name="whats-new-for-c-in-visual-studio-2005"></a>Visual Studio 2005의 새로운 C++ 기능

Visual C++ 2005 서비스 팩 1에서 새로 추가된 기능은 다음과 같습니다.

### <a name="intrinsics-for-x86-and-x64"></a>x86 및 x64 내장 함수

- __halt
- __lidt
- __nop
- __readcr8
- __sidt
- __svm_clgi
- __svm_invlpga
- __svm_skinit
- __svm_stgi
- __svm_vmload
- __svm_vmrun
- __svm_vmsave
- __ud2
- __vmx_off
- __vmx_vmptrst
- __writecr8

### <a name="intrinsics-for-x64-only"></a>x64 전용 내장 함수

- __vmx_on
- __vmx_vmclear
- __vmx_vmlaunch
- __vmx_vmptrld
- __vmx_vmread
- __vmx_vmresume
- __vmx_vmwrite

### <a name="new-language-keywords"></a>새 언어 키워드

__sptr, __uptr

### <a name="new-compiler-features"></a>새 컴파일러 기능

이 릴리스의 컴파일러에는 주요 변경 내용이 있습니다.

- 64비트 네이티브 및 크로스 컴파일러
- `/analyze`(엔터프라이즈 코드 분석) 컴파일러 옵션이 추가되었습니다.
- `/bigobj` 컴파일러 옵션이 추가되었습니다.
- `/clr:pure`, `/clr:safe` 및 `/clr:oldSyntax`가 추가되었습니다. (나중에 Visual Studio 2015에서 사용이 중단되었으며, Visual Studio 2017에서 제거되었습니다.)
- 사용되지 않는 컴파일러 옵션: 이 릴리스에서는 많은 컴파일러 옵션이 더 이상 사용되지 않습니다. 자세한 내용은 **사용되지 않는 컴파일러 옵션**을 참조하세요.
- `/clr` 코드의 이중 썽킹이 줄어듭니다. 자세한 내용은 **이중 썽킹(C++)** 을 참조하세요.
- `/EH`(예외 처리 모델) 또는 `/EHs`는 throw 이외의 다른 방식으로 발생하는 예외를 catch하는 데 더 이상 사용할 수 없습니다. 대신 `/EHa`를 사용합니다.
- `/errorReport`(내부 컴파일러 오류 보고) 컴파일러 옵션이 추가되었습니다.
- `/favor`(64에 대한 최적화) 컴파일러 옵션이 추가되었습니다.
- `/FA`, `/Fa`(목록 파일) 컴파일러 옵션이 추가되었습니다.
- `/FC`(진단의 소스 코드 파일에 대한 전체 경로) 컴파일러 옵션이 추가되었습니다.
- `/fp`(부동 소수점 동작 지정) 컴파일러 옵션이 추가되었습니다.
- `/G`(프로세서 최적화) 옵션 컴파일러 옵션이 추가되었습니다.
- `/G`(프로세서 최적화) 옵션 컴파일러 옵션이 추가되었습니다.
- `/G3`, `/G4`, `/G5`, `/G6`, `/G7` 및 `/GB` 컴파일러 옵션이 제거되었습니다. 컴파일러는 이제 모든 아키텍처에 대해 최상의 출력 파일을 만들려고 하는 "복합 모델"을 사용합니다.
- `/Gf` 는 제거되었습니다. 대신 `/GF`(중복 문자열 제거)를 사용합니다.
- `/GL`(전체 프로그램 최적화)이 `/CLRHEADER`와 호환됩니다.
- `/GR`는 기본적으로 사용됩니다.
- `/GS`(버퍼 보안 검사)는 취약한 포인터 매개 변수에 대한 보안을 제공합니다. `/GS`는 기본적으로 사용됩니다. `/GS`는 `/clr`(공용 언어 런타임 컴파일)을 사용하여 MSIL로 컴파일된 함수에서도 작동합니다.
- `/homeparams`(스택에 레지스터 매개 변수 복사) 컴파일러 옵션이 추가되었습니다.
- `/hotpatch`(핫 패치 가능 이미지 만들기) 컴파일러 옵션이 추가되었습니다.
- 인라인 함수 추론을 업데이트 했습니다. **`inline`** **`__inline`** **`__forceinline`** 자세한 내용은, 및 **inline_depth** 을 참조 하세요.
- 다양한 새 내장 함수가 추가되었으며, 이전에 문서화되지 않은 많은 내장 함수가 문서화되었습니다.
- 실패한 new에 대한 호출은 기본적으로 예외를 throw합니다.
- `/ML` 및 `/MLd` 컴파일러 옵션이 제거되었습니다. Visual C++는 더 이상 단일 스레드, 정적으로 연결된 CRT 라이브러리 지원을 지원하지 않습니다.
- 컴파일러는 `/O1`, `/O2`(크기 최소화, 속도 최대화), `/Og`(글로벌 최적화) 및 `/Ox`(전체 최적화)를 사용하여 컴파일할 때 활성화되는 명명된 반환 값 최적화를 구현했습니다.
- `/Oa` 컴파일러 옵션은 제거되었지만 자동으로 무시됩니다. `noalias` 또는 `restrict__declspec` 한정자를 사용하여 컴파일러에서 별칭 지정을 수행하는 방법을 지정합니다.
- `/Op` 컴파일러 옵션이 제거되었습니다. 대신 `/fp`(부동 소수점 동작 지정)를 사용합니다.
- OpenMP가 Visual C++에서 지원됩니다.
- `/openmp`(OpenMP 2.0 지원 활성화) 컴파일러 옵션이 추가되었습니다.
- `/Ow` 컴파일러 옵션은 제거되었지만 자동으로 무시됩니다. `noalias` 또는 `restrict__declspec` 한정자를 사용하여 컴파일러에서 별칭 지정을 수행하는 방법을 지정합니다.

### <a name="profile-guided-optimizations"></a>프로필 기반 최적화

- `/QI0f` 는 제거되었습니다.
- `/QIfdiv` 는 제거되었습니다.
- `/QIPF_B`(B CPU 단계별 실행에 대한 Errata) 컴파일러 옵션이 추가되었습니다.
- `/QIPF_C`(C CPU 단계별 실행에 대한 Errata) 컴파일러 옵션이 추가되었습니다.
- `/QIPF_fr32`(상위 96개 부동 소수점 레지스터 사용 안 함) 컴파일러 옵션이 추가되었습니다.
- `/QIPF_noPIC`(위치 종속성 코드 생성) 컴파일러 옵션이 추가되었습니다.
- `/QIPF_restrict_plabels`(런타임에 만든 함수가 없다고 가정) 컴파일러 옵션이 추가되었습니다.

### <a name="unicode-support-in-the-compiler-and-linker"></a>컴파일러 및 링커에서의 유니코드 지원

- `/vd`(생성 치환 비활성화)를 사용하면 생성되는 개체(/vd2)에서 dynamic_cast 연산자를 사용할 수 있습니다.
- `/YX` 컴파일러 옵션이 제거되었습니다. 대신 `/Yc`(미리 컴파일된 헤더 파일 만들기) 또는 `/Yu`(미리 컴파일된 헤더 파일 사용)를 사용합니다. 빌드 구성에서 `/YX`를 제거하고 nothing으로 바꾸면 빌드가 빨라질 수 있습니다.
- `/Zc:forScope`는 기본적으로 사용됩니다.
- `/Zc:wchar_t`는 기본적으로 사용됩니다.
- `/Zd` 컴파일러 옵션이 제거되었습니다. 줄 번호만 표시 디버깅 정보는 더 이상 지원되지 않습니다. 대신 `/Zi`를 사용합니다. 자세한 내용은 **/Z7, /Zi, /ZI(디버그 정보 형식)** 을 참조하세요.
- `/Zg`는 현재 C 소스 코드 파일에만 유효하며, C++ 소스 코드 파일에는 유효하지 않습니다.
- `/Zx`(최적화된 Itanium 코드 디버그) 컴파일러 옵션이 추가되었습니다.

### <a name="new-language-features"></a>새 언어 기능

- attributeattribute는 더 이상 사용되지 않습니다.
- `appdomain__declspec` 한정자가 추가되었습니다.
- `__clrcall` 호출 규칙이 추가되었습니다.
- 사용되지 않는 (C++) **declspec** 한정자를 사용하면, 사용자가 사용되지 않는 클래스 또는 함수에 액세스하려고 할 경우 컴파일 시 표시되는 문자열을 지정할 수 있습니다.
- **`dynamic_cast`** 연산자에 주요 변경 내용이 있습니다.
- 네이티브 열거형을 사용하면 기본 형식을 지정할 수 있습니다.
- `jitintrinsicdeclspec` 한정자가 추가되었습니다.
- `noaliasdeclspec` 한정자가 추가되었습니다.
- `process__declspec` 한정자가 추가되었습니다.
- **abstract**, **override** 및 **sealed**는 네이티브 컴파일에 유효합니다.
- **`__restrict`** 키워드가 추가 되었습니다.
- `restrictdeclspec` 한정자가 추가되었습니다.
- **`__thiscall`** 는 이제 키워드입니다.
- **`__unaligned`** 이제 키워드가 문서화 되었습니다.
- **`volatile`** (C + +)는 최적화와 관련 하 여 동작을 업데이트 했습니다.

### <a name="new-preprocessor-features"></a>새 전처리기 기능

- 미리 정의된 __CLR_VER 매크로가 추가되었습니다.
- 주석(C/C++) pragma는 링커 주석으로 `/MANIFESTDEPENDENCY`를 적용합니다. 주석에 대한 exestr 옵션은 더 이상 사용되지 않습니다.
- `embedded_idl` 특성(`#import` 지시문)에서 선택적 매개 변수를 사용합니다.
- `fenv_access` pragma
- `float_control` pragma
- `fp_contract` pragma
- pragma unmanaged, pragma unmanaged 및 unmanaged 섹션에 전역 변수가 있는 경우 전역 변수가 선언된 순서대로 초기화되지 않습니다. 예를 들어 unmanaged 전역 변수가 managed 전역 변수로 초기화되고 완전히 생성된 관리되는 개체가 필요한 경우 이는 잠재적인 주요 변경 내용입니다.
- init_seg로 지정된 섹션은 이제 읽기 전용이므로 이전 버전과 같이 읽기/쓰기가 아닙니다.
- inline_depth의 기본값은 16입니다. Visual C++ .NET 2003에서도 기본값인 16이 적용되었습니다.
- 미리 정의된 _INTEGRAL_MAX_BITS 매크로가 추가되었습니다. "미리 정의된 매크로"를 참조하세요.
- 미리 정의된 _M_CEE, _M_CEE_PURE 및 _M_CEE_SAFE 매크로가 추가되었습니다. "미리 정의된 매크로"를 참조하세요.
- 미리 정의된 _M_IX86_FP 매크로가 추가되었습니다.
- 미리 정의된 _M_X64 매크로가 추가되었습니다.
- `make_public` pragma
- `managed`, `unmanaged` pragma 구문이 업데이트되었습니다(이제 `push` 및 `pop` 포함).
- mscorlib.dll은 모든 `/clr` 컴파일의 `#using` 지시문에서 암시적으로 참조됩니다.
- 미리 정의된 _OPENMP매크로가 추가되었습니다.
- optimize pragma가 업데이트되었고, a 및 w는 더 이상 유효한 매개 변수가 아닙니다.
- no_registry#import 특성이 추가되었습니다.
- `region``endregion` pragmas가 추가되었습니다
- 미리 정의된 _VC_NODEFAULTLIB 매크로가 추가되었습니다.
- variadic 매크로가 구현되었습니다.
- `vtordisp`는 더 이상 사용되지 않으며, 이후 Visual C++ 릴리스에서 제거됩니다.
- `warning` pragma에는 이제 표시 안 함 지정자가 있습니다.

### <a name="new-linker-features"></a>새 링커 기능

- 모듈(비어셈블리 MSIL 출력 파일)은 링커에 대한 입력으로 허용됩니다.
- `/ALLOWISOLATION`(매니페스트 조회) 링커 옵션이 추가되었습니다.
- `/ASSEMBLYRESOURCE`(관리되는 리소스 포함)가 업데이트되어 어셈블리에서 리소스 이름을 지정하고 리소스가 어셈블리에서 private가 되도록 지정할 수 있습니다.
- `/CLRIMAGETYPE`(CLR 이미지 형식 지정) 링커 옵션이 추가되었습니다.
- `/CLRSUPPORTLASTERROR`(PInvoke 호출의 마지막 오류 코드 유지) 링커 옵션이 추가되었습니다.
- `/CLRTHREADATTRIBUTE`(CLR 스레드 특성 설정) 링커 옵션이 추가되었습니다.
- `/CLRUNMANAGEDCODECHECK`(SuppressUnmanagedCodeSecurityAttribute 추가) 링커 옵션이 추가되었습니다.
- `/ERRORREPORT`(내부 링커 오류 보고) 링커 옵션이 추가되었습니다.
- `/EXETYPE` 링커 옵션이 제거되었습니다. 링커는 더 이상 Windows 95 및 Windows 98 디바이스 드라이버를 만들도록 지원하지 않습니다. 적절한 DDK를 사용하여 이러한 디바이스 드라이버를 만듭니다. EXETYPE 키워드는 더 이상 모듈 정의 파일에 유효하지 않습니다.
- `/FUNCTIONPADMIN`(핫 패치 가능 이미지 만들기) 링커 옵션이 추가되었습니다.
- `/LTCG` 링커 옵션이 `/clr`을 사용하여 컴파일된 모듈에서 지원됩니다. `/LTCG`는 프로필 기반 최적화를 지원하도록 업데이트되었습니다.
- `/MANIFEST`(동시에 어셈블리 매니페스트 만들기) 링커 옵션이 추가되었습니다.
- `/MANIFESTDEPENDENCY`(매니페스트 종속성 지정) 링커 옵션이 추가되었습니다.
- `/MANIFESTFILE`(매니페스트 파일 이름 지정) 링커 옵션이 추가되었습니다.
- `/MAPINFO:LINES` 링커 옵션이 제거되었습니다.
- `/NXCOMPAT`(데이터 실행 방지와 호환) 링커 옵션이 추가되었습니다.
- `/PGD`(프로필 기반 최적화를 위한 데이터베이스 지정) 링커 옵션이 추가되었습니다.
- `/PROFILE`(성능 도구 프로파일러) 링커 옵션이 추가되었습니다.
- `/SECTION`(섹션 특성 지정) 링커 옵션이 특성 부정을 지원하며, 더 이상 L 또는 D(VxD 관련) 특성을 지원하지 않습니다.
- 컴파일러 및 링커에서의 유니코드 지원
- `/VERBOSE`(출력 진행 메시지) 링커 옵션은 이제 ICF 및 REF도 허용합니다.
- `/VXD` 링커 옵션이 제거되었습니다. 링커는 더 이상 Windows 95 및 Windows 98 디바이스 드라이버를 만들도록 지원하지 않습니다. 적절한 DDK를 사용하여 이러한 디바이스 드라이버를 만듭니다. VXD 키워드는 더 이상 모듈 정의 파일에 유효하지 않습니다.
- `/WS` 링커 옵션이 제거되었습니다. `/WS`는 Windows NT 4.0에 대한 대상 이미지를 수정하는 데 사용되었습니다. IMAGECFG.exe -R filename을 `/WS` 대신 사용할 수 있습니다. IMAGECFG.exe는 Windows NT 4.0 CD-ROM의 SUPPORT\DEBUG\I386\IMAGECFG.EXE에 있습니다.
- `/WX`(링커 경고를 오류로 처리) 링커 옵션이 문서화되었습니다.

### <a name="new-linker-utility-features"></a>새 링커 유틸리티 기능

- `/ALLOWISOLATION` editbin 옵션이 추가되었습니다.
- DESCRIPTION 모듈 정의 파일 문이 제거되었습니다. 링커는 더 이상 가상 디바이스 드라이버를 작성하도록 지원하지 않습니다.
- `/ERRORREPORT` 옵션이 bscmake.exe, dumpbin.exe, editbin.exe 및 lib.exe에 추가되었습니다.
- `/LTCG` lib 옵션이 추가되었습니다.
- `/NXCOMPAT` editbin 옵션이 추가되었습니다.
- `/RANGE` dumpbin 옵션이 추가되었습니다.
- `/TLS` dumpbin 옵션이 추가되었습니다.
- `/WS` editbin 옵션이 제거되었습니다. `/WS`는 Windows NT 4.0에 대한 대상 이미지를 수정하는 데 사용되었습니다. IMAGECFG.exe -R filename을 `/WS` 대신 사용할 수 있습니다. IMAGECFG.exe는 Windows NT 4.0 CD-ROM의 SUPPORT\DEBUG\I386\IMAGECFG.EXE에 있습니다.
- /WX[:NO] lib 옵션이 추가되었습니다.

### <a name="new-nmake-features"></a>새 NMAKE 기능

- `/ERRORREPORT`가 추가되었습니다.
- `/G`가 추가되었습니다.
- 미리 정의된 규칙이 업데이트되었습니다.
- 재귀 매크로에 문서화된 $(MAKE) 매크로는 nmake.exe에 대한 전체 경로를 제공합니다.

### <a name="new-masm-features"></a>새 MASM 기능

- MASM 식은 64비트 값입니다. 이전 버전에서 MASM 식은 32비트 값이었습니다.
- __asm int 3 명령은 함수를 네이티브로 컴파일하도록 합니다.
- ALIAS(MASM)가 문서화되었습니다.
- `/ERRORREPORT` ml.exe 및 ml64.exe 옵션이 추가되었습니다.
- .FPO가 문서화되었습니다.
- H2INC.exe는 Visual C++ 2005에서 제공되지 않습니다. H2INC를 계속 사용해야 하는 경우 이전 버전의 Visual C++에서 H2INC.exe를 사용합니다.
- IMAGEREL 연산자가 추가되었습니다.
- HIGH32 연산자가 추가되었습니다.
- LOW32 연산자가 추가되었습니다.
- ml64.exe는 x64 아키텍처용 MASM 버전입니다. x64 .asm 파일을 x64 개체 파일로 어셈블합니다. 인라인 어셈블리 언어는 x64 컴파일러에서 지원되지 않습니다. ml64.exe(x64)에 대해 추가된 MASM 지시문은 다음과 같습니다.
- .ALLOCSTACK
- .ENDPROLOG
- .PUSHFRAME
- .PUSHREG
- .SAVEREG
- .SAVEXMM128
- .SETFRAME. 또한 PROC 지시문은 x64 전용 구문으로 업데이트되었습니다.
- MMWORD 지시문이 추가되었습니다.
- `/omf`(ML.exe 명령줄 옵션)는 `/c`를 의미합니다. ML.exe는 OMF 형식 개체 연결을 지원하지 않습니다.
- SEGMENT 지시문이 추가 특성을 지원합니다.
- SECTIONREL 연산자가 추가되었습니다.
- XMMWORD 지시문이 추가되었습니다.

### <a name="new-crt-features"></a>새 CRT 기능

- 여러 함수의 보안 버전이 추가되었습니다. 이러한 함수는 오류를 더 효율적인 방식으로 처리하고, 버퍼에 더 강력한 제어를 적용하여 일반적인 보안 결함을 방지합니다. 새로운 보안 버전은 **_s** 접미사로 식별됩니다.
- 기존의 보안 수준이 낮은 버전의 많은 함수가 더 이상 사용되지 않습니다. 사용 중단 경고를 사용하지 않으려면 _CRT_SECURE_NO_WARNINGS를 정의합니다.
- 기존의 많은 함수에서 매개 변수의 유효성을 검사하고, 잘못된 매개 변수가 전달되면 잘못된 매개 변수 처리기를 호출합니다.
- 기존의 많은 함수에서 이전에 설정하지 않았던 `errno`를 설정합니다.
- 정수 형식의 typedef `errno_t`가 추가되었습니다. `errno_t`가 함수 반환 형식 또는 매개 변수에서 `errno`의 오류 코드를 처리할 때마다 사용됩니다. `errno_t`는 `errcode`을 대신합니다.
- 로캘 종속 함수에는 현재 로캘을 사용하는 대신 로캘을 매개 변수로 사용하는 버전이 있습니다. 이러한 새 함수에는 **_l** 접미사가 있습니다. 로캘 개체를 사용하기 위해 몇 가지 새로운 함수가 추가되었습니다. 새 함수에는 `_get_current_locale`, `_create_locale` 및 `_free_locale`가 있습니다.
- 파일 핸들 잠금 및 잠금 해제를 지원하는 새 함수가 추가되었습니다.
- 함수의 `_spawn` 제품군은 이전 버전과 같이 성공 시 errno를 0으로 다시 설정하지 않습니다.
- 인수가 사용되는 순서를 지정할 수 있는 `printf` 계열의 함수 버전을 사용할 수 있습니다.
- 유니코드 텍스트 형식이 지원됩니다. `_open` 함수는 _O_TEXTW, _O_UTF8 및 _O_UTF16 특성을 지원합니다. `fopen` 함수는 유니코드 형식을 지정하는 "ccs=ENCODING" 메서드를 지원합니다.
- 관리 코드(MSIL)로 빌드된 CRT 라이브러리의 새 버전을 사용할 수 있으며, `/clr`(공용 언어 런타임 컴파일) 옵션을 사용하여 컴파일할 때 사용됩니다.
- _fileinfo가 제거되었습니다.
- `time_t`의 기본 크기는 64비트입니다. 이에 따라 `time_t` 및 몇 가지 시간 함수의 범위가 3000년까지 확장됩니다.
- CRT는 스레드 단위의 로캘 설정을 지원합니다. 이 기능을 지원하기 위해 `_configthreadlocale` 함수가 추가되었습니다.
- x87 및 SSE2 부동 소수점 프로세서 모두에서 부동 소수점 제어 단어를 액세스하고 제어할 수 있도록 `_statusfp2` 및 `__control87_2` 함수가 추가되었습니다.
- 시간(struct tm)을 GMT(그리니치 표준시)로 변환하는 기능을 지원하기 위해 `_mkgmtime` 및 `_mkgmtime64` 함수가 추가되었습니다.
- `swprintf` 및 `vswprintf`가 표준을 더 잘 준수하도록 변경되었습니다.
- 새로운 INTRIN.H 헤더 파일에서 일부 내장 함수에 대한 프로토타입을 제공합니다.
- `fopen` 함수에는 N 특성이 있습니다.
- `_open` 함수에 _O_NOINHERIT 특성이 있습니다.
- `atoi` 함수는 INT_MAX를 반환하고, 오버플로가 발생하면 `errno`를 ERANGE로 설정합니다. 이전 버전에서는 오버플로 동작이 정의되지 않았습니다.
- `printf` 계열의 함수는 %a 및 %A 형식 지정자를 사용하여 ANSI C99 표준에 따라 구현된 16진수 부동 소수점 출력을 지원합니다.
- `printf` 계열은 "ll"(long long) 크기 접두사를 지원합니다.
- `_controlfp` 함수가 더 나은 성능을 위해 최적화되었습니다.
- 일부 함수의 디버그 버전이 추가되었습니다.
- `_chgsignl` 및 `_cpysignl`(long double 버전)이 추가되었습니다.
- `_locale_t` 형식이 형식 테이블에 추가되었습니다.
- 새 `_countof` Macro 매크로가 배열의 요소 수를 계산하기 위해 추가되었습니다.
- 각 함수 항목에서 .NET Framework에 해당하는 섹션이 추가되었습니다.
- 몇 가지 문자열 함수에는 출력 버퍼가 너무 작을 때 실패하지 않고 문자열을 자르는 옵션이 있습니다. **_TRUNCATE**를 참조하세요.
- `_set_se_translator`에서는 이제 `/EHa` 컴파일러 옵션을 사용해야 합니다.
- `fpos_t` 는 현재 **`__int64`** `/Za` (c 코드의 경우)이 고 __STDC__ 가 수동으로 설정 된 경우 (c + + 코드의 경우) 로 사용 됩니다 **`struct`** .
- _CRT_DISABLE_PERFCRIT_LOCKS는 단일 스레드 프로그램의 I/O 성능을 향상시킬 수 있습니다.
- POSIX 이름은 ISO C++ 호환 이름을 따르므로 더 이상 사용되지 않습니다(예: `getch` 대신 `_getch` 사용).
- 새 링크 옵션인 .obj 파일은 pure 모드에서 사용할 수 있습니다.
- `_recalloc`은 `realloc` 및 `calloc` 기능을 결합합니다.

## <a name="whats-new-for-c-in-visual-studio-2003"></a>Visual Studio 2003의 새로운 C++ 기능

### <a name="compiler"></a>컴파일러

- 이전 버전의 런타임에서 현재 버전의 컴파일러를 사용하여 빌드된 Managed Extensions for C++ 애플리케이션을 실행하는 방법에 대한 정보.
- Managed Extensions for C++에 대한 FAQ(질문과 대답)
- Managed Extensions for C++를 사용하도록 기존 네이티브 애플리케이션을 이식하는 방법을 보여 주는 연습(연습: .NET Framework 구성 요소와 상호 운용하도록 기존 네이티브 C++ 애플리케이션 이식)이 추가되었습니다.
- 값 형식의 메서드에 대리자를 만들 수 있습니다.
- Visual C++ .NET 2003에 대한 컴파일러의 C++ 표준 준수가 크게 향상되었습니다.
- `/arch` 컴파일러 옵션이 추가되었습니다.
- `/Gf`는 더 이상 사용되지 않으며, 다음 버전의 Visual C++에서 제거됩니다.
- `/G7` 컴파일러 옵션이 추가되었습니다.
- `/GS` 컴파일러 옵션이 직접 버퍼 오버런으로부터 로컬 변수를 보호하도록 향상되었습니다.
- `/noBool` 컴파일러 옵션이 제거되었습니다. 이제 컴파일러는 **`bool`** c + + 소스 코드 파일에서 식별자가 아닌 키워드로만 표시 되도록 허용 합니다.
- **`long long`** 이제 형식을 **`typedef`** **`__int64`** CRT에서 아직 지원 하지 않는의로 사용할 수 있습니다 **`long long`** .
- `/Zm` 컴파일러 옵션은 미리 컴파일된 헤더 메모리의 할당 제한을 지정합니다.
- _InterlockedCompareExchange 내장 함수가 문서화되었습니다.
- _InterlockedDecrement 내장 함수가 문서화되었습니다.
- _InterlockedExchange 내장 함수가 문서화되었습니다.
- _InterlockedExchangeAdd 내장 함수가 문서화되었습니다.
- _InterlockedIncrement 내장 함수가 문서화되었습니다.
- _ReadWriteBarrier 내장 함수가 추가되었습니다.

### <a name="attributes"></a>특성

- `implements` 특성이 문서화되었습니다.

### <a name="linker-features"></a>링커 기능

추가된 링커 스위치는 다음과 같습니다.

- /ASSEMBLYDEBUG
- /ASSEMBLYLINKRESOURCE
- DELAYSIGN
- /KEYFILE
- /KEYCONTAINER
- /SAFESEH

### <a name="masm"></a>MASM

.SAFESEH 지시문 및 `/safeseh` ml.exe 옵션이 추가되었습니다.

## <a name="see-also"></a>참고 항목

[Visual C++ 포팅 및 업그레이드 가이드](visual-cpp-porting-and-upgrading-guide.md)
