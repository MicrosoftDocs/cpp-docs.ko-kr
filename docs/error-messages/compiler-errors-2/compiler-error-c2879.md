---
title: 컴파일러 오류 C2879 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2879
dev_langs:
- C++
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 632142ea0efd8a9d009f18b898213cfa92514b16
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042478"
---
# <a name="compiler-error-c2879"></a>컴파일러 오류 C2879

'symbol':만 기존 네임 스페이스 별칭 정의 네임 스페이스로 대체 이름을 지정할 수 있습니다

만들 수 없습니다는 [네임 스페이스 별칭](../../cpp/namespaces-cpp.md#namespace_aliases) 네임 스페이스 이외의 기호입니다.

다음 샘플에서는 C2879를 생성합니다.

```
// C2879.cpp
int main() {
   int i;
   namespace A = i;   // C2879 i is not a namespace
}
```