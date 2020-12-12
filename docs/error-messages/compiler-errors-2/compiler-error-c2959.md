---
description: '자세한 정보: 컴파일러 오류 C2959'
title: 컴파일러 오류 C2959
ms.date: 11/04/2016
f1_keywords:
- C2959
helpviewer_keywords:
- C2959
ms.assetid: d66bb2a8-70c3-4209-a358-b0c47f111a50
ms.openlocfilehash: aa5da1db36ce8544e95ad509402b066e664faf18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210428"
---
# <a name="compiler-error-c2959"></a>컴파일러 오류 C2959

제네릭 클래스 또는 함수는 템플릿의 멤버가 될 수 없습니다.

자세한 내용은 [Windows 런타임 및 관리 되는 템플릿](../../extensions/windows-runtime-and-managed-templates-cpp-component-extensions.md) 및 [제네릭](../../extensions/generics-cpp-component-extensions.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2959를 생성 합니다.

```cpp
// C2959.cpp
// compile with: /clr /c
template <class T> ref struct S {
   generic <class U> ref struct GR1;   // C2959
};
```
