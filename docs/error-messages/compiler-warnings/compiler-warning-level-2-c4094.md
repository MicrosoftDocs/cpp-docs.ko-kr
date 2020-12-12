---
description: '자세한 정보: 컴파일러 경고 (수준 2) C4094'
title: 컴파일러 경고 (수준 2) C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: 63c554703c1eb6f7ecb831d1046641a0cde2094a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326533"
---
# <a name="compiler-warning-level-2-c4094"></a>컴파일러 경고 (수준 2) C4094

태그가 없는 ' token '은 기호를 선언 하지 않았습니다.

컴파일러가 태그가 없는 구조체, 공용 구조체 또는 클래스를 사용 하 여 빈 선언을 검색 했습니다. 선언이 무시 됩니다.

## <a name="example"></a>예제

```cpp
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

이 조건은 ANSI 호환성 ([/za](../../build/reference/za-ze-disable-language-extensions.md))에서 오류를 생성 합니다.
