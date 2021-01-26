---
title: /permissive-(표준 준수)
description: Microsoft c + +/permissive-(표준 준수) 컴파일러 옵션에 대 한 참조 가이드입니다.
ms.date: 10/28/2020
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: c8d654540deb492a5bebff304ef01ca4c71f044a
ms.sourcegitcommit: 74e58bee5cffb30b66e17be6dbfde2544369638e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/25/2021
ms.locfileid: "98763817"
---
# <a name="permissive--standards-conformance"></a>/permissive-(표준 준수)

컴파일러에 대 한 표준 규칙 모드를 지정 합니다. 이 옵션을 사용 하면 코드에서 규칙 문제를 식별 하 고 수정 하 여 보다 정확 하 고 이식 가능 하 게 만들 수 있습니다.

## <a name="syntax"></a>구문

> **`/permissive-`**\
> **`/permissive`**

## <a name="remarks"></a>설명

**`/permissive-`** 이 옵션은 Visual Studio 2017 이상에서 지원 됩니다. **`/permissive`** 는 Visual Studio 2019 버전 16.8 이상에서 지원 됩니다.

**`/permissive-`** 컴파일러 옵션을 사용 하 여 표준을 준수 하는 컴파일러 동작을 지정할 수 있습니다. 이 옵션은 관대 한 동작을 사용 하지 않도록 설정 하 고 [`/Zc`](zc-conformance.md) 엄격한 규칙에 대 한 컴파일러 옵션을 설정 합니다. IDE에서이 옵션을 사용 하면 IntelliSense 엔진에서 순응 하지 않는 코드에 밑줄이 표시 됩니다.

**`/permissive-`** 이 옵션은 현재 컴파일러 버전의 규칙 지원 기능을 사용 하 여 일치 하지 않는 언어 구문을 확인 합니다. 옵션은 코드가 특정 버전의 c + + 표준에 맞는지 확인 하지 않습니다. 최신 초안 표준에 대해 구현 된 모든 컴파일러 지원을 사용 하도록 설정 하려면 [`/std:c++latest`](std-specify-language-standard-version.md) 옵션을 사용 합니다. 현재 구현 된 c + + 17 표준에 대 한 컴파일러 지원을 제한 하려면 [`/std:c++17`](std-specify-language-standard-version.md) 옵션을 사용 합니다. 컴파일러 지원이 c + + 14 표준에 더 가깝게 일치 하도록 제한 하려면 [`/std:c++14`](std-specify-language-standard-version.md) 기본값 인 옵션을 사용 합니다.

Visual Studio 2019 버전 16.8부터 **`/std:c++latest`** 옵션은 옵션을 암시적으로 설정 합니다 **`/permissive-`** . C + + 20 모듈 지원에 필요 합니다. 코드에 모듈 지원이 필요 하지는 않지만에서 사용 하도록 설정 된 다른 기능이 필요 **`/std:c++latest`** 합니다. 후행 대시가 없는 옵션을 사용 하 여 Microsoft 확장 지원을 명시적으로 사용 하도록 설정할 수 있습니다 **`/permissive`** .

기본적으로 **`/permissive-`** 이 옵션은 Visual Studio 2017 버전 15.5 이상 버전에서 만든 새 프로젝트에 설정 되어 있습니다. 이전 버전에서는 기본적으로 설정 되어 있지 않습니다. 옵션이 설정 되 면 코드에서 비표준 언어 구문이 검색 될 때 컴파일러에서 진단 오류 또는 경고를 생성 합니다. 이러한 구문에는 C + + 11 이전 코드의 몇 가지 일반적인 버그가 포함 됩니다.

