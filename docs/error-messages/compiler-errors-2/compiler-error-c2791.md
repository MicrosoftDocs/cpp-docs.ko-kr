---
title: 컴파일러 오류 C2791 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2791
dev_langs:
- C++
helpviewer_keywords:
- C2791
ms.assetid: 938ad1fb-75d9-4ce2-ad92-83d6249005b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 853e9b8a7741b31a57af172427656be8a78a99f5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098149"
---
# <a name="compiler-error-c2791"></a>컴파일러 오류 C2791

잘못 사용 했습니다 'super': 'class' 기본 클래스 없는 합니다.

키워드 [super](../../cpp/super.md) 모든 기본 클래스가 없는 클래스 멤버 함수의 컨텍스트에서 사용 되었습니다.

다음 샘플에서는 C2791를 생성합니다.

```
// C2791.cpp
struct D {
   void mf() {
      __super::mf();   // C2791
   }
};
```