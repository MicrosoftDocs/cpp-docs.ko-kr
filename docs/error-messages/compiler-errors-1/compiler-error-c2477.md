---
description: '자세한 정보: 컴파일러 오류 C2477'
title: 컴파일러 오류 C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: 50cbb3523e6dc30dc465876435db40a80e2768fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164395"
---
# <a name="compiler-error-c2477"></a>컴파일러 오류 C2477

' member ': 정적 데이터 멤버는 파생 클래스를 통해 초기화할 수 없습니다.

템플릿 클래스의 정적 데이터 멤버가 잘못 초기화 되었습니다. 이는 ISO c + + 표준을 준수 하기 위해 Visual Studio .NET 2003 이전 버전의 Microsoft c + + 컴파일러에 대 한 주요 변경 내용입니다.

다음 샘플에서는 C2477를 생성 합니다.

```cpp
// C2477.cpp
// compile with: /Za /c
template <class T>
struct S {
   static int n;
};

struct X {};
struct A: S<X> {};

int A::n = 0;   // C2477

template<>
int S<X>::n = 0;
```
