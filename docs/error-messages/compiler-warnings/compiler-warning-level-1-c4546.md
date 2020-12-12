---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4546'
title: 컴파일러 경고(수준 1) C4546
ms.date: 11/04/2016
f1_keywords:
- C4546
helpviewer_keywords:
- C4546
ms.assetid: 071e1709-3841-46c1-8e71-96109cd22041
ms.openlocfilehash: b99980c2a007e8726a152c16e0ec05b394ea2da8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212222"
---
# <a name="compiler-warning-level-1-c4546"></a>컴파일러 경고(수준 1) C4546

쉼표 앞의 함수에 인수 목록이 없습니다.

컴파일러가 잘못 된 형식의 쉼표 식을 발견 했습니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4546를 생성 합니다.

```cpp
// C4546.cpp
// compile with: /W1
#pragma warning (default : 4546)
void f(int i) {
   i++;
}

int main() {
   int i = 0, k = 0;

   if ( f, k )   // C4546
   // try the following line instead
   // if ( f(i), k )
      i++;
}
```