**`/permissive-`** 이 옵션은 windows에서 10.0.16299.0 (소프트웨어 개발 키트) 또는 WDK (Windows 드라이버 키트)와 같은 최신 Windows 키트의 거의 모든 헤더 파일과 호환 됩니다. 이전 버전의 SDK는 **`/permissive-`** 다양 한 소스 코드 규칙의 이유로에서 컴파일되지 않을 수 있습니다. 컴파일러와 Sdk는 서로 다른 릴리스 타임 라인에서 제공 되므로 몇 가지 문제가 남아 있습니다. 특정 헤더 파일 문제에 대 한 자세한 내용은 아래의 [Windows 헤더 문제](#windows-header-issues) 를 참조 하세요.

**`/permissive-`** 옵션은 [`/Zc:referenceBinding`](zc-referencebinding-enforce-reference-binding-rules.md) , [`/Zc:strictStrings`](zc-strictstrings-disable-string-literal-type-conversion.md) 및 옵션을 [`/Zc:rvalueCast`](zc-rvaluecast-enforce-type-conversion-rules.md) 준수 하는 동작으로 설정 합니다. 이러한 옵션은 기본적으로 순응 하지 않는 동작으로 설정 됩니다. **`/Zc`** 명령줄에서 특정 옵션을 전달 **`/permissive-`** 하 여이 동작을 재정의할 수 있습니다.

Visual Studio 2017 버전 15.3에서 시작 하는 컴파일러 버전에서는 옵션을 **`/permissive-`** 설정 합니다 [`/Zc:ternary`](zc-ternary.md) . 또한 컴파일러는 2 단계 이름 조회에 대 한 요구 사항을 추가로 구현 합니다. **`/permissive-`** 옵션이 설정 되 면 컴파일러는 함수와 클래스 템플릿 정의를 구문 분석 하 고 템플릿에 사용 되는 종속 및 종속 되지 않은 이름을 식별 합니다. 이 릴리스에서는 이름 종속성 분석만 수행 됩니다.

표준에서 구현까지 유지 하는 환경 관련 확장 및 언어 영역은의 영향을 받지 않습니다 **`/permissive-`** . 예를 들어 Microsoft 전용 **`__declspec`** 호출 규칙 및 구조적 예외 처리 키워드, 컴파일러 관련 pragma 지시문 또는 특성은 컴파일러가 모드에서 플래그 지정 되지 않습니다 **`/permissive-`** .

모든 버전의 Visual Studio 2017에서 MSVC 컴파일러가 c + + 11, c + + 14 또는 c + + 17 표준을 준수 하는 코드를 지원 하지는 않습니다. Visual Studio의 버전에 따라 **`/permissive-`** 옵션은 2 단계 이름 조회의 일부 측면에서 문제를 검색 하지 못할 수 있습니다. 즉, 임시에 대 한 비 const 참조를 바인딩 하거나, 복사 init를 직접 init로 처리 하거나, 초기화에서 여러 사용자 정의 변환을 허용 하거나, 논리 연산자에 대 한 대체 토큰 및 기타 지원 되지 않는 규칙 영역을 지원 합니다. Visual C++의 규칙과 관련된 문제에 대한 자세한 내용은 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)을 참조하세요. 을 최대한 활용 하려면 **`/permissive-`** Visual Studio를 최신 버전으로 업데이트 하세요.

### <a name="how-to-fix-your-code"></a>코드를 수정 하는 방법

다음은를 사용 하는 경우 호환 되지 않는 것으로 검색 되는 코드의 몇 가지 예로 **`/permissive-`** ,이 문제를 해결 하는 제안 된 방법이 있습니다.

#### <a name="use-default-as-an-identifier-in-native-code"></a>네이티브 코드에서 식별자로 기본값 사용

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>종속 된 기본에서 멤버 조회

```cpp
template <typename T>
struct B {
    void f();
};

template <typename T>
struct D : public B<T> // B is a dependent base because its type
                       // depends on the type of T.
{
    // One possible fix is to uncomment the following line.
    // If this is a type, don't forget the 'typename' keyword.
    // using B<T>::f;

    void g() {
        f(); // error C3861: 'f': identifier not found
             // Another fix is to change it to 'this->f();'
    }
};

void h() {
    D<int> d;
    d.g();
}
```

#### <a name="use-of-qualified-names-in-member-declarations"></a>멤버 선언에 정규화 된 이름 사용

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>멤버 이니셜라이저에서 여러 공용 구조체 멤버를 초기화 합니다.

```cpp
union U
{
    U()
        : i(1), j(1) // error C3442: Initializing multiple members of
                     // union: 'U::i' and 'U::j'.
                     // Remove all but one of the initializations to fix.
    {}
    int i;
    int j;
};
```

#### <a name="hidden-friend-name-lookup-rules"></a>숨겨진 friend 이름 조회 규칙

