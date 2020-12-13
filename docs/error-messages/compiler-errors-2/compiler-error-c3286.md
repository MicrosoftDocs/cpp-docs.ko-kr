---
description: '자세한 정보: 컴파일러 오류 C3286'
title: 컴파일러 오류 C3286
ms.date: 11/04/2016
f1_keywords:
- C3286
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
ms.openlocfilehash: 38e3b405f9093baa266cf56e5bfc7f44c7566206
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339223"
---
# <a name="compiler-error-c3286"></a>컴파일러 오류 C3286

> '*지정자*': 반복 변수에는 저장소 클래스 지정자를 사용할 수 없습니다.

반복 변수에는 저장소 클래스를 지정할 수 없습니다. 자세한 내용은에서 [저장소 클래스 (c + +)](../../cpp/storage-classes-cpp.md) 및 [에 대 한](../../dotnet/for-each-in.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3286를 생성 하 고 올바른 사용법도 보여 줍니다.

```cpp
// C3286.cpp
// compile with: /clr
int main() {
   array<int> ^p = { 1, 2, 3 };
   for each (static int i in p) {}   // C3286
   for each (int j in p) {}   // OK
}
```
