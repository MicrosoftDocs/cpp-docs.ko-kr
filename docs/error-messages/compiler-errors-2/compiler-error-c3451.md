---
title: 컴파일러 오류 C3451
ms.date: 11/04/2016
f1_keywords:
- C3451
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
ms.openlocfilehash: d6a0d1234d8f25c6a55fffa7170f37aae27f5817
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501322"
---
# <a name="compiler-error-c3451"></a>컴파일러 오류 C3451

' attribute ': ' type '에 관리 되지 않는 특성을 적용할 수 없습니다.

CLR 형식에는 c + + 특성을 적용할 수 없습니다. 자세한 내용은 [c + + 특성 참조](../../windows/attributes/attributes-alphabetical-reference.md) 를 참조 하세요.

자세한 내용은 [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)을 참조하세요.

이 오류는 Visual Studio 2005에 대해 수행 된 컴파일러 규칙 작업의 결과로 생성 될 수 있습니다. CLR 프로그래밍을 사용 하 여 사용자 정의 특성에서 [uuid](../../windows/attributes/uuid-cpp-attributes.md) 특성이 더 이상 허용 되지 않습니다. 대신 <xref:System.Runtime.InteropServices.GuidAttribute>를 사용하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3451를 생성 합니다.

```cpp
// C3451.cpp
// compile with: /clr /c
using namespace System;
[ attribute(AttributeTargets::All) ]
public ref struct MyAttr {};

[ MyAttr, helpstring("test") ]   // C3451
// try the following line instead
// [ MyAttr ]
public ref struct ABC {};
```
