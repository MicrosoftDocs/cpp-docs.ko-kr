---
description: '자세한 정보: 컴파일러 경고 C4694'
title: 컴파일러 경고 C4694
ms.date: 10/25/2017
f1_keywords:
- C4694
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
ms.openlocfilehash: f6a6890fab320c2471381076707eeca30ce3e99b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315077"
---
# <a name="compiler-warning-c4694"></a>컴파일러 경고 C4694

> '*class*': 봉인 된 추상 클래스는 기본 클래스 '*base_class*'을 사용할 수 없습니다.

추상 및 봉인 클래스가 참조 형식에서 상속할 수 없습니다. 추상 및 봉인 클래스는 기본 클래스 함수를 구현할 수도 없고 스스로를 기본 클래스로 사용할 수도 없습니다.

자세한 내용은 [추상](../../extensions/abstract-cpp-component-extensions.md), [sealed](../../extensions/sealed-cpp-component-extensions.md), [클래스 및 구조체](../../extensions/classes-and-structs-cpp-component-extensions.md)를 참조 하세요.

이 경고는 자동으로 오류로 승격 됩니다. 이 동작을 수정 하려는 경우 [#pragma 경고](../../preprocessor/warning.md)를 사용 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4694를 생성합니다.

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```
