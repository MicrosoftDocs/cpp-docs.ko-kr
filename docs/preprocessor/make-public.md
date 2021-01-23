---
description: pragmaMicrosoft C/c + +의 make_public 지시문에 대해 자세히 알아보세요.
title: make_public pragma
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
helpviewer_keywords:
- pragma, make_public
- make_public pragma
no-loc:
- pragma
ms.openlocfilehash: 4bc3370ac0901ff9a0656de5657f9c9f557e1dff
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713521"
---
# <a name="make_public-no-locpragma"></a>`make_public` pragma

네이티브 형식이 공용 어셈블리 액세스 가능성을 갖도록 지정합니다.

## <a name="syntax"></a>구문

> **`#pragma make_public(`***유형***`)`**

### <a name="parameters"></a>매개 변수

*type*\
공용 어셈블리 액세스 가능성을 부여할 형식의 이름입니다.

## <a name="remarks"></a>설명

**`make_public`** 는 변경할 수 없는 헤더 파일에서 참조 하려는 네이티브 형식이 인 경우에 유용 합니다. Public 어셈블리 표시 유형이 있는 형식의 public 함수 시그니처에 네이티브 형식을 사용 하려면 네이티브 형식에도 공용 어셈블리 액세스 가능성이 있어야 합니다. 그렇지 않으면 컴파일러에서 경고를 표시 합니다.

**`make_public`** 전역 범위에서 지정 해야 합니다. 소스 코드 파일의 끝까지를 통해 선언 된 지점 에서만 적용 됩니다.

네이티브 형식은 암시적 또는 명시적 전용일 수 있습니다. 자세한 내용은 [형식 표시 유형](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)을 참조 하세요.

## <a name="examples"></a>예

다음 샘플은 두 개의 네이티브 구조체에 대 한 정의를 포함 하는 헤더 파일의 내용입니다.

```cpp
// make_public_pragma.h
struct Native_Struct_1 { int i; };
struct Native_Struct_2 { int i; };
```

다음 코드 샘플에서는 헤더 파일을 사용 합니다. 를 사용 하 여 네이티브 구조체를 public으로 명시적으로 표시 하지 않는 한 **`make_public`** , 공용 관리 되는 형식에서 public 함수 시그니처의 네이티브 구조체를 사용 하려고 하면 컴파일러에서 경고를 생성 함을 보여 줍니다.

```cpp
// make_public_pragma.cpp
// compile with: /c /clr /W1
#pragma warning (default : 4692)
#include "make_public_pragma.h"
#pragma make_public(Native_Struct_1)

public ref struct A {
   void Test(Native_Struct_1 u) {u.i = 0;}   // OK
   void Test(Native_Struct_2 u) {u.i = 0;}   // C4692
};
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
