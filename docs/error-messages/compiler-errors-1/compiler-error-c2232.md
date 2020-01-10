---
title: 컴파일러 오류 C2232
ms.date: 11/04/2016
f1_keywords:
- C2232
helpviewer_keywords:
- C2232
ms.assetid: 76f302b7-30a7-4a81-9a39-b4edde33b54c
ms.openlocfilehash: 78ed8970b29126bceb06ff89d12c83cb98c4b5fd
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301810"
---
# <a name="compiler-error-c2232"></a>컴파일러 오류 C2232

'-> ': 왼쪽 피연산자에 ' 클래스 키 ' 형식이 있습니다. '. '를 사용 하세요.

`->` 연산자의 왼쪽에 있는 피연산자가 포인터가 아닙니다. 클래스, 구조체 또는 공용 구조체에는 마침표 (.) 연산자를 사용 합니다.

다음 샘플에서는 C2232를 생성합니다.

```c
// C2232.c
struct X {
    int member;
} x, *px;
int main() {
    x->member = 0;   // C2232, x is not a pointer

    px->member = 0;
    x.member = 0;
}
```
