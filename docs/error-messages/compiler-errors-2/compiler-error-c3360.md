---
description: '자세한 정보: 컴파일러 오류 C3360'
title: 컴파일러 오류 C3360
ms.date: 11/04/2016
f1_keywords:
- C3360
helpviewer_keywords:
- C3360
ms.assetid: 6acf983a-dbb6-422b-b045-a34bb4ba6761
ms.openlocfilehash: d4ab0a4ffd12e5ffde46971134dfe858c491733c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150893"
---
# <a name="compiler-error-c3360"></a>컴파일러 오류 C3360

'string': 이름을 만들 수 없습니다.

[uuid](../../windows/attributes/uuid-cpp-attributes.md) 특성에 전달된 값이 잘못되었습니다.

다음 샘플에서는 C3360을 생성합니다.

```cpp
// C3360.cpp
[ uuid("1") ]
// try this line instead
// [ uuid("12341234-1234-1234-1234-123412341234") ]
struct A   // C3360
{
};

int main()
{
}
```
