---
description: '자세한 정보: 컴파일러 오류 C3174'
title: 컴파일러 오류 C3174
ms.date: 11/04/2016
f1_keywords:
- C3174
helpviewer_keywords:
- C3174
ms.assetid: fe6b3b5a-8196-485f-a45f-0b2e51df4086
ms.openlocfilehash: 28a2daae597e93d8aa3745ad16eed491e3ea2e87
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242095"
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
