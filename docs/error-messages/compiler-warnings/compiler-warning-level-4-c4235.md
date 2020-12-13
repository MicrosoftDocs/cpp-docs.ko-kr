---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4235'
title: 컴파일러 경고(수준 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: 011586efb311cab1da5cd4452bbbc03a942a5045
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334892"
---
# <a name="compiler-warning-level-4-c4235"></a>컴파일러 경고(수준 4) C4235

비표준 확장이 사용 됨:이 아키텍처에서는 ' keyword ' 키워드를 사용할 수 없습니다.

컴파일러는 사용한 키워드를 지원 하지 않습니다.

이 경고는 자동으로 오류로 승격 됩니다. 이 동작을 수정 하려는 경우 [#pragma 경고](../../preprocessor/warning.md)를 사용 합니다. 예를 들어 C4235을 수준 2 경고로 만들려면 다음 코드 줄을 사용 합니다.

```cpp
#pragma warning(2:4235)
```

소스 코드 파일에 있습니다.
