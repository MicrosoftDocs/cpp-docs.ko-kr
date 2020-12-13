---
description: '자세한 정보: 관리 되는 관리 되지 않는 pragma'
title: 관리, 관리되지 않는 pragmas
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
ms.openlocfilehash: 10f632b009c9922f67f4321acc862142d895e7ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333390"
---
# <a name="managed-unmanaged-pragmas"></a>관리, 관리되지 않는 pragmas

함수 수준 제어를 사용 하 여 함수를 관리 되거나 관리 되지 않는 것으로 컴파일합니다.

## <a name="syntax"></a>Syntax

> **관리 #pragma**\
> **#pragma 관리 되지 않음**\
> **#pragma 관리 (** [ **push,** ] { **on**  |  **off** } **)**\
> **#pragma 관리 (pop)**

## <a name="remarks"></a>설명

[/Clr](../build/reference/clr-common-language-runtime-compilation.md) 컴파일러 옵션은 함수를 관리 되거나 관리 되지 않는 것으로 컴파일하기 위한 모듈 수준 제어를 제공 합니다.

관리 되지 않는 함수는 네이티브 플랫폼에 대해 컴파일됩니다. 프로그램의 해당 부분을 실행 하면 공용 언어 런타임에 의해 네이티브 플랫폼으로 전달 됩니다.

함수는 `/clr`이 사용되는 경우 기본적으로 관리되는 것으로 컴파일됩니다.

다음 pragma를 적용할 때

- 함수 본문 내에서가 아니라 함수 앞에 pragma를 추가 합니다.

- `#include` 문 다음에 pragma를 추가합니다. 문 앞에 이러한 pragma를 사용 하지 마세요 `#include` .

컴파일에 사용 되지 않는 경우 컴파일러는 **관리 되** 는 및 **관리 되지 않는** pragma를 무시 합니다 `/clr` .

템플릿 함수를 인스턴스화하면 템플릿이 정의 될 때 pragma 상태가 관리 되는지 또는 관리 되지 않는 지를 결정 합니다.

자세한 내용은 [혼합 어셈블리 초기화](../dotnet/initialization-of-mixed-assemblies.md)를 참조 하세요.

## <a name="example"></a>예제

```cpp
// pragma_directives_managed_unmanaged.cpp
// compile with: /clr
#include <stdio.h>

// func1 is managed
void func1() {
   System::Console::WriteLine("In managed function.");
}

// #pragma unmanaged
// push managed state on to stack and set unmanaged state
#pragma managed(push, off)

// func2 is unmanaged
void func2() {
   printf("In unmanaged function.\n");
}

// #pragma managed
#pragma managed(pop)

// main is managed
int main() {
   func1();
   func2();
}
```

```Output
In managed function.
In unmanaged function.
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
