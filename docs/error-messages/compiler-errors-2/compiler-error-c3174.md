---
title: 컴파일러 오류 C3174
ms.date: 11/04/2016
f1_keywords:
- C3174
helpviewer_keywords:
- C3174
ms.assetid: fe6b3b5a-8196-485f-a45f-0b2e51df4086
ms.openlocfilehash: a14b59168e0723ea25eefa9ec33a3131837a3aa4
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508277"
---
# <a name="compiler-error-c3174"></a>컴파일러 오류 C3174

모듈 특성을 지정 하지 않았습니다.

Visual C++ 특성을 사용 하는 프로그램은 특성을 사용 하는 프로그램에서 필요한 [module](../../windows/attributes/module-cpp.md) 특성도 사용 하지 않습니다.

다음 샘플에서는 C3174를 생성 합니다.

```cpp
// C3174.cpp
// C3174 expected
// uncomment the following line to resolve this C3174
// [module(name="x")];
[export]
struct S
{
   int i;
};

int main()
{
}
```
