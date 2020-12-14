---
description: '자세한 정보: 컴파일러 오류 C3397'
title: 컴파일러 오류 C3397
ms.date: 11/04/2016
f1_keywords:
- C3397
helpviewer_keywords:
- C3397
ms.assetid: a8536e87-79c4-4ed7-bd96-42704d06391f
ms.openlocfilehash: 2d450e11849b58af55e34396674597fa3a60166d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313179"
---
# <a name="compiler-error-c3397"></a>컴파일러 오류 C3397

기본 인수에서는 집합체 초기화가 허용되지 않습니다.

배열이 잘못 선언되었습니다.  자세한 내용은 [배열](../../extensions/arrays-cpp-component-extensions.md) 을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3397을 생성합니다.

```cpp
// C3397.cpp
// compile with: /clr
// /clr /c
void Func(array<int> ^p = gcnew array<int> { 1, 2, 3 });   // C3397
void Func2(array<int> ^p = gcnew array<int> (3));   // OK

int main() {
   array<int> ^p = gcnew array<int> { 1, 2, 3};   // OK
}
```
