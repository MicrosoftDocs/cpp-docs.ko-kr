---
description: '자세한 정보: 컴파일러 오류 C2577'
title: 컴파일러 오류 C2577
ms.date: 11/04/2016
f1_keywords:
- C2577
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
ms.openlocfilehash: 9e54791070401f334a4dc0650ca2b1bcee5f32a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208855"
---
# <a name="compiler-error-c2577"></a>컴파일러 오류 C2577

' member ': 소멸자/종료자에는 반환 형식을 사용할 수 없습니다.

소멸자 또는 종료자는 또는 다른 형식의 값을 반환할 수 없습니다 **`void`** . **`return`** 소멸자 정의에서 문을 제거 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2577를 생성 합니다.

```cpp
// C2577.cpp
// compile with: /c
class A {
public:
   A() {}
   ~A(){
      return 0;   // C2577
   }
};
```
