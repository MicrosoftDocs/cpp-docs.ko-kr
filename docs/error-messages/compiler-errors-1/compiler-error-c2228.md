---
title: 컴파일러 오류 C2228 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2228
dev_langs:
- C++
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70ea4fcdf2647264550b32ce941a3551664a6b94
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082881"
---
# <a name="compiler-error-c2228"></a>컴파일러 오류 C2228

'.identifier' 왼쪽에는 클래스/구조체/공용 구조체가 있어야 합니다.

마침표 (.)의 왼쪽 피연산자는 클래스, 구조체 또는 공용 구조체입니다.

다음 샘플에서는 C2228을 생성합니다.

```
// C2228.cpp
int i;
struct S {
public:
    int member;
} s, *ps = &s;

int main() {
   i.member = 0;   // C2228 i is not a class type
   ps.member = 0;  // C2228 ps is a pointer to a structure

   s.member = 0;   // s is a structure type
   ps->member = 0; // ps points to a structure S
}
```

Managed Extensions를 사용할 때 잘못된 구문을 사용하는 경우에도 이 오류가 나타납니다. 반면, 다른 Visual Studio 언어에서는 점(.) 연산자를 사용하여 관리되는 클래스의 멤버에 액세스할 수 있습니다. C++에서 개체에 대한 포인터는 멤버에 액세스할 때 -> 연산자를 사용해야 한다는 것을 뜻합니다.

올바르지 않은 코드: `String * myString = checkedListBox1->CheckedItems->Item[0].ToString();`

올바른 코드: `String * myString = checkedListBox1->CheckedItems->Item[0]->ToString();`