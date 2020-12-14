---
description: '자세한 정보: 심각한 오류 C1021'
title: 심각한 오류 C1021
ms.date: 11/04/2016
f1_keywords:
- C1021
helpviewer_keywords:
- C1021
ms.assetid: e23171f4-ca6b-40c0-a913-a2edc6fa3766
ms.openlocfilehash: 74998b7b745ab2c0404ecea3392750b71cd40c6d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316351"
---
# <a name="fatal-error-c1021"></a>심각한 오류 C1021

'string' 전처리기 명령이 잘못되었습니다.

`string` 는 유효한 [전처리기 지시문](../../preprocessor/preprocessor-directives.md)이 아닙니다. 오류를 해결하려면 `string`에 대해 올바른 전처리기 이름을 사용합니다.

다음 샘플에서는 C1021을 생성합니다.

```cpp
// C1021.cpp
#BadPreProcName    // C1021 delete line
```
