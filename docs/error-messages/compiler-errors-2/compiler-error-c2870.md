---
description: '자세한 정보: 컴파일러 오류 C2870'
title: 컴파일러 오류 C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: 74e7f2de5cfbb5aca6bd653f5711b989de4ef326
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333762"
---
# <a name="compiler-error-c2870"></a>컴파일러 오류 C2870

' name ': 네임 스페이스 정의는 파일 범위에 있거나 다른 네임 스페이스 정의 바로 안에 표시 되어야 합니다.

네임 스페이스를 `name` 잘못 정의 했습니다. 네임 스페이스는 파일 범위 (모든 블록 및 클래스 외부)에서 정의 하거나 다른 네임 스페이스 내에서 직접 정의 해야 합니다.

다음 샘플에서는 C2870를 생성 합니다.

```cpp
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```
