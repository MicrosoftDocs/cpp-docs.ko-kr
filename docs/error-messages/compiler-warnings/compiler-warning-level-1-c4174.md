---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4174'
title: 컴파일러 경고(수준 1) C4174
ms.date: 11/04/2016
f1_keywords:
- C4174
helpviewer_keywords:
- C4174
ms.assetid: 63301e51-24bc-43c4-bb11-252f7d513e9e
ms.openlocfilehash: 59c4450e91f6e7041fc3b3b801ca34020e7b6dc7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266925"
---
# <a name="compiler-warning-level-1-c4174"></a>컴파일러 경고(수준 1) C4174

'name': #pragma 구성 요소로 사용할 수 없습니다.

## <a name="example"></a>예제

```cpp
// C4174.cpp
// compile with: /W1
#pragma component(info)  // C4174; unknown
#pragma component(browser, off)  // turn off browse info
int main()
{
}
```
