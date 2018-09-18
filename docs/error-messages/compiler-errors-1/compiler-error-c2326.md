---
title: 컴파일러 오류 C2326 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2326
dev_langs:
- C++
helpviewer_keywords:
- C2326
ms.assetid: 01a5ea40-de83-4e6f-a4e8-469f441258e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb81b429e88bd364d6e4d649bd28234ed829a930
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063972"
---
# <a name="compiler-error-c2326"></a>컴파일러 오류 C2326

'declarator': 함수에서 'name'에 액세스할 수 없습니다.

코드에서 멤버 변수를 수정하려고 하는데, 이는 불가능합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2326을 생성합니다.

```
// C2326.cpp
void MyFunc() {
   int i;

   class MyClass  {
   public:
      void mf() {
         i = 4;   // C2326 i is inaccessible
      }
   };
}
```