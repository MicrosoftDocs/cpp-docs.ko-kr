---
description: '자세한 정보: 컴파일러 오류 C3126'
title: 컴파일러 오류 C3126
ms.date: 11/04/2016
f1_keywords:
- C3126
helpviewer_keywords:
- C3126
ms.assetid: e72658a3-5d85-4a31-89a4-dbc3d475973d
ms.openlocfilehash: 7084359ae0be412ccb36e9a634cc72848f1c8daa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345461"
---
# <a name="compiler-error-c3126"></a>컴파일러 오류 C3126

' type ' 관리 되는 형식 내에서 ' union ' 공용 구조체를 정의할 수 없습니다.

공용 구조체는 관리 되는 형식 내에서 정의할 수 없습니다.

다음 샘플에서는 C3126를 생성 합니다.

```cpp
// C3126_2.cpp
// compile with: /clr /c
ref class Test
{
   union x
   {   // C3126
      int a;
      int b;
   };
};
```
