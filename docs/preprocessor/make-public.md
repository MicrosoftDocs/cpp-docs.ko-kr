---
description: '다음에 대 한 자세한 정보: make_public pragma'
title: make_public pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
ms.openlocfilehash: 327a9882e13f9c51182e0673443566b56177d320
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333405"
---
# <a name="make_public-pragma"></a>make_public pragma

네이티브 형식이 공용 어셈블리 액세스 가능성을 갖도록 지정합니다.

## <a name="syntax"></a>Syntax

> **#pragma make_public (** *형식* **)**

### <a name="parameters"></a>매개 변수

*type*\
공용 어셈블리 액세스 가능성을 부여할 형식의 이름입니다.

## <a name="remarks"></a>설명

**make_public** 는 참조 하려는 네이티브 형식이 변경할 수 없는 헤더 파일에서 가져온 경우에 유용 합니다. Public 어셈블리 표시 유형이 있는 형식의 public 함수 시그니처에 네이티브 형식을 사용 하려면 네이티브 형식에도 공용 어셈블리 액세스 가능성이 있어야 합니다. 그렇지 않으면 컴파일러에서 경고를 표시 합니다.

전역 범위에 **make_public** 를 지정 해야 합니다. 소스 코드 파일의 끝까지를 통해 선언 된 지점 에서만 적용 됩니다.

네이티브 형식은 암시적 또는 명시적 전용일 수 있습니다. 자세한 내용은 [형식 표시 유형](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)을 참조 하세요.

## <a name="examples"></a>예제

다음 샘플은 두 개의 네이티브 구조체에 대 한 정의를 포함 하는 헤더 파일의 내용입니다.

```cpp
// make_public_pragma.h
struct Native_Struct_1 { int i; };
struct Native_Struct_2 { int i; };
```

다음 코드 샘플에서는 헤더 파일을 사용 합니다. **Make_public** 를 사용 하 여 네이티브 구조체를 public으로 명시적으로 표시 하지 않으면 공용 관리 되는 형식에서 public 함수 시그니처의 네이티브 구조체를 사용 하려고 할 때 컴파일러에서 경고를 생성 합니다.

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

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
