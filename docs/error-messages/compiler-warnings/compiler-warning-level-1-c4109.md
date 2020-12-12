---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4109'
title: 컴파일러 경고(수준 1) C4109
ms.date: 11/04/2016
f1_keywords:
- C4109
helpviewer_keywords:
- C4109
ms.assetid: 9e8d95c6-e05d-47e0-bd87-78974b3cc06c
ms.openlocfilehash: 2063b6d9f85e497892bad27bc1b553872a309b17
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267510"
---
# <a name="compiler-warning-level-1-c4109"></a>컴파일러 경고(수준 1) C4109

예기치 않은 식별자 'identifier'입니다.

예기치 않은 식별자를 포함하는 pragma는 무시됩니다.

## <a name="example"></a>예제

```cpp
// C4109.cpp
// compile with: /W1 /LD
#pragma init_seg( abc ) // C4109
```
