---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4532'
title: 컴파일러 경고(수준 1) C4532
ms.date: 11/04/2016
f1_keywords:
- C4532
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
ms.openlocfilehash: 9468ca1242397289c832fec28d71cf245c6c8a5f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294810"
---
# <a name="compiler-warning-level-1-c4532"></a>컴파일러 경고(수준 1) C4532

' continue ': 종료를 처리 하는 동안 __finally/finally 블록 밖으로 점프 하면 정의 되지 않은 동작이 발생 합니다.

컴파일러에서 다음 키워드 중 하나가 발생 했습니다.

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

[__finally](../../cpp/try-finally-statement.md) 에서 또는 비정상적인 종료 시 [마지막으로](../../dotnet/finally.md) 차단 하는 경우

예외가 발생 하 고 종료 처리기 (또는 finally 블록)를 실행 하는 동안 스택이 해제 되는 동안 **`__finally`** **`__finally`** 블록이 종료 되기 전에 코드가 블록 밖으로 점프 하면 **`__finally`** 동작이 정의 되지 않습니다. 제어는 해제 코드에 반환 될 수 없으므로 예외가 제대로 처리 되지 않을 수 있습니다.

블록 밖으로 이동 해야 하는 경우 **`__finally`** 에는 먼저 비정상적인 종료를 확인 합니다.

다음 샘플에서는 C4532를 생성 합니다. 경고를 해결 하기 위해 점프 문을 주석 처리 하기만 하면 됩니다.

```cpp
// C4532.cpp
// compile with: /W1
// C4532 expected
int main() {
   int i;
   for (i = 0; i < 10; i++) {
      __try {
      } __finally {
         // Delete the following line to resolve.
         continue;
      }

      __try {
      } __finally {
         // Delete the following line to resolve.
         break;
      }
   }
}
```
