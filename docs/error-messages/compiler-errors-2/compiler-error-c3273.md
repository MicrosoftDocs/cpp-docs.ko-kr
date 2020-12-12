---
description: '자세한 정보: 컴파일러 오류 C3273'
title: 컴파일러 오류 C3273
ms.date: 11/04/2016
f1_keywords:
- C3273
helpviewer_keywords:
- C3273
ms.assetid: 1d2ce9d9-222b-4cab-94e2-d2c1a9f5ebe0
ms.openlocfilehash: 23216089bb6d4a963f04201e742af2f50818efcc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185767"
---
# <a name="compiler-error-c3273"></a>컴파일러 오류 C3273

__finally는 비관리 코드의 예외 블록에서 사용할 수 없습니다.

다음 샘플에서는 C3273을 생성합니다.

```cpp
// C3273.cpp
// compile with: /GX
int main()
{
   try
   {
   }
   catch (int)
   {
   }
   __finally   // C3273, remove __finally clause
   {
   }
}
```
