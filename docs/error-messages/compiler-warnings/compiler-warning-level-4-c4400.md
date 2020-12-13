---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4400'
title: 컴파일러 경고(수준 4) C4400
ms.date: 11/04/2016
f1_keywords:
- C4400
helpviewer_keywords:
- C4400
ms.assetid: f135fe98-4f92-4e07-9d71-2621b36ee755
ms.openlocfilehash: c91a77758127b5c5b5c5ab742c980f6367830812
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136242"
---
# <a name="compiler-warning-level-4-c4400"></a>컴파일러 경고(수준 4) C4400

' type ':이 형식에는 const/volatile 한정자를 사용할 수 없습니다.

[Const](../../cpp/const-cpp.md)및 [volatile](../../cpp/volatile-cpp.md)한정자는 공용 언어 런타임 형식의 변수와 함께 사용할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4400를 생성 합니다.

```cpp
// C4400.cpp
// compile with: /clr /W4
// C4401 expected
using namespace System;
#pragma warning (disable : 4101)
int main() {
   const String^ str;   // C4400
   volatile String^ str2;   // C4400
}
```
