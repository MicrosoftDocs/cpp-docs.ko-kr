---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4632'
title: 컴파일러 경고(수준 1) C4632
ms.date: 11/04/2016
f1_keywords:
- C4632
helpviewer_keywords:
- C4632
ms.assetid: 9e35d205-cf21-4e34-8bd5-e1e7b0e2cdd3
ms.openlocfilehash: a055f49a1aa71c36679f7c6177f502141e52dcde
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318873"
---
# <a name="compiler-warning-level-1-c4632"></a>컴파일러 경고(수준 1) C4632

XML 문서 주석: 파일 액세스 거부 됨: 원인

.Xdc 파일 ()에 대 `file` 한 경로가 잘못 되었으며 .xdc 파일이 생성 되지 않았습니다.

다음 샘플에서는 C4632를 생성 합니다.

```cpp
// C4632.cpp
// compile with: /clr /docv:\\falsedir /LD /W1
// C4632 expected

/// Text for class MyClass.
public ref class MyClass {};
```
