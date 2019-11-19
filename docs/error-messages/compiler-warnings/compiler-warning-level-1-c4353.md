---
title: 컴파일러 경고 (수준 1) C4353
ms.date: 11/04/2016
f1_keywords:
- C4353
helpviewer_keywords:
- C4353
ms.assetid: 6e79f186-ed82-4c95-9923-0ad5bb9c4db1
ms.openlocfilehash: f04bc78e1ff6183208f888d9072bfe90b3aca083
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966542"
---
# <a name="compiler-warning-level-1-c4353"></a>컴파일러 경고 (수준 1) C4353

비표준 확장이 사용 됨: 상수 0을 함수 식으로 사용 했습니다. 대신 ' __noop ' 함수 내장 함수를 사용 하십시오.

상수 0은 함수 식으로 사용할 수 없습니다. 자세한 내용은 [__noop](../../intrinsics/noop.md)를 참조 하세요.

다음 샘플에서는 C4353를 생성 합니다.

```cpp
// C4353.cpp
// compile with: /W1
void MyPrintf(void){};
#define X 0
#if X
   #define DBPRINT MyPrint
#else
   #define DBPRINT 0   // C4353 expected
#endif
int main(){
DBPRINT();
}
```