---
title: 컴파일러 경고 (수준 1) C4174 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4174
dev_langs:
- C++
helpviewer_keywords:
- C4174
ms.assetid: 63301e51-24bc-43c4-bb11-252f7d513e9e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16556d197c39ef0c5a8c974103535a7bc875671a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034384"
---
# <a name="compiler-warning-level-1-c4174"></a>컴파일러 경고(수준 1) C4174

'name': #pragma 구성 요소로 사용할 수 없습니다.

## <a name="example"></a>예제

```
// C4174.cpp
// compile with: /W1
#pragma component(info)  // C4174; unknown
#pragma component(browser, off)  // turn off browse info
int main()
{
}
```