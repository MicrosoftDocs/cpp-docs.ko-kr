---
title: 컴파일러 경고(수준 4) C4690
ms.date: 07/03/2018
f1_keywords:
- C4690
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
ms.openlocfilehash: de996128c68ebf96b4a00f6206cbaf54d97ca275
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509975"
---
# <a name="compiler-warning-level-4-c4690"></a>컴파일러 경고(수준 4) C4690

> \[ emitidl (pop)]: 푸시 횟수 보다 팝 횟수가 많습니다.

## <a name="remarks"></a>설명

[emitidl](../../windows/attributes/emitidl.md) 특성을 넣은 횟수보다 꺼낸 횟수가 한 번 더 많습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4690을 생성합니다. 이 문제를 해결 하려면 특성이 푸시되는 횟수 만큼 정확 하 게 팝 되는지 확인 합니다.

```cpp
// C4690.cpp
// compile with: /c /W4
[emitidl(pop)];   // C4690
class x {};
```
