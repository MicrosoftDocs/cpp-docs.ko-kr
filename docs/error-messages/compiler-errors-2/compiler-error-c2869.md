---
description: '자세한 정보: 컴파일러 오류 C2869'
title: 컴파일러 오류 C2869
ms.date: 11/04/2016
f1_keywords:
- C2869
helpviewer_keywords:
- C2869
ms.assetid: 6e30c001-47f3-4101-b9f1-cc542c9fffae
ms.openlocfilehash: 53171af019de9e099e2135747a8ce4d63c526b1e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333774"
---
# <a name="compiler-error-c2869"></a>컴파일러 오류 C2869

' name ': 이미 네임 스페이스로 정의 되었습니다.

이미 네임 스페이스로 사용 된 이름을 다시 사용할 수 없습니다.

다음 샘플에서는 C2869를 생성 합니다.

```cpp
// C2869.cpp
// compile with: /c
namespace A { int i; };

class A {};   // C2869, A is already used
```
