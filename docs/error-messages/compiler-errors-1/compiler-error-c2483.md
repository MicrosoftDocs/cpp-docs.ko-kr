---
title: 컴파일러 오류 C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: d1a5632328c00ca2dcd03519d03fbdb648776a51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637881"
---
# <a name="compiler-error-c2483"></a>컴파일러 오류 C2483

>'*식별자*': 'thread' 생성자 또는 소멸자를 사용 하 여 개체를 선언할 수 없습니다.

이 오류 메시지는 Visual Studio 2015 이상 버전에서 사용 되지 않습니다. 이전 버전에서는로 선언 된 변수에 `thread` 특성 생성자 나 런타임에 계산에 필요한 다른 식으로 초기화할 수 없습니다. 정적 식 초기화에 필요 `thread` 데이터입니다.

## <a name="example"></a>예제

다음 샘플 Visual Studio 2013 및 이전 버전에서 C2483를 생성합니다.

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>참고 항목

[thread](../../cpp/thread.md)