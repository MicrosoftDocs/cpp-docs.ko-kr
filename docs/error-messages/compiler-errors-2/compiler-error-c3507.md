---
description: '자세한 정보: 컴파일러 오류 C3507'
title: 컴파일러 오류 C3507
ms.date: 11/04/2016
f1_keywords:
- C3507
helpviewer_keywords:
- C3507
ms.assetid: 75f89767-f6f9-40f6-9820-81a49e09abdf
ms.openlocfilehash: d745aab4fec8c7a0bebab6fd4f41b27b7ac5c4df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113089"
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
