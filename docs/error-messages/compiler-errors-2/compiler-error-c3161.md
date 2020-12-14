---
description: '자세한 정보: 컴파일러 오류 C3161'
title: 컴파일러 오류 C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 4e45d64e1c1f318a126122148c2dd8e3ddb9c5af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203967"
---
# <a name="compiler-error-c3161"></a>컴파일러 오류 C3161

' interface ': 인터페이스에 클래스, 구조체, 공용 구조체 또는 인터페이스를 중첩할 수 없습니다. 클래스, 구조체 또는 공용 구조체의 중첩 인터페이스가 잘못 되었습니다.

[__Interface](../../cpp/interface.md) 는 전역 범위 또는 네임 스페이스 내에만 나타날 수 있습니다. 클래스, 구조체 또는 공용 구조체는 인터페이스에 나타날 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3161를 생성 합니다.

```cpp
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```
