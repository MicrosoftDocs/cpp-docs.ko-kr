---
title: 컴파일러 경고(수준 1) C4122
ms.date: 11/04/2016
f1_keywords:
- C4122
helpviewer_keywords:
- C4122
ms.assetid: 9a83eb0d-8708-42f7-988a-b0b6f2f646a0
ms.openlocfilehash: bb5016bbf323057822c89a74001c75ab1855542c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490339"
---
# <a name="compiler-warning-level-1-c4122"></a>컴파일러 경고(수준 1) C4122

'function': alloc_text는 C 링크가 있는 함수에만 적용될 수 있습니다.

**alloc_text** pragma는 **extern c**로 선언된 함수에만 적용됩니다. 외부 C++ 함수와 함께 사용할 수 없습니다.

pragma가 무시됩니다.