---
description: '자세한 정보: 컴파일러 오류 C3113'
title: 컴파일러 오류 C3113
ms.date: 11/04/2016
f1_keywords:
- C3113
helpviewer_keywords:
- C3113
ms.assetid: 3afdc668-b29e-474e-9ea3-aa027d42db7c
ms.openlocfilehash: dcad27e26e0795b8d1901cca51dc5cd16a88ae5c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115991"
---
# <a name="compiler-error-c3113"></a>컴파일러 오류 C3113

' structure '는 template/generic 일 수 없습니다.

클래스 템플릿 또는 클래스를 인터페이스 또는 열거형에서 제네릭으로 만들려고 했습니다.

다음 샘플에서는 C3113를 생성 합니다.

```cpp
// C3113.cpp
// compile with: /c
template <class T>
enum E {};   // C3113
// try the following line instead
// class MyClass{};
```
