---
title: 컴파일러 경고(수준 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: 2ce261b36344126d541a9b453c88f7f8289ecba0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214336"
---
# <a name="compiler-warning-level-4-c4611"></a>컴파일러 경고(수준 4) C4611

' function '과 c + + 개체 소멸 사이의 상호 작용이 이식 가능 하지 않습니다.

일부 플랫폼에서를 포함 하는 함수는 **`catch`** 범위를 벗어난 경우 소멸의 c + + 개체 의미 체계를 지원 하지 않을 수 있습니다.

예기치 않은 동작을 방지 하려면 **`catch`** 생성자와 소멸자가 있는 함수에서을 사용 하지 마십시오.

이 경고는 한 번만 실행 됩니다. [pragma warning](../../preprocessor/warning.md)을 참조 하십시오.
