---
description: 다음에 대해 자세히 알아보세요. `__declspec`
title: __declspec
ms.date: 03/21/2019
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
helpviewer_keywords:
- __declspec keyword [C++]
ms.openlocfilehash: d0567c522e0e21f70b9ed8acfa428c3374fd09f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339542"
---
# `__declspec`

**Microsoft 전용**

저장소 클래스 정보를 지정 하기 위한 확장 특성 구문은 **`__declspec`** 키워드를 사용 합니다 .이 키워드는 지정 된 형식의 인스턴스가 아래 나열 된 Microsoft 전용 저장소 클래스 특성과 함께 저장 되도록 지정 합니다. 다른 저장소 클래스 한정자의 예로는 및 키워드를 들 수가 **`static`** **`extern`** 있습니다. 그러나 이 키워드는 C 및 C++ 언어의 ANSI 사양에 포함되므로 확장 특성 구문에는 사용되지 않습니다. 확장명 특성 구문은 C 및 C++ 언어에 대한 Microsoft 전용 확장을 간소화하고 표준화합니다.

## <a name="grammar"></a>문법

*`decl-specifier`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__declspec (`**  *`extended-decl-modifier-seq`*  **`)`**

*`extended-decl-modifier-seq`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`extended-decl-modifier`* <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`extended-decl-modifier`* *`extended-decl-modifier-seq`*

*`extended-decl-modifier`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`align(`***number***`)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`allocate("`***segname***`")`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`allocator`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`appdomain`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`code_seg("`***segname***`")`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`deprecated`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllimport`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllexport`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`jitintrinsic`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`naked`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`noalias`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`noinline`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`noreturn`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`nothrow`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`novtable`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`process`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`property(`**{ **`get=`** _get-func-name_ &#124;- **`,put=`** _func-name_ }**`)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`restrict`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`safebuffers`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`selectany`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`spectre(nomitigation)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`thread`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`uuid("`***Comobjectguid***`")`**

공백은 선언 한정자 시퀀스를 구분합니다. 뒤에 나오는 단원에 예제가 있습니다.

확장 특성 문법은는,,,,,,,,,,,,,,,,,,,,,,,,,,,,,, 등의 Microsoft 전용 저장소 클래스 특성을 지원 [`align`](../cpp/align-cpp.md) [`allocate`](../cpp/allocate.md) [`allocator`](../cpp/allocator.md) [`appdomain`](../cpp/appdomain.md) [`code_seg`](../cpp/code-seg-declspec.md) [`deprecated`](../cpp/deprecated-cpp.md) [`dllexport`](../cpp/dllexport-dllimport.md) [`dllimport`](../cpp/dllexport-dllimport.md) [`jitintrinsic`](../cpp/jitintrinsic.md) [`naked`](../cpp/naked-cpp.md) [`noalias`](../cpp/noalias.md) [`noinline`](../cpp/noinline.md) [`noreturn`](../cpp/noreturn.md) [`nothrow`](../cpp/nothrow-cpp.md) [`novtable`](../cpp/novtable.md) [`process`](../cpp/process.md) [`restrict`](../cpp/restrict.md) [`safebuffers`](../cpp/safebuffers.md) [`selectany`](../cpp/selectany.md) [`spectre`](../cpp/spectre.md) [`thread`](../cpp/thread.md) 합니다. 또한 다음과 같은 COM 개체 특성도 지원 합니다. [`property`](../cpp/property-cpp.md) [`uuid`](../cpp/uuid-cpp.md)

,,,,,,,,, **`code_seg`** **`dllexport`** **`dllimport`** **`naked`** **`noalias`** **`nothrow`** **`property`** **`restrict`** **`selectany`** **`thread`** 및 **`uuid`** 저장소 클래스 특성은 해당 특성이 적용 되는 개체 또는 함수의 선언에만 해당 되는 속성입니다. **`thread`** 특성은 데이터 및 개체에만 영향을 줍니다. **`naked`** 및 **`spectre`** 특성은 함수에만 영향을 줍니다. **`dllimport`** 및 **`dllexport`** 특성은 함수, 데이터 및 개체에 영향을 줍니다. **`property`**, **`selectany`** 및 특성은 **`uuid`** COM 개체에 영향을 줍니다.

이전 버전과의 호환성을 위해 **`_declspec`** 는 **`__declspec`** 컴파일러 옵션 [/Za \( 사용 안 함 언어 확장](../build/reference/za-ze-disable-language-extensions.md) 을 지정 하지 않는 경우의 동의어입니다.

**`__declspec`** 키워드는 간단한 선언의 시작 부분에 배치 해야 합니다. 컴파일러는 **`__declspec`** * 또는 & 뒤에 배치 된 키워드와 선언에서 변수 식별자 앞에 있는 모든 키워드를 무시 합니다.

**`__declspec`** 사용자 정의 형식 선언의 시작 부분에 지정 된 특성은 해당 형식의 변수에 적용 됩니다. 예를 들어:

```cpp
__declspec(dllimport) class X {} varX;
```

이 경우 특성이 `varX`에 적용됩니다. **`__declspec`** 또는 키워드 뒤에 배치 되는 특성은 **`class`** **`struct`** 사용자 정의 형식에 적용 됩니다. 예를 들어:

```cpp
class __declspec(dllimport) X {};
```

이 경우 특성이 `X`에 적용됩니다.

단순 선언에 특성을 사용 하는 일반적인 지침은 다음과 같습니다 **`__declspec`** .

*decl-지정자-시퀀스* *init-선언 목록*

*Decl 지정자-시퀀스* 는 기타 항목 (예:,, **`int`** **`float`** **`typedef`** 또는 클래스 이름), 저장소 클래스 (예:, **`static`** **`extern`** ) 또는 **`__declspec`** 확장을 포함 해야 합니다. *Init 선언 자 목록* 에는 선언의 포인터 부분을 포함 해야 합니다. 예를 들어:

```cpp
__declspec(selectany) int * pi1 = 0;   //Recommended, selectany & int both part of decl-specifier
int __declspec(selectany) * pi2 = 0;   //OK, selectany & int both part of decl-specifier
int * __declspec(selectany) pi3 = 0;   //ERROR, selectany is not part of a declarator
```

다음 코드는 정수 스레드 지역 변수를 선언하고 값을 사용하여 초기화합니다.

```cpp
// Example of the __declspec keyword
__declspec( thread ) int tls_i = 1;
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[키워드](../cpp/keywords-cpp.md)<br/>
[C 확장 스토리지 클래스 특성](../c-language/c-extended-storage-class-attributes.md)
