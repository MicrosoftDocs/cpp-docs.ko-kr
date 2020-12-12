---
description: '자세한 정보: 컴파일러 오류 C2989'
title: 컴파일러 오류 C2989
ms.date: 11/04/2016
f1_keywords:
- C2989
helpviewer_keywords:
- C2989
ms.assetid: 936303d8-eb3b-4746-82ec-2f18020a6f64
ms.openlocfilehash: 38838630f5be23698de099d8c40f7e9b96bc2b13
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338606"
---
# <a name="compiler-error-c2989"></a>컴파일러 오류 C2989

' class ': 클래스 형식이 이미 비 클래스 형식으로 선언 되었습니다.

클래스 제네릭 또는 템플릿에서 템플릿이 아닌 클래스 또는 제네릭이 아닌 클래스를 다시 정의 합니다. 헤더 파일의 충돌을 검사 합니다.

다음 샘플에서는 C2989를 생성 합니다.

```cpp
// C2989.cpp
// compile with: /c
class C{};

template <class T>
class C{};  // C2989
class C2{};
```

제네릭을 사용 하는 경우에도 C2989이 발생할 수 있습니다.

```cpp
// C2989b.cpp
// compile with: /clr /c
ref class GC1;

generic <typename T> ref class GC1;   // C2989
template <typename T> ref class GC2;

generic <typename T> ref class GC2;   // C2989
generic <typename T> ref class GCb;
template <typename T> ref class GC2;
generic <typename T> ref class GCc;
```
