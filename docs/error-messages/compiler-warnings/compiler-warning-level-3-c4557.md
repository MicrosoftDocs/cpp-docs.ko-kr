---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4557'
title: 컴파일러 경고(수준 3) C4557
ms.date: 11/04/2016
f1_keywords:
- C4557
helpviewer_keywords:
- C4557
ms.assetid: 7d9db716-03b2-4ee5-9b09-ba8aa5aa7e4c
ms.openlocfilehash: 606c1cdb36d79b13ad914912fb570c82e38eed2c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257786"
---
# <a name="compiler-warning-level-3-c4557"></a>컴파일러 경고(수준 3) C4557

'__assume'에 'effect' 효과가 있습니다.

[__Assume](../../intrinsics/assume.md) 문 2 전달 된 값이 수정 되었습니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4557를 생성 합니다.

```cpp
// C4557.cpp
// compile with: /W3
#pragma warning(default : 4557)
int main()
{
   int i;
   __assume(i++);   // C4557
}
```
