---
title: 컴파일러 오류 C2959 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2959
dev_langs:
- C++
helpviewer_keywords:
- C2959
ms.assetid: d66bb2a8-70c3-4209-a358-b0c47f111a50
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f225dccc917e34fba690064d66cf1cda36219877
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078974"
---
# <a name="compiler-error-c2959"></a>컴파일러 오류 C2959

제네릭 클래스 또는 함수 템플릿의 구성원이 아닐 수 있습니다.

자세한 내용은 [Windows 런타임 및 관리 템플릿](../../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md) 하 고 [제네릭](../../windows/generics-cpp-component-extensions.md)합니다.

## <a name="example"></a>예제

다음 샘플 C2959를 생성합니다.

```
// C2959.cpp
// compile with: /clr /c
template <class T> ref struct S {
   generic <class U> ref struct GR1;   // C2959
};
```