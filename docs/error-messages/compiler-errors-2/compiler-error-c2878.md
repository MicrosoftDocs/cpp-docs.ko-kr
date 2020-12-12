---
description: '자세한 정보: 컴파일러 오류 C2878'
title: 컴파일러 오류 C2878
ms.date: 11/04/2016
f1_keywords:
- C2878
helpviewer_keywords:
- C2878
ms.assetid: 83ee3de1-f554-49e8-a840-1f550cee7f69
ms.openlocfilehash: df79869572117eed851c5edd63f94234555cb990
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320475"
---
# <a name="compiler-error-c2878"></a>컴파일러 오류 C2878

' name ':이 이름의 네임 스페이스 또는 클래스가 없습니다.

정의 되지 않은 네임 스페이스 또는 클래스를 참조 했습니다.

다음 샘플에서는 C2878를 생성 합니다.

```cpp
// C2878.cpp
// compile with: /c
namespace A {}
namespace B = C;   // C2878 namespace C doesn't exist
namespace B = A;
```
