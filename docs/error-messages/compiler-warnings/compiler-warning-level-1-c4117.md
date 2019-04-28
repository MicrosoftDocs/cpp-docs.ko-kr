---
title: 컴파일러 경고(수준 1) C4117
ms.date: 11/04/2016
f1_keywords:
- C4117
helpviewer_keywords:
- C4117
ms.assetid: c45aa281-4cc1-4dfd-bd32-bd7a60ddd577
ms.openlocfilehash: 657963dd0199c1474f0cef566e5a177a16247521
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299805"
---
# <a name="compiler-warning-level-1-c4117"></a>컴파일러 경고(수준 1) C4117

'name' 매크로 이름이 예약되었습니다. 'Command'는 무시됩니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. 미리 정의된 매크로를 정의 또는 정의 해제하려고 합니다.

1. **정의된**전처리기 연산자를 정의 또는 정의 해제하려고 합니다.

다음 샘플에서는 C4117을 생성합니다.

```
// C4117.cpp
// compile with: /W1
#define __FILE__ test         // C4117. __FILE__ is a predefined macro
#define ValidMacroName test   // ok

int main() {
}
```