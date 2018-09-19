---
title: 컴파일러 오류 C3209 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3209
dev_langs:
- C++
helpviewer_keywords:
- C3209
ms.assetid: 1de44e39-69d1-4894-8f89-ff92136e8e5d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d5df31170578c2462c3e437d6eb7f65d6b76af8b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048411"
---
# <a name="compiler-error-c3209"></a>컴파일러 오류 C3209

'class': 제네릭 클래스는 관리 되는 또는 WinRTclass 해야 합니다.

제네릭 클래스는 관리되는 클래스 또는 Windows 런타임 클래스여야 합니다.

다음 샘플에서는 C3209를 생성하고 해결 방법을 보여 줍니다.

```
// C3209.cpp
// compile with: /clr
generic <class T>
class C {};   // C3209

// OK - ref class can be generic
generic <class T>
ref class D {};
```