---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4230'
title: 컴파일러 경고(수준 1) C4230
ms.date: 11/04/2016
f1_keywords:
- C4230
helpviewer_keywords:
- C4230
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
ms.openlocfilehash: b5427d4ab87a1ba1c65456dab379f76100e75fea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266289"
---
# <a name="compiler-warning-level-1-c4230"></a>컴파일러 경고(수준 1) C4230

오래 사용: 한정자/한정자가 섞여 있습니다. 한정자 무시 됨

과 같은 Microsoft 한정자 앞에 한정자를 사용 하 **`__cdecl`** 는 것은 오래 된 관행입니다.

## <a name="example"></a>예제

```cpp
// C4230.cpp
// compile with: /W1 /LD
int __cdecl const function1();   // C4230 const ignored
```
