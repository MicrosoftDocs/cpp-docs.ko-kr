---
title: 컴파일러 경고(수준 1) C4109
ms.date: 11/04/2016
f1_keywords:
- C4109
helpviewer_keywords:
- C4109
ms.assetid: 9e8d95c6-e05d-47e0-bd87-78974b3cc06c
ms.openlocfilehash: b6b6c0f182aff9bdb4a5e4e7d35dfd111e11e079
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626310"
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