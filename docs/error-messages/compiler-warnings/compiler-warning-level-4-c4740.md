---
title: 컴파일러 경고(수준 4) C4740
ms.date: 11/04/2016
f1_keywords:
- C4740
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
ms.openlocfilehash: 679f577eb7911b401473ee570e367ed5a8a094eb
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989481"
---
# <a name="compiler-warning-level-4-c4740"></a>컴파일러 경고(수준 4) C4740

인라인 asm 코드 내부 또는 외부 흐름은 전역 최적화를 표시 하지 않습니다.

`asm` 블록 사이 또는 외부로 이동 하는 경우 해당 함수에 대해 전역 최적화를 사용할 수 없습니다.

다음 샘플에서는 C4740를 생성 합니다.

```cpp
// C4740.cpp
// compile with: /O2 /W4
// processor: x86
int main() {
   __asm jmp tester
   tester:;
}
```