```cpp
// Example 1
struct S {
    friend void f(S *);
};
// Uncomment this declaration to make the hidden friend visible:
// void f(S *); // This declaration makes the hidden friend visible

using type = void (*)(S *);
type p = &f; // error C2065: 'f': undeclared identifier.
```

```cpp
// Example 2
struct S {
    friend void f(S *);
};
void g() {
    // Using nullptr instead of S prevents argument dependent lookup in S
    f(nullptr); // error C3861: 'f': identifier not found

    S *p = nullptr;
    f(p); // Hidden friend now found via argument-dependent lookup.
}
```

를 사용 하 여와 별개로 숨겨진 friend 이름 조회 규칙을 사용 하도록 설정할 수 있습니다 **`/permissive`** [`/Zc:hiddenFriend`](./zc-hiddenfriend.md) . 숨겨진 friend 이름 조회에 대 한 레거시 동작을 원하지만 **`/permissive-`** 동작을 원하는 경우 옵션을 사용 **`/Zc:hiddenFriend-`** 합니다.

#### <a name="use-scoped-enums-in-array-bounds"></a>배열 범위에서 범위가 지정 된 열거형 사용

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>네이티브 코드에서 각에 대해 사용

```cpp
void func() {
    int array[] = {1, 2, 30, 40};
    for each (int i in array) // error C4496: nonstandard extension
                              // 'for each' used: replace with
                              // ranged-for statement:
                              // for (int i: array)
    {
        // ...
    }
}
```

#### <a name="use-of-atl-attributes"></a>ATL 특성 사용

```cpp
// Example 1
[uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
class A {};
```

```cpp
// Fix for example 1
class __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) B {};
```

```cpp
// Example 2
[emitidl];
[module(name="Foo")];

[object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
__interface ICustom {
    HRESULT Custom([in] longl, [out, retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out, retval] long*pLong);
};

[coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
class CFoo : public ICustom
{};
```

```cpp
// Fix for example 2
// First, create the *.idl file. The vc140.idl generated file can be
// used to automatically obtain a *.idl file for the interfaces with
// annotation. Second, add a midl step to your build system to make
// sure that the C++ interface definitions are outputted.
// Last, adjust your existing code to use ATL directly as shown in
// the atl implementation section.

-- IDL  FILE--
import "docobj.idl";

[object, local, uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)]
interface ICustom : IUnknown {
    HRESULT Custom([in] longl, [out,retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out,retval] long*pLong);
};

[ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
library Foo {
    importlib("stdole2.tlb");
    importlib("olepro32.dll");

    [version(1.0), appobject, uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)]
    coclass CFoo { interface ICustom; };
}

-- ATL IMPLEMENTATION--
#include <idl.header.h>
#include <atlbase.h>

class ATL_NO_VTABLE CFooImpl : public ICustom,
    public ATL::CComObjectRootEx<CComMultiThreadModel>
{
    public:BEGIN_COM_MAP(CFooImpl)
    COM_INTERFACE_ENTRY(ICustom)
    END_COM_MAP()
};
```

#### <a name="ambiguous-conditional-operator-arguments"></a>모호한 조건부 연산자 인수

Visual Studio 2017 이전 15.3 버전의 컴파일러에서는 컴파일러가 `?:` 표준에서 모호한 것으로 간주 되는 조건 연산자 (또는 삼항 연산자)에 대 한 인수를 수락 했습니다. **`/permissive-`** 모드에서 이제 컴파일러는 이전 버전에서 진단 하지 않고 컴파일한 경우 하나 이상의 진단을 실행 합니다.

이러한 변경으로 인해 발생할 수 있는 일반적인 오류는 다음과 같습니다.

- `error C2593: 'operator ?' is ambiguous`

- `error C2679: binary '?': no operator found which takes a right-hand operand of type 'B' (or there is no acceptable conversion)`

- `error C2678: binary '?': no operator found which takes a left-hand operand of type 'A' (or there is no acceptable conversion)`

- `error C2446: ':': no conversion from 'B' to 'A'`

이 문제를 발생 시킬 수 있는 일반적인 코드 패턴은 일부 클래스 C에서 다른 형식 T의 비 명시적 생성자와 명시적 변환 연산자를 둘 다 제공 하는 경우를 T 형식으로 제공 하는 경우입니다. 이 경우 두 번째 인수를 세 번째 인수의 형식으로 변환 하 고 세 번째 인수를 두 번째 인수의 형식으로 변환 하는 것은 유효한 변환입니다. 둘 다 유효 하므로 표준에 따라 모호 합니다.

