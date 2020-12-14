---
description: '자세한 정보: 컴파일러 오류 C3633'
title: 컴파일러 오류 C3633
ms.date: 11/04/2016
f1_keywords:
- C3633
helpviewer_keywords:
- C3633
ms.assetid: 7d65babf-2191-4d67-a69f-f5c4c2ddf946
ms.openlocfilehash: caf89e2297bb4e9d62be76699b153f013095fa34
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239261"
---
# <a name="compiler-error-c3633"></a>컴파일러 오류 C3633

' member '를 관리 되는 ' type '의 멤버로 정의할 수 없습니다.

CLR 참조 클래스 데이터 멤버는 POD가 아닌 c + + 형식일 수 없습니다.  CLR 형식에서는 POD 네이티브 형식만 인스턴스화할 수 있습니다.  예를 들어 POD 형식에는 복사 생성자 또는 대입 연산자를 사용할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3633를 생성 합니다.

```cpp
// C3633.cpp
// compile with: /clr /c
#pragma warning( disable : 4368 )

class A1 {
public:
   A1() { II = 0; }
   int II;
};

ref class B {
public:
   A1 a1;   // C3633
   A1 * a2;   // OK
   B() : a2( new A1 ) {}
    ~B() { delete a2; }
};
```
