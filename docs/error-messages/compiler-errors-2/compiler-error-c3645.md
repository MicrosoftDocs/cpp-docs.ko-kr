---
description: '자세한 정보: 컴파일러 오류 C3645'
title: 컴파일러 오류 C3645
ms.date: 11/04/2016
f1_keywords:
- C3645
helpviewer_keywords:
- C3645
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
ms.openlocfilehash: 198b22b80a4975d8bd6fab130c075621f248a93c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203772"
---
# <a name="compiler-error-c3645"></a>컴파일러 오류 C3645

' function ': 네이티브 코드로 컴파일된 함수에는 __clrcall를 사용할 수 없습니다.

함수에 일부 키워드가 있으면 함수가 네이티브로 컴파일됩니다.

## <a name="example"></a>예제

다음 샘플에서는 C3645를 생성 합니다.

```cpp
// C3645.cpp
// compile with: /clr /c
#pragma unmanaged
int __clrcall dog() {}   // C3645
```
