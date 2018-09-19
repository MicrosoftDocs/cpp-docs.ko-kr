---
title: 컴파일러 오류 C2271 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2271
dev_langs:
- C++
helpviewer_keywords:
- C2271
ms.assetid: ea47bf57-f55d-4171-8e98-95a71d62820e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b47619bfc42037703b908ff9cb551307063f2bfa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065467"
---
# <a name="compiler-error-c2271"></a>컴파일러 오류 C2271

'operator': 삭제/새 형식 목록 한정자를 사용할 수 없습니다

연산자 (`new` 또는 `delete`)는 메모리 내 모델 지정자를 사용 하 여 선언 됩니다.

다음 샘플에서는 C2271 오류가 생성 됩니다.

```
// C2271.cpp
// compile with: /c
void* operator new(size_t) const {   // C2271
// try the following line instead
// void* operator new(size_t) {
   return 0;
}

struct X {
   static void* operator new(size_t) const;   // C2271
   // try the following line instead
   // void * X::operator new(size_t) const;   // static member operator new
};
```