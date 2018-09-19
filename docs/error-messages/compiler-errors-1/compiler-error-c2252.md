---
title: 컴파일러 오류 C2252 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2252
dev_langs:
- C++
helpviewer_keywords:
- C2252
ms.assetid: fee74ab9-1997-4615-82fe-e6d1fe3aacd9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31fb5b48f322fbce71f1b830a01e428930937958
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041378"
---
# <a name="compiler-error-c2252"></a>컴파일러 오류 C2252

현재 범위에서 템플릿을 명시적으로 인스턴스화할 수 없습니다.

컴파일러가 템플릿의 명시적 인스턴스화를 사용 하 여 문제를 발견 했습니다.  예를 들어, 함수에서 템플릿을 명시적으로 인스턴스화할 수 없습니다.

다음 샘플에서는 C2252 오류가 생성 됩니다.

```
// C2252.cpp
class A {
public:
   template <class T>
   int getit(int i , T * it ) {
      return i;
   }
   template int A::getit<double>(int i, double * it);   // C2252
   // try the following line instead
   // template <> int A::getit<double>(int i, double * it);

};

int main() {
   // cannot explicitly instantiate in function
   template int A::getit<long>(int i, long * it);   // C2252
}
```