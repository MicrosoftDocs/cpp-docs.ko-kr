---
description: '자세한 정보: 컴파일러 오류 C3215'
title: 컴파일러 오류 C3215
ms.date: 11/04/2016
f1_keywords:
- C3215
helpviewer_keywords:
- C3215
ms.assetid: d0d16007-8885-42e0-b086-2d3a61f348c5
ms.openlocfilehash: 1291f480e4f01502db4232585f7e7786fd637072
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173742"
---
# <a name="compiler-error-c3215"></a>컴파일러 오류 C3215

'type1': 제네릭 형식 매개 변수가 이미 'type2'의 제약을 받습니다.

제약 조건을 두 번 이상 지정했습니다.

제네릭에 대한 자세한 내용은 [Generics](../../extensions/generics-cpp-component-extensions.md)을 참조하세요.

다음 샘플에서는 C3215를 생성합니다.

```cpp
// C3215.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where T : A,A
ref class C {};   // C3215
```

해결 방법:

```cpp
// C3215b.cpp
// compile with: /clr /c
interface struct A {};

generic <class T>
where T : A
ref class C {};
```
