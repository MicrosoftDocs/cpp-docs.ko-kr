---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4431'
title: 컴파일러 경고(수준 4) C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: 47e83f5e49ec8a4e54f4cda62267d01bd42f1ce7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251494"
---
# <a name="compiler-warning-level-4-c4431"></a>컴파일러 경고(수준 4) C4431

형식 지정자가 없습니다. int로 가정합니다. 참고: C에서는 더 이상 기본 int를 지원하지 않습니다.

이 오류는 Visual Studio 2005에 대해 수행한 컴파일러 규칙 작업의 결과로 생성 될 수 있습니다. Visual C++는 더 이상 형식화 되지 않은 식별자를 기본적으로 int로 생성 하지 않습니다. 식별자의 형식은 명시적으로 지정 해야 합니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4431를 생성 합니다.

```c
// C4431.c
// compile with: /c /W4
#pragma warning(default:4431)
i;   // C4431
int i;   // OK
```
