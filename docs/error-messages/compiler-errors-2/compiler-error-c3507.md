---
title: 컴파일러 오류 C3507
ms.date: 11/04/2016
f1_keywords:
- C3507
helpviewer_keywords:
- C3507
ms.assetid: 75f89767-f6f9-40f6-9820-81a49e09abdf
ms.openlocfilehash: a38efcc0d74bbea0e0bf767cb9e5a11561ab4fb8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507128"
---
# <a name="compiler-error-c3507"></a>컴파일러 오류 C3507

ProgID에는 ' id '가 39 자이 하만 포함 될 수 있습니다. '. ' 이외의 문장 부호는 포함 하지 않습니다. 숫자로 시작할 수도 없습니다.

[Progid](../../windows/attributes/progid.md) 특성에는 사용할 수 있는 값에 대 한 제한이 있습니다.

다음 샘플에서는 C3507를 생성 합니다.

```cpp
// C3507.cpp
[module(name="x")];
[
coclass,
progid("0123456789012345678901234567890123456789"),
uuid("00000000-0000-0000-0000-000000000001") // C3507 expected
]
struct CMyStruct {
};
int main() {
}
```