```cpp
// Example 1: class that provides conversion to and initialization from some type T
struct A
{
    A(int);
    operator int() const;
};

extern bool cond;

A a(42);
// Accepted when /Zc:ternary or /permissive- is not used:
auto x = cond ? 7 : a; // A: permissive behavior prefers A(7) over (int)a
// Accepted always:
auto y = cond ? 7 : int(a);
auto z = cond ? A(7) : a;
```

T가 null로 종료 되는 문자열 형식 (예:, 등) 중 하나를 나타내고의 `const char *` `const char16_t *` 실제 인수가 `?:` 해당 형식의 문자열 리터럴인 경우이 일반적인 패턴에 대 한 중요 한 예외가 있습니다. C + + 17에는 c + + 14의 의미 체계가 변경 되었습니다. 따라서 **`/std:c++14`** **`/std:c++17`** **`/Zc:ternary`** 또는 **`/permissive-`** 가 사용 될 때 예 2의 코드는에서 허용 되 고 거부 됩니다.

```cpp
// Example 2: exception from the above
struct MyString
{
    MyString(const char* s = "") noexcept;  // from char*
    operator const char* () const noexcept; //   to char*
};

extern bool cond;

MyString s;
// Using /std:c++14, /permissive- or /Zc:ternary behavior
// is to prefer MyString("A") over (const char*)s
// but under /std:c++17 this line causes error C2445:
auto x = cond ? "A" : s;
// You can use a static_cast to resolve the ambiguity:
auto y = cond ? "A" : static_cast<const char*>(s);
```

오류가 표시 될 수 있는 또 다른 경우는 형식의 인수 하나를 사용 하는 조건부 연산자입니다 **`void`** . 이 경우는 ASSERT와 같은 매크로에서 일반적 일 수 있습니다.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

또한 템플릿 메타 프로그래밍에서 오류가 표시 될 수 있습니다. 여기서 조건 연산자 결과 형식은 및에서 변경 될 수 있습니다 **`/Zc:ternary`** **`/permissive-`** . 이 문제를 해결 하는 한 가지 방법은 결과 형식에서를 사용 하는 것입니다 [`std::remove_reference`](../../standard-library/remove-reference-class.md) .

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>2 단계 이름 조회

**`/permissive-`** 옵션이 설정 되 면 컴파일러는 함수 및 클래스 템플릿 정의를 구문 분석 하 여 2 단계 이름 조회에 필요에 따라 템플릿에 사용 되는 종속 및 종속 되지 않은 이름을 식별 합니다. Visual Studio 2017 버전 15.3에서 이름 종속성 분석이 수행 됩니다. 특히 템플릿 정의의 컨텍스트에서 선언 되지 않은 종속 되지 않은 이름은 ISO c + + 표준에 필요한 진단 메시지를 발생 시킵니다. Visual Studio 2017 버전 15.7에서는 정의 컨텍스트에서 인수 종속 조회를 필요로 하는 종속 되지 않은 이름의 바인딩만 수행 됩니다.

```cpp
// dependent base
struct B {
    void g() {}
};

template<typename T>
struct D : T {
    void f() {
        // The call to g was incorrectly allowed in VS2017:
        g();  // Now under /permissive-: C3861
        // Possible fixes:
        // this->g();
        // T::g();
    }
};

int main()
{
    D<B> d;
    d.f();
}
```

2 단계 조회에 대 한 레거시 동작을 원하는 경우 동작을 원하지 않을 경우 **`/permissive-`** 옵션을 추가 **`/Zc:twoPhase-`** 합니다.

### <a name="windows-header-issues"></a>Windows 헤더 문제

**`/permissive-`** 이 옵션은 windows에서 10.0.16299.0 (Windows 드라이버 키트) 버전 1709 이전 버전의 Windows 키트에 비해 너무 엄격 합니다. **`/permissive-`** Windows 또는 장치 드라이버 코드에서 사용할 최신 버전의 Windows 키트로 업데이트 하는 것이 좋습니다.

