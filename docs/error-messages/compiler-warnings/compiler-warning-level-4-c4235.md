---
title: 컴파일러 경고 (수준 4) C4235 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4235
dev_langs:
- C++
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9e709017e51101efe53a8697bb145014f200871
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031823"
---
# <a name="compiler-warning-level-4-c4235"></a>컴파일러 경고(수준 4) C4235

비표준 확장이 사용 됨: 'keyword' 키워드는이 아키텍처에서 지원 되지 않습니다

컴파일러에서 사용 하는 키워드를 지원 하지 않습니다.

이 경고는 오류를 자동으로 승격 됩니다. 사용 하 여이 동작을 수정 하려는 경우 [#pragma 경고](../../preprocessor/warning.md)합니다. 예를 들어, 수준 2 경고에 c4235, 다음 코드 줄을 사용 하 여

```
#pragma warning(2:4235)
```

소스 코드 파일.