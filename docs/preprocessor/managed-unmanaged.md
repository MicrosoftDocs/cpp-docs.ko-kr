---
description: Microsoft c + +의 관리 되는 지시문 및 관리 되지 않는 지시문에 대해 자세히 알아보세요. pragma
title: 관리 및 관리 되지 않는 pragma
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
helpviewer_keywords:
- managed pragma
- pragma, unmanaged
- pragma, managed
- unmanaged pragma
no-loc:
- pragma
ms.openlocfilehash: a106e9a1370daeedb94bbf5e4d092ae85457a3d2
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713508"
---
# <a name="managed-and-unmanaged-no-locpragma"></a>`managed` 및 `unmanaged` pragma

함수 수준 제어를 사용 하 여 함수를 관리 되거나 관리 되지 않는 것으로 컴파일합니다.

## <a name="syntax"></a>구문

> **`#pragma managed`**\
> **`#pragma unmanaged`**\
> **`#pragma managed(`** [ **`push,`** ] { **`on`** | **`off`** } **`)`**\
> **`#pragma managed(pop)`**

## <a name="remarks"></a>설명

[`/clr`](../build/reference/clr-common-language-runtime-compilation.md)컴파일러 옵션은 함수를 관리 되거나 관리 되지 않는 것으로 컴파일하기 위한 모듈 수준 제어를 제공 합니다.

관리 되지 않는 함수는 네이티브 플랫폼에 대해 컴파일됩니다. 프로그램의 해당 부분을 실행 하면 공용 언어 런타임에 의해 네이티브 플랫폼으로 전달 됩니다.

함수는를 사용할 때 기본적으로 관리 되는 것으로 컴파일됩니다 **`/clr`** .

또는를 적용할 **`managed`** 때 **`unmanaged`** pragma :

- pragma함수 본문 내에는 없지만 앞에 함수를 추가 합니다.

- pragmaAfter 문을 추가 `#include` 합니다. 문 앞에 사용 하지 마십시오 `#include` .

컴파일러는를 무시 **`managed`** 하 고가 **`unmanaged`** pragma **`/clr`** 컴파일에 사용 되지 않습니다.

템플릿 함수를 인스턴스화하면 pragma 템플릿이 정의 된 상태에 따라 템플릿이 관리 되는지 또는 관리 되지 않는 것으로 결정 됩니다.

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

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
