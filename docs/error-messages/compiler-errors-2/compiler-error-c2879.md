---
description: '자세한 정보: 컴파일러 오류 C2879'
title: 컴파일러 오류 C2879
ms.date: 11/04/2016
f1_keywords:
- C2879
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
ms.openlocfilehash: 6060678f71bf36d0af2e94e380a046ea7916ef05
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194373"
---
# <a name="compiler-error-c2879"></a>컴파일러 오류 C2879

' symbol ': 네임 스페이스 별칭 정의에 따라 기존 네임 스페이스에만 다른 이름을 지정할 수 있습니다.

네임 스페이스 이외의 기호에는 [네임 스페이스 별칭](../../cpp/namespaces-cpp.md#namespace_aliases) 을 만들 수 없습니다.

다음 샘플에서는 C2879를 생성 합니다.

```cpp
// C2879.cpp
int main() {
   int i;
   namespace A = i;   // C2879 i is not a namespace
}
```
