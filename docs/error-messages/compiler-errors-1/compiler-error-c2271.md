---
title: 컴파일러 오류 C2271
ms.date: 11/04/2016
f1_keywords:
- C2271
helpviewer_keywords:
- C2271
ms.assetid: ea47bf57-f55d-4171-8e98-95a71d62820e
ms.openlocfilehash: bddd5a413c0ca16d7b344e5d6c478b07f82ca1a5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758712"
---
# <a name="compiler-error-c2271"></a>컴파일러 오류 C2271

' operator ': new/delete에는 형식 목록 한정자를 사용할 수 없습니다.

연산자 (`new` 또는 `delete`)는 메모리 모델 지정자를 사용 하 여 선언 됩니다.

다음 샘플에서는 C2271를 생성 합니다.

```cpp
// C2271.cpp
// compile with: /c
void* operator new(size_t) const {   // C2271
// try the following line instead
// void* operator new(size_t) {
   return 0;
}

struct X {
   static void* operator new(size_t) const;   // C2271
   // try the following line instead
   // void * X::operator new(size_t) const;   // static member operator new
};
```
