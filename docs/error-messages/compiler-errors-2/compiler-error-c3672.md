---
title: 컴파일러 오류 C3672 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3672
dev_langs:
- C++
helpviewer_keywords:
- C3672
ms.assetid: da971041-1766-467a-aecf-1d8655c6cb7a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0002b6fdf25374ec0d977c5fa4f450e41d29335f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090648"
---
# <a name="compiler-error-c3672"></a>컴파일러 오류 C3672

함수 호출의 일부로 의사 (pseudo) 소멸자 식만 사용할 수 있습니다.

소멸자를 잘못 호출 했습니다.  자세한 내용은 [소멸자](../../cpp/destructors-cpp.md)합니다.

## <a name="example"></a>예제

다음 샘플 C3672를 생성합니다.

```
// C3672.cpp
template<typename T>
void f(T* pT) {
   &pT->T::~T;   // C3672
   pT->T::~T();   // OK
};

int main() {
   int i;
   f(&i);
}
```