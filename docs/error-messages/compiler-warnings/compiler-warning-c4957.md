---
description: '자세한 정보: 컴파일러 경고 C4957'
title: 컴파일러 경고 C4957
ms.date: 11/04/2016
f1_keywords:
- C4957
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
ms.openlocfilehash: ac9d41b6161f658eb7debf438c495fbc57c6bb2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314830"
---
# <a name="compiler-warning-c4957"></a>컴파일러 경고 C4957

> '*cast*': '*cast_from*'에서 '*cast_to*' (으)로의 명시적 캐스트는 확인할 수 없습니다.

## <a name="remarks"></a>설명

캐스트로 인해 확인할 수 없는 이미지가 발생합니다.

일부 캐스트는 안전 합니다 (예: **`static_cast`** 사용자 정의 변환과를 트리거하는 **`const_cast`** ). [safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) 는 확인할 수 있는 코드를 생성합니다.

자세한 내용은 [순수형 및 안정형 코드 (c + +/cli)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)를 참조 하세요.

**/Clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

이 경고는 오류로 발생하며 [warning](../../preprocessor/warning.md) pragma 또는 [/wd](../../build/reference/compiler-option-warning-level.md) 컴파일러 옵션과 함께 사용하지 않도록 설정할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4957을 생성합니다.

```cpp
// C4957.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4957 )
using namespace System;
int main() {
   Object ^ o = "Hello, World!";
   String ^ s = static_cast<String^>(o);   // C4957
   String ^ s2 = safe_cast<String^>(o);   // OK
}
```
