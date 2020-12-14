---
description: '자세한 정보: 컴파일러 오류 C3413'
title: 컴파일러 오류 C3413
ms.date: 11/04/2016
f1_keywords:
- C3413
helpviewer_keywords:
- C3413
ms.assetid: de6c9b05-c373-4bd8-8cb0-12c2cd2e5674
ms.openlocfilehash: 1b6f5ba895ce1db433fb8c8366e62ab3c0790f84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316247"
---
# <a name="compiler-error-c3413"></a>컴파일러 오류 C3413

'name': 잘못된 명시적 인스턴스화입니다.

컴파일러가 잘못된 형식의 명시적 인스턴스화를 검색했습니다.

다음 샘플에서는 C3413을 생성합니다.

```cpp
// C3413.cpp
template
class MyClass {};   // C3413
```

해결 방법:

```cpp
// C3413b.cpp
// compile with: /c
template <class T>
class MyClass {};

template <>
class MyClass<int> {};
```
