---
description: '자세한 정보: 컴파일러 오류 C3234'
title: 컴파일러 오류 C3234
ms.date: 11/04/2016
f1_keywords:
- C3234
helpviewer_keywords:
- C3234
ms.assetid: ebefc15a-e40d-424b-a3dd-d7e185d0ed7b
ms.openlocfilehash: 8e43b4ae7151d3be32ffc18ccec9995de67c21cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311970"
---
# <a name="compiler-error-c3234"></a>컴파일러 오류 C3234

제네릭 클래스는 제네릭 형식 매개 변수에서 상속할 수 없습니다.

제네릭 클래스는 제네릭 형식 매개 변수에서 상속할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3234를 생성합니다.

```cpp
// C3234.cpp
// compile with: /clr /c
generic <class T>
public ref class C : T {};   // C3234
// try the following line instead
// public ref class C {};
```
