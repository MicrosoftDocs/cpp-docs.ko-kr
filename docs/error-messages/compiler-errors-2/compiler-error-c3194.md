---
description: '자세한 정보: 컴파일러 오류 C3194'
title: 컴파일러 오류 C3194
ms.date: 11/04/2016
f1_keywords:
- C3194
helpviewer_keywords:
- C3194
ms.assetid: 49d3ffc6-eff6-4b46-865b-18811692a8bb
ms.openlocfilehash: 7513b9d4964b6eb0024c3b51480f188243bf2637
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174041"
---
# <a name="compiler-error-c3194"></a>컴파일러 오류 C3194

' member ': 값 형식에는 할당 연산자를 사용할 수 없습니다.

복사 생성자 또는 복사 할당 연산자와 같이 컴파일러에서 자동으로 호출 해야 하는 특수 멤버 함수는 값 클래스 내에서 지원 되지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3194를 생성 합니다.

```cpp
// C3194.cpp
// compile with: /clr /c
value struct MyStruct {
   MyStruct& operator= (const MyStruct& i) { return *this; }   // C3194
};

ref struct MyStruct2 {
   MyStruct2% operator= (const MyStruct2% i) { return *this; }   // OK
};
```
