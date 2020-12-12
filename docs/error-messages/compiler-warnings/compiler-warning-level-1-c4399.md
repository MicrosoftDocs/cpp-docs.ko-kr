---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4399'
title: 컴파일러 경고(수준 1) C4399
ms.date: 11/04/2016
f1_keywords:
- C4399
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
ms.openlocfilehash: a1d0fab62d13c08fb2117279d9173786c65d846f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311138"
---
# <a name="compiler-warning-level-1-c4399"></a>컴파일러 경고(수준 1) C4399

> '*symbol*':/clr: pure를 사용 하 여 컴파일할 경우 프로세스별 기호를 __declspec (dllimport)로 표시 해서는 안 됩니다.

## <a name="remarks"></a>설명

**/Clr: pure** 컴파일러 옵션은 visual studio 2015에서는 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

네이티브 이미지 또는 네이티브 및 CLR 구문이 있는 이미지의 데이터는 순수 이미지로 가져올 수 없습니다. 이 경고를 해결 하려면 **/clr** ( **/clr: pure** 아님) 또는 delete를 사용 하 여 컴파일합니다 `__declspec(dllimport)` .

## <a name="example"></a>예제

다음 샘플에서는 C4399를 생성 합니다.

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```
