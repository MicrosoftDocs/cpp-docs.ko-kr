---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4537'
title: 컴파일러 경고(수준 1) C4537
ms.date: 08/27/2018
f1_keywords:
- C4537
helpviewer_keywords:
- C4537
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
ms.openlocfilehash: 39219361445832f51160311733c77d3becd8bc5f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294771"
---
# <a name="compiler-warning-level-1-c4537"></a>컴파일러 경고(수준 1) C4537

> '*object*': '*OPERATOR*'가 UDT 형식이 아닌 형식에 적용 되었습니다.

## <a name="remarks"></a>설명

개체 (사용자 정의 형식)가 필요한 위치에 참조가 전달 되었습니다. 참조는 개체가 아니지만 인라인 어셈블러 코드는이를 구분할 수 없습니다. 컴파일러는 *개체가* 인스턴스인 것 처럼 코드를 생성 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4537를 생성 하 고 수정 하는 방법을 보여 줍니다.

```cpp
// C4537.cpp
// compile with: /W1 /c
// processor: x86
struct S {
    int member;
};

void f1(S &s) {
    __asm mov eax, s.member;   // C4537
    // try the following code instead
    // or, make the declaration "void f1(S s)"
    /*
    mov eax, s
    mov eax, [eax]s.member
    */
}
```
