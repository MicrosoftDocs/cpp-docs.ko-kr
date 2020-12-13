---
description: '자세한 정보: 컴파일러 오류 C3133'
title: 컴파일러 오류 C3133
ms.date: 11/04/2016
f1_keywords:
- C3133
helpviewer_keywords:
- C3133
ms.assetid: 4a709405-b67b-4061-8a2a-19fa5fb34a2a
ms.openlocfilehash: 3559e5864ea5f8d5e690a77899d6314ee2b65519
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177382"
---
# <a name="compiler-error-c3133"></a>컴파일러 오류 C3133

C + + varargs에 특성을 적용할 수 없습니다.

특성이 올바르게 적용되었습니다. 변수 인수를 나타내는 줄임표에는 특성을 적용할 수 없습니다.

자세한 내용은 [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3133를 생성 합니다.

```cpp
// C3133.cpp
// compile with: /clr /c
ref struct MyAttr: System::Attribute {};
void Func([MyAttr]...);   // C3133
void Func2([MyAttr] int i);   // OK
```
