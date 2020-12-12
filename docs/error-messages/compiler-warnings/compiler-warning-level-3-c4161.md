---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4161'
title: 컴파일러 경고(수준 3) C4161
ms.date: 08/27/2018
f1_keywords:
- C4161
helpviewer_keywords:
- C4161
ms.assetid: 03d3be61-83f1-4009-8310-8758ab67055f
ms.openlocfilehash: 6bb96fbee367751533fba769a6c56f01f94df19c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272190"
---
# <a name="compiler-warning-level-3-c4161"></a>컴파일러 경고(수준 3) C4161

> #<a name="pragma-pragmapop--more-pops-than-pushes"></a>pragma *pragma*(pop ...): 푸시 횟수 보다 팝 횟수가 많습니다.

## <a name="remarks"></a>설명

소스 코드에서 pragma *pragma* 에 대한 팝 횟수가 푸시 횟수보다 하나 더 많으므로 스택이 예상대로 동작하지 않을 수 있습니다. 경고를 방지하려면 팝 횟수가 푸시 횟수를 초과하지 않도록 합니다.

## <a name="example"></a>예제

다음 예제에서는 C4161을 생성합니다.

```cpp
// C4161.cpp
// compile with: /W3 /LD
#pragma pack(push, id)
#pragma pack(pop, id)
#pragma pack(pop, id)   // C4161, an extra pop

#pragma bss_seg(".my_data1")
int j;

#pragma bss_seg(push, stack1, ".my_data2")
int l;

#pragma bss_seg(pop, stack1)
int m;

#pragma bss_seg(pop, stack1)   // C4161
```
