---
description: '자세한 정보: 컴파일러 오류 C3412'
title: 컴파일러 오류 C3412
ms.date: 11/04/2016
f1_keywords:
- C3412
helpviewer_keywords:
- C3412
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
ms.openlocfilehash: aa0dc6cfeac193afc99d003cd821663bcfc139c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313192"
---
# <a name="compiler-error-c3412"></a>컴파일러 오류 C3412

' template ': 현재 범위에서 템플릿을 특수화할 수 없습니다.

템플릿은 전역 또는 네임 스페이스 범위 에서만 클래스 범위에서 특수화할 수 있습니다.

## <a name="examples"></a>예제

다음 샘플에서는 C3412를 생성 합니다.

```cpp
// C3412.cpp
template <class T>
struct S {
   template <>
   struct S<int> {};   // C3412 in a class
};
```

다음 샘플에서는 가능한 해결 방법을 보여 줍니다.

```cpp
// C3412b.cpp
// compile with: /c
template <class T>
struct S {};

template <>
struct S<int> {};
```
