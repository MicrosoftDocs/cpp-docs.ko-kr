---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4619'
title: 컴파일러 경고(수준 3) C4619
ms.date: 11/04/2016
f1_keywords:
- C4619
helpviewer_keywords:
- C4619
ms.assetid: 701fea21-01aa-4bea-93d4-1cb8824170b0
ms.openlocfilehash: c108e4d1a0845cc6629a36307c33fc8342cadd67
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337270"
---
# <a name="compiler-warning-level-3-c4619"></a>컴파일러 경고(수준 3) C4619

\#pragma warning: 경고 번호 ' number '가 없습니다.

존재 하지 않는 경고를 사용 하지 않도록 설정 하려고 한 경우

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4619를 생성 합니다.

```cpp
// C4619.cpp
// compile with: /W3 /c
#pragma warning(default : 4619)
#pragma warning(disable : 4354)   // C4619, C4354 does not exist
```
