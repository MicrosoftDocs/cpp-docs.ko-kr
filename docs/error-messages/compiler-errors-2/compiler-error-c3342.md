---
description: '자세한 정보: 컴파일러 오류 C3342'
title: 컴파일러 오류 C3342
ms.date: 11/04/2016
f1_keywords:
- C3342
helpviewer_keywords:
- C3342
ms.assetid: 5c6d784f-bebe-4f7e-8615-44ca6f78bfba
ms.openlocfilehash: dfbeada49972832c238acb6c0fa656e3e75d7089
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337304"
---
# <a name="compiler-error-c3342"></a>컴파일러 오류 C3342

'attribute': 모호한 특성입니다.

컴파일러가 특성의 정의를 둘 이상 찾았습니다.

특성이 두 번 이상 정의되었습니다.

자세한 내용은 [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3342를 생성합니다.

```cpp
// C3342.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Reflection;

[AttributeUsage(AttributeTargets::All)]
public ref class XAttribute : public  Attribute {};

[AttributeUsage(AttributeTargets::All)]
public ref class X : public Attribute {};

[X]   // C3342 could refer to X or XAttribute
// try the following line instead
// [XAttribute]
public ref class Class4 {};
```
