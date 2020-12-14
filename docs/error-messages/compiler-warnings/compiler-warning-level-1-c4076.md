---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4076'
title: 컴파일러 경고(수준 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 0bae49d3af23e499851fbf70fb24fdeb817ee03c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198260"
---
# <a name="compiler-warning-level-1-c4076"></a>컴파일러 경고(수준 1) C4076

> '*type modifier*': '*typename*' 형식과 함께 사용할 수 없습니다.

## <a name="remarks"></a>설명

형식 한정자가 또는 인지 여부는 **`signed`** **`unsigned`** 정수 형식이 아닌 형식에 사용할 수 없습니다. *형식 한정자* 는 무시 됩니다.

## <a name="example"></a>예제

다음 샘플에서는 C4076를 생성 합니다. 이 문제를 해결 하려면 형식 한정자를 제거 합니다 **`unsigned`** .

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```
