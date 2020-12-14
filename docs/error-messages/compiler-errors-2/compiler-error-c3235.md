---
description: '자세한 정보: 컴파일러 오류 C3235'
title: 컴파일러 오류 C3235
ms.date: 11/04/2016
f1_keywords:
- C3235
helpviewer_keywords:
- C3235
ms.assetid: 0554d6c7-e1dc-4c99-8934-cbcf491c8203
ms.openlocfilehash: 5e478e9104599f833d3f63abb042660816425028
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311905"
---
# <a name="compiler-error-c3235"></a>컴파일러 오류 C3235

'specialization': 제네릭 클래스의 명시적 특수화 또는 부분 특수화는 허용되지 않습니다.

명시적 특수화 또는 부분 특수화에 제네릭 클래스를 사용할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3235를 생성합니다.

```cpp
// C3235.cpp
// compile with: /clr
generic<class T>
public ref class C {};

generic<>
public ref class C<int> {};   // C3235 Remove this specialization to resolve this error.
```
