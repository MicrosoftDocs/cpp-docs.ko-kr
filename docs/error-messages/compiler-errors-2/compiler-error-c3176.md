---
description: '자세한 정보: 컴파일러 오류 C3176'
title: 컴파일러 오류 C3176
ms.date: 11/04/2016
f1_keywords:
- C3176
helpviewer_keywords:
- C3176
ms.assetid: 6cc8d602-8e15-47a7-b1b5-e93e5d50e271
ms.openlocfilehash: 8dda09ccbe6faa80d77f43c38b2c94427956cc3f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242043"
---
# <a name="compiler-error-c3176"></a>컴파일러 오류 C3176

' type ': 지역 값 형식을 선언할 수 없습니다.

전역 범위에서는 클래스를 값 형식 으로만 선언할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3176를 생성 합니다.

```cpp
// C3176.cpp
// compile with: /clr
int main () {
   enum class C {};   // C3176
}
```
