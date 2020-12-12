---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4176'
title: 컴파일러 경고(수준 1) C4176
ms.date: 11/04/2016
f1_keywords:
- C4176
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
ms.openlocfilehash: 9ba6e0ec6dff72d875aecc74e51d6f9a7e1c05e3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266899"
---
# <a name="compiler-warning-level-1-c4176"></a>컴파일러 경고(수준 1) C4176

'subcomponent': #pragma 구성 요소 브라우저의 하위 구성 요소를 알 수 없습니다.

**구성 요소** pragma에 잘못된 하위 구성 요소가 포함되어 있습니다. 특정 이름에 대한 참조를 제외하려면 이름 앞에 **참조** 옵션을 사용해야 합니다.

## <a name="example"></a>예제

```cpp
// C4176.cpp
// compile with: /W1 /LD
#pragma component(browser, off, i)  // C4176
#pragma component(browser, off, references, i) // ok
```
