---
description: '자세한 정보: 컴파일러 오류 C3868'
title: 컴파일러 오류 C3868
ms.date: 11/04/2016
f1_keywords:
- C3868
helpviewer_keywords:
- C3868
ms.assetid: f0e45c2a-2149-4885-a03b-0d230069f03a
ms.openlocfilehash: c71a5321b99e5852a2dc7267dd098bfec08c5ad2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222816"
---
# <a name="compiler-error-c3868"></a>컴파일러 오류 C3868

' type ': 제네릭 매개 변수 ' parameter '의 제약 조건이 선언에 대 한 제약 조건과 다릅니다.

여러 선언에 동일한 제네릭 제약 조건이 있어야 합니다.  자세한 내용은 [제네릭](../../extensions/generics-cpp-component-extensions.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3868를 생성 합니다.

```cpp
// C3868.cpp
// compile with: /clr /c
interface struct I1;

generic <typename T> ref struct MyStruct;
generic <typename U> where U : I1 ref struct MyStruct;   // C3868

// OK
generic <typename T> ref struct MyStruct2;
generic <typename U> ref struct MyStruct2;

generic <typename T> where T : I1 ref struct MyStruct3;
generic <typename U> where U : I1 ref struct MyStruct3;
```
