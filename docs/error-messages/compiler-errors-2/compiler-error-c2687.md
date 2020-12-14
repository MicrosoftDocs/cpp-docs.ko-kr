---
description: '자세한 정보: 컴파일러 오류 C2687'
title: 컴파일러 오류 C2687
ms.date: 11/04/2016
f1_keywords:
- C2687
helpviewer_keywords:
- C2687
ms.assetid: 1d24b24a-cd0f-41cc-975c-b08dcfb7f402
ms.openlocfilehash: 38996f2f31998ef96dd848915686adb1bf46c987
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220762"
---
# <a name="compiler-error-c2687"></a>컴파일러 오류 C2687

' type ': 예외 선언은 ' void ' 일 수 없으며 불완전 한 형식 또는 불완전 한 형식에 대 한 포인터 또는 참조를 나타낼 수 없습니다.

형식이 예외 선언의 일부가 되려면 void가 아닌 정의 되어야 합니다.

다음 샘플에서는 C2687를 생성 합니다.

```cpp
// C2687.cpp
class C;

int main() {
   try {}
   catch (C) {}   // C2687 error
}
```

해결 방법:

```cpp
// C2687b.cpp
// compile with: /EHsc
class C {};

int main() {
   try {}
   catch (C) {}
}
```
