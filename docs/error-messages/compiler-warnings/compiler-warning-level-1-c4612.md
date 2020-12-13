---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4612'
title: 컴파일러 경고(수준 1) C4612
ms.date: 08/27/2018
f1_keywords:
- C4612
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
ms.openlocfilehash: 2844b54c592f5c4c4817cfec97d57c41fa2055b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341726"
---
# <a name="compiler-warning-level-1-c4612"></a>컴파일러 경고(수준 1) C4612

> 포함 파일 이름에 오류가 있습니다.

## <a name="remarks"></a>설명

파일 이름이 잘못되었거나 누락된 경우 **#pragma include_alias** 에서 이 경고가 발생합니다.

**#Pragma include_alias** 문에 대 한 인수는 따옴표 형식 ("*파일 이름*") 또는 꺾쇠 괄호 형식 ( \<*filename*> )을 사용할 수 있지만 둘 다 동일한 양식을 사용 해야 합니다.

## <a name="example"></a>예제

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```
