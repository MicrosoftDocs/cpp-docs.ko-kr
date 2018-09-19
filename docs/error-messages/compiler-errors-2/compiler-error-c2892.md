---
title: 컴파일러 오류 C2892 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2892
dev_langs:
- C++
helpviewer_keywords:
- C2892
ms.assetid: c22a5084-2f50-42c2-a56b-6dfe5442edc9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04efc10f6613029b2a6e4947dc202555f0d53501
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097249"
---
# <a name="compiler-error-c2892"></a>컴파일러 오류 C2892

지역 클래스 멤버 템플릿을 가질 수 없습니다.

템플릿 멤버 함수는 함수에 정의 된 클래스에서 사용할 수 없습니다.

다음 샘플에서는 C2892 오류가 생성 됩니다.

```
// C2892.cpp
int main() {
   struct local {
      template<class T>   // C2892
      void f() {}
   };
}
```