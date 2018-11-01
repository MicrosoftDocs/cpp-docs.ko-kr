---
title: 컴파일러 오류 C3451
ms.date: 11/04/2016
f1_keywords:
- C3451
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
ms.openlocfilehash: 041c0c22b7ae842073bfd6656d9cbb3b2a20af9c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430058"
---
# <a name="compiler-error-c3451"></a>컴파일러 오류 C3451

'attribute': 'type' 관리 되지 않는 특성을 적용할 수 없습니다

C + + 특성은 CLR 형식에 적용할 수 없습니다. 참조 [c + + 특성 참조](../../windows/cpp-attributes-reference.md) 자세한 내용은 합니다.

자세한 내용은 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)을 참조하세요.

이 오류는 Visual c + + 2005에 대해 수행한 컴파일러 규칙 작업의 결과로 생성 될 수 없습니다: 합니다 [uuid](../../windows/uuid-cpp-attributes.md) CLR 프로그래밍을 사용 하 여 사용자 정의 특성에서 특성을 사용할 수 없습니다. 대신 <xref:System.Runtime.InteropServices.GuidAttribute>를 사용하세요.

## <a name="example"></a>예제

다음 샘플 C3451를 생성합니다.

```
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