Windows 4 월 2018 업데이트 SDK (10.0.17134.0)에 있는 특정 헤더 파일, Windows에 대 한 10.0.16299.0 (windows의 작성자 업데이트 SDK) 또는 WDK (Windows 드라이버 키트) 1709에는를 사용 하는 것과 호환 되지 않는 문제가 있습니다 **`/permissive-`** . 이러한 문제를 해결 하려면 이러한 헤더를 필요로 하는 소스 코드 파일로만 사용 하는 것을 제한 하 고 **`/permissive-`** 특정 소스 코드 파일을 컴파일할 때 옵션을 제거 하는 것이 좋습니다.

Windows 4 월 2018 업데이트 SDK (10.0.17134.0)에서 릴리스된 이러한 WinRT WRL 헤더는 정리 되지 않습니다 **`/permissive-`** . 이러한 문제를 해결 하려면를 사용 하지 않거나 **`/permissive-`** **`/permissive-`** **`/Zc:twoPhase-`** 다음 헤더를 사용할 때를 사용 합니다.

- Winrt/wrl/async의 문제

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Winrt/wrl/구현에 문제가 있습니다.

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Windows 4 월 2018 업데이트 SDK (10.0.17134.0)에서 릴리스된 이러한 사용자 모드 헤더는 정리 되지 않습니다 **`/permissive-`** . 이러한 문제를 해결 하려면 **`/permissive-`** 이러한 헤더로 작업할 때를 사용 하지 마세요.

- Um/튠의 문제

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Um/spddkhlp에 문제가 있습니다.

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Um/refptrco의 문제

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

이러한 문제는 Windows가 10.0.16299.0 (Windows가 나 크리에이터 업데이트 SDK)의 사용자 모드 헤더에만 해당 됩니다.

- Um/Query .h의 문제

   **`/permissive-`** 컴파일러 스위치를 사용 하는 경우 `tagRESTRICTION` 구조체는 Case (rtor) 멤버 ' or '로 인해 컴파일되지 않습니다.

   ```cpp
   struct tagRESTRICTION
   {
       ULONG rt;
       ULONG weight;
       /* [switch_is][switch_type] */ union _URes
       {
           /* [case()] */ NODERESTRICTION ar;
           /* [case()] */ NODERESTRICTION or;  // error C2059: syntax error: '||'
           /* [case()] */ NODERESTRICTION pxr;
           /* [case()] */ VECTORRESTRICTION vr;
           /* [case()] */ NOTRESTRICTION nr;
           /* [case()] */ CONTENTRESTRICTION cr;
           /* [case()] */ NATLANGUAGERESTRICTION nlr;
           /* [case()] */ PROPERTYRESTRICTION pr;
           /* [default] */  /* Empty union arm */
       } res;
   };
   ```

   이 문제를 해결 하려면 옵션 없이 resource.h를 포함 하는 파일을 컴파일합니다. **`/permissive-`**

- Um/cellularapi_oem에 문제가 있습니다.

   컴파일러 스위치를 사용 하는 경우 **`/permissive-`**  의 전방 선언으로 `enum UICCDATASTOREACCESSMODE` 인해 경고가 발생 합니다.

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   범위가 없는 열거형의 전방 선언은 Microsoft 확장입니다. 이 문제를 해결 하려면 옵션 없이 cellularapi_oem를 포함 하는 파일을 컴파일하거나, 옵션을 사용 하 여 **`/permissive-`** [`/wd`](compiler-option-warning-level.md) 경고 C4471 합니다.

- Um/omscript .h의 문제

   C + + 03에서 문자열 리터럴을 BSTR (' wchar_t * '로의 typedef)로 변환 하는 것은 더 이상 사용 되지 않지만 허용 됩니다. C + + 11에서는 변환이 더 이상 허용 되지 않습니다.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   이 문제를 해결 하려면 옵션 없이 omscript. h를 포함 하는 파일을 컴파일하거나 **`/permissive-`** 대신을 사용 **`/Zc:strictStrings-`** 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

Visual Studio 2017 버전 15.5 이상 버전에서 다음 절차를 따르십시오.

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다.

1. **구성 속성**  >  **C/c + +**  >  **언어** 속성 페이지를 선택 합니다.

1. **규칙 모드** 속성 값을 **예 (/permissive-)** 로 변경 합니다. **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

Visual Studio 2017 버전 15.5 이전 버전에서 다음 절차를 사용 합니다.

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에 **/permissive-** 컴파일러 옵션을 입력 합니다. **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)\
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
