---
description: '자세한 정보: 컴파일러 오류 C3237'
title: 컴파일러 오류 C3237
ms.date: 11/04/2016
f1_keywords:
- C3237
helpviewer_keywords:
- C3237
ms.assetid: 690970c8-e13b-4ff3-96e3-5fd93c4d356b
ms.openlocfilehash: 4cfb42f7b8267623d085794822f2688c8798b2d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307485"
---
# <a name="compiler-error-c3237"></a>컴파일러 오류 C3237

'generic_class': 제네릭 클래스는 사용자 지정 특성이 될 수 없습니다.

제네릭 클래스는 사용자 정의 특성이 될 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3237을 생성합니다.

```cpp
// C3237.cpp
// compile with: /clr /c
// C3237 expected
using namespace System;

generic <class T>
// Delete the following line to resolve.
[attribute(AttributeTargets::All, AllowMultiple=true)]
public ref class GR {};
```
