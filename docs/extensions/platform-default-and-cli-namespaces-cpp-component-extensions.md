---
description: '자세히 알아보기: Platform, default 및 cli 네임 스페이스 (c + +/CLI 및 c + +/CX)'
title: 플랫폼, 기본값 및 cli 네임스페이스(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- lang
- cli
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
ms.openlocfilehash: 1b4b47a1568b1a137bc49a09b8b50feb8ec3a76b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185676"
---
# <a name="platform-default-and-cli-namespaces--ccli-and-ccx"></a>플랫폼, 기본값 및 cli 네임스페이스(C++/CLI 및 C++/CX)

네임스페이스는 언어 요소의 이름을 한정하므로, 이름이 그렇지 않았다면 소스 코드의 다른 곳에 있는 같은 이름과 충돌하지 않습니다. 예를 들어 이름 충돌로 인해 컴파일러에서 [상황에 맞는 키워드](context-sensitive-keywords-cpp-component-extensions.md)를 인식하지 못할 수 있습니다. 네임스페이스는 컴파일러에 의해 사용되지만 컴파일된 어셈블리에 유지되지 않습니다.

## <a name="all-runtimes"></a>모든 런타임

Visual Studio에서는 프로젝트를 만들 때 프로젝트의 기본 네임스페이스를 제공합니다. C++/CX에서는 .winmd 파일의 이름이 루트 네임스페이스의 이름과 일치해야 하지만, 네임스페이스 이름을 수동으로 바꿀 수 있습니다.

## <a name="windows-runtime"></a>Windows 런타임

자세한 내용은 [네임스페이스 및 형식 표시 유형(C++/CX)](../cppcx/namespaces-and-type-visibility-c-cx.md)을 참조하세요.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

### <a name="syntax"></a>구문

```cpp
using namespace cli;
```

### <a name="remarks"></a>설명

C++/CLI에서는 **cli** 네임스페이스를 지원합니다. 를 사용 하 여 컴파일할 때 `/clr` **`using`** 구문 섹션의 문이 암시 됩니다.

다음 언어 기능은 **cli** 네임스페이스에 있습니다.

- [배열](arrays-cpp-component-extensions.md)

- [interior_ptr (c + +/CLI)](interior-ptr-cpp-cli.md)

- [pin_ptr (c + +/CLI)](pin-ptr-cpp-cli.md)

- [safe_cast](safe-cast-cpp-component-extensions.md)

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예제

다음 코드 예제에서는 **cli** 네임스페이스의 기호를 코드에서 사용자 정의 기호로 사용할 수 있음을 보여 줍니다.  그러나 사용자 정의 기호로 사용한 경우 같은 이름의 **cli** 언어 요소에 대한 참조를 명시적 또는 암시적으로 한정해야 합니다.

```cpp
// cli_namespace.cpp
// compile with: /clr
using namespace cli;
int main() {
   array<int> ^ MyArray = gcnew array<int>(100);
   int array = 0;

   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062

   // OK
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);
}
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
