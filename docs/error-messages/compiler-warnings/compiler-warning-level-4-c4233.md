---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4233'
title: 컴파일러 경고(수준 4) C4233
ms.date: 10/25/2017
f1_keywords:
- C4233
helpviewer_keywords:
- C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
ms.openlocfilehash: 3e797bcefeaeee615014ea8e0bd109e4cf4ffbef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344018"
---
# <a name="compiler-warning-level-4-c4233"></a>컴파일러 경고(수준 4) C4233

> 비표준 확장이 사용 됨: '*keyword*' 키워드는 c + + 에서만 지원 됩니다.

컴파일러가 소스 코드를 c + +가 아닌 C로 컴파일 했 고 c + + 에서만 유효한 키워드를 사용 했습니다. 소스 파일의 확장명이 .c 인 경우 컴파일러는 소스 파일을 C로 컴파일하거나 [/tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)를 사용 합니다.

이 경고는 자동으로 오류로 승격 됩니다. 이 동작을 수정 하려는 경우 [#pragma 경고](../../preprocessor/warning.md)를 사용 합니다. 예를 들어 수준 4 경고 문제로 C4233을 만들려면 소스 코드 파일에 다음 줄을 추가 합니다.

```cpp
#pragma warning(4:4233)
```
