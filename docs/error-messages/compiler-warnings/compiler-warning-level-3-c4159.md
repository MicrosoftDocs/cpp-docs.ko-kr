---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4159'
title: 컴파일러 경고 (수준 3) C4159
ms.date: 11/04/2016
f1_keywords:
- C4159
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
ms.openlocfilehash: 153bd7ee7bc634ab10e0e6eb872a8f055e6470e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326465"
---
# <a name="compiler-warning-level-3-c4159"></a>컴파일러 경고 (수준 3) C4159

> #<a name="pragma-pragmapop--has-popped-previously-pushed-identifier-identifier"></a>pragma pragma (pop,...): 이전에 푸시한 '*identifier*' 식별자를 팝 했습니다.

## <a name="remarks"></a>설명

소스 코드에 pragma에 대 한 식별자가 포함 된 **push** 명령과 식별자가 없는 **pop** 명령이 있습니다. 따라서 *식별자* 가 팝 되 고 이후에 *식별자* 를 사용 하면 예기치 않은 동작이 발생할 수 있습니다.

## <a name="example"></a>예제

이 경고를 방지 하려면 **pop** 명령에 식별자를 제공 합니다. 예를 들어:

```cpp
// C4159.cpp
// compile with: /W3
#pragma pack(push, f)
#pragma pack(pop)   // C4159

// using the identifier resolves the warning
// #pragma pack(pop, f)

int main()
{
}
```
