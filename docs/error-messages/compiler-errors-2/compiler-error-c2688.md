---
description: '자세한 정보: 컴파일러 오류 C2688'
title: 컴파일러 오류 C2688
ms.date: 11/04/2016
f1_keywords:
- C2688
helpviewer_keywords:
- C2688
ms.assetid: 168c9e9d-8f65-4664-af86-db71d3e6ee46
ms.openlocfilehash: 17219fe6f4358b73ace0435e60d8fc2b7a9b6df8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330690"
---
# <a name="compiler-error-c2688"></a>컴파일러 오류 C2688

' C2:: fgrv ': varargs 함수에 대해 다중 또는 가상 상속이 지원 되지 않으므로 공변 (covariant)을 반환 합니다.

함수에 가변 인수가 포함 된 경우에는 Visual C++에서 공변 (Covariant) 반환 형식이 지원 되지 않습니다.

이 오류를 해결 하려면 변수 인수를 사용 하거나 모든 가상 함수에 대해 반환 값을 동일 하 게 설정 하지 않도록 함수를 정의 합니다.

다음 샘플에서는 C2688를 생성 합니다.

```cpp
// C2688.cpp
struct G1 {};
struct G2 {};
struct G3 : G1, G2 {};
struct G4 {};
struct G5 {};
struct G6 : G4, G5 {};
struct G7 : G3, G6 {};

struct C1 {
   virtual G4& fgrv(int,...);
};

struct C2 : C1 {
   virtual G7& fgrv(int,...);   // C2688, does not return G4&
};
```
