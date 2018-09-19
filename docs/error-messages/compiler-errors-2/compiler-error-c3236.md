---
title: 컴파일러 오류 C3236 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3236
dev_langs:
- C++
helpviewer_keywords:
- C3236
ms.assetid: 4ef1871f-a348-44ae-922b-1e2081de20d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ad012c067a5698eefa3f8a91e85252aef93d3e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044394"
---
# <a name="compiler-error-c3236"></a>컴파일러 오류 C3236

제네릭을 명시적으로 인스턴스화할 수 없습니다.

컴파일러는 제네릭 클래스의 명시적 인스턴스화를 허용하지 않습니다.

다음 샘플에서는 C3236을 생성합니다.

```
// C3236.cpp
// compile with: /clr
generic<class T>
public ref class X {};

generic ref class X<int>;   // C3236
```

다음 샘플에는 가능한 해결 방법을 보여 줍니다.

```
// C3236b.cpp
// compile with: /clr /c
generic<class T>
public ref class X {};
```