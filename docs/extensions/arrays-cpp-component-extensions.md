---
title: 배열(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- cli::array
- details::array
- lang::array
helpviewer_keywords:
- array keyword [C++]
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
ms.openlocfilehash: 814be57caafed117a1403105d46326ac53682578
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500886"
---
# <a name="arrays-ccli-and-ccx"></a>배열(C++/CLI 및 C++/CX)

C++/CX의 `Platform::Array<T>` 형식이나 C++/CLI의 **array** 키워드는 지정된 형식과 초기 값의 배열을 선언합니다.

## <a name="all-platforms"></a>모든 플랫폼

선언에서 닫는 꺾쇠 괄호(>) 다음에 개체 핸들(^) 한정자를 사용하여 배열을 선언해야 합니다.
배열의 요소 수는 형식에 포함되지 않습니다. 하나의 배열 변수가 다양한 크기의 배열을 참조할 수 있습니다.

표준 C++와 달리, 첨자는 포인터 산술 연산의 동의어가 아니며 누적되지 않습니다.

배열에 대한 자세한 내용은 다음을 참조하세요.

- [방법: c + +/CLI에서 배열 사용](../dotnet/how-to-use-arrays-in-cpp-cli.md)

- [가변 인수 목록 (...) (C + +/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)

## <a name="windows-runtime"></a>Windows 런타임

배열은 `Platform` 네임스페이스의 멤버입니다. 1차원 배열만 사용할 수 있습니다.

### <a name="syntax"></a>구문

첫 번째 구문 예제에서는 **ref new** 집계 키워드를 사용하여 배열을 할당합니다. 두 번째 예제에는 로컬 배열을 선언합니다.

```cpp
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]

[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*한정자*<br/>
(선택 사항) [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/extern-cpp.md), [static](../cpp/static-members-cpp.md) 스토리지 클래스 지정자 중 하나 이상입니다.

*배열 형식*<br/>
배열 변수의 형식입니다. 유효한 형식은 Windows 런타임 클래스 및 기본 형식, ref 클래스 및 구조체, 값 클래스 및 구조체, 네이티브 포인터(`type*`)입니다.

*배열*<br/>
(선택 사항) 배열의 차원 수입니다. 1이어야 합니다.

*identifier*<br/>
배열 변수의 이름입니다.

*initialization-type*<br/>
배열을 초기화하는 값의 형식입니다. 일반적으로 *array-type*과 *initialization-type*은 동일한 형식입니다. 그러나 *initialization-type*에서 *array-type*으로의 변환이 있는 경우(예: *initialization-type*이 *array-type*에서 파생된 경우), 형식이 서로 다를 수 있습니다.

*initialization-list*<br/>
(선택 사항) 배열의 요소를 초기화하는, 중괄호 안의 쉼표로 구분된 값 목록입니다. 예를 들어 *rank-size-list*가 3개의 요소로 이루어진 1차원 배열을 선언하는 `(3)`이면 *initialization list*는 `{1,2,3}`일 수 있습니다.

### <a name="remarks"></a>설명

컴파일 시간에 `__is_ref_array(type)`을 사용하여 형식이 참조 횟수가 계산되는 배열인지 여부를 검색할 수 있습니다. 자세한 내용은 [형식 특성에 대한 컴파일러 지원](compiler-support-for-type-traits-cpp-component-extensions.md)을 참조하세요.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

### <a name="examples"></a>예

다음 예제에서는 100개의 요소로 이루어진 1차원 배열을 만듭니다.

```cpp
// cwr_array.cpp
// compile with: /ZW
using namespace Platform;
ref class MyClass {};
int main() {
   // one-dimensional array
   Array<MyClass^>^ My1DArray = ref new Array<MyClass^>(100);
   My1DArray[99] = ref new MyClass();
}
```

## <a name="common-language-runtime"></a>공용 언어 런타임

### <a name="syntax"></a>구문

첫 번째 구문 예제에서는 **gcnew** 키워드를 사용하여 배열을 할당합니다. 두 번째 예제에는 로컬 배열을 선언합니다.

```cpp
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]

[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*한정자*<br/>
(선택 사항) [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/extern-cpp.md), [static](../cpp/static-members-cpp.md) 스토리지 클래스 지정자 중 하나 이상입니다.

*배열 형식*<br/>
배열 변수의 형식입니다. 유효한 형식은 Windows 런타임 클래스 및 기본 형식, ref 클래스 및 구조체, 값 클래스 및 구조체, 네이티브 포인터(`type*`), 네이티브 POD(Plain Old Data) 형식입니다.

*배열*<br/>
(선택 사항) 배열의 차원 수입니다. 기본값은 1이고, 최댓값은 32입니다. 배열의 각 차원 자체도 배열입니다.

*identifier*<br/>
배열 변수의 이름입니다.

*initialization-type*<br/>
배열을 초기화하는 값의 형식입니다. 일반적으로 *array-type*과 *initialization-type*은 동일한 형식입니다. 그러나 *initialization-type*에서 *array-type*으로의 변환이 있는 경우(예: *initialization-type*이 *array-type*에서 파생된 경우), 형식이 서로 다를 수 있습니다.

*rank-size-list*<br/>
배열에 포함된 각 차원 크기의 쉼표로 구분된 목록입니다. 또는 *initialization-list* 매개 변수를 지정한 경우 컴파일러에서 각 차원의 크기를 추론할 수 있으며, *rank-size-list*를 생략할 수 있습니다.

*initialization-list*<br/>
(선택 사항) 배열의 요소를 초기화하는, 중괄호 안의 쉼표로 구분된 값 목록입니다. 또는 다차원 배열의 요소를 초기화하는 중첩된 *initialization-list* 항목의 쉼표로 구분된 목록입니다.

예를 들어 *rank-size-list*가 3개의 요소로 이루어진 1차원 배열을 선언하는 `(3)`이면 *initialization list*는 `{1,2,3}`일 수 있습니다. *rank-size-list*가 첫 번째 차원에는 3개 요소, 두 번째 차원에는 2개 요소, 세 번째 차원에는 4개 요소가 포함된 3차원 배열을 선언하는 `(3,2,4)`이면 *initialization-list*는 `{{1,2,3},{0,0},{-5,10,-21,99}}`일 수 있습니다.

### <a name="remarks"></a>설명

**array**는 [Platform, default 및 cli 네임스페이스](platform-default-and-cli-namespaces-cpp-component-extensions.md)에 있습니다.

표준 C++와 마찬가지로, 배열의 인덱스는 0부터 시작하고 대괄호([])를 사용하여 배열의 첨자를 나타냅니다. 표준 C++와 달리, 다차원 배열의 인덱스는 각 차원의 대괄호([]) 연산자 집합이 아닌 각 차원의 인덱스의 목록에 지정됩니다. 예를 들어 *identifier*[*index1*][ *index2*] 대신 *identifier*[*index1*, *index2*]를 사용합니다.

모든 관리형 배열은 `System::Array`에서 상속받습니다. `System::Array`의 모든 메서드 또는 속성을 배열 변수에 직접 적용할 수 있습니다.

요소 형식이-관리형 클래스에 대한 포인터인 배열을 할당하면 요소가 0으로 초기화됩니다.

요소 형식이 값 형식 `V`인 배열을 할당하면 `V`의 기본 생성자가 각 배열 요소에 적용됩니다. 자세한 내용은 [C++ 네이티브 형식에 해당하는 .NET Framework 형식(C++/CLI)](../dotnet/managed-types-cpp-cli.md#dotnet)을 참조하세요.

컴파일 시간에 `__is_ref_array(type)`를 사용하여 형식이 CLR(공용 언어 런타임) 배열인지 여부를 검색할 수 있습니다. 자세한 내용은 [형식 특성에 대한 컴파일러 지원](compiler-support-for-type-traits-cpp-component-extensions.md)을 참조하세요.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예

다음 예제에서는 100개의 요소로 이루어진 1차원 배열과 첫 번째 차원에는 3개 요소, 두 번째 차원에는 5개 요소, 세 번째 차원에는 6개 요소가 있는 3차원 배열을 만듭니다.

```cpp
// clr_array.cpp
// compile with: /clr
ref class MyClass {};
int main() {
   // one-dimensional array
   array<MyClass ^> ^ My1DArray = gcnew array<MyClass ^>(100);
   My1DArray[99] = gcnew MyClass();

   // three-dimensional array
   array<MyClass ^, 3> ^ My3DArray = gcnew array<MyClass ^, 3>(3, 5, 6);
   My3DArray[0,0,0] = gcnew MyClass();
}
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
