---
title: 컴파일러 경고(수준 1) C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: b4d3356522faacfc343c33908b64597387fbe51c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521075"
---
# <a name="compiler-warning-level-1-c4572"></a>컴파일러 경고(수준 1) C4572

'...'를 사용 합니다 /clr [ParamArray] 특성은 사용 되지 않습니다. 대신

가변 인수 목록을 지정 하는 데 사용 되지 않는 스타일을 사용 했습니다. CLR을 컴파일할 때 대신 줄임표 구문을 사용 하 여 <xref:System.ParamArrayAttribute>입니다. 자세한 내용은 참조 하세요. [가변 인수 목록 (...) (C + + /CLI CLI) ](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>예제

다음 샘플 C4572를 생성합니다.

```
// C4572.cpp
// compile with: /clr /W1
void Func([System::ParamArray] array<int> ^);   // C4572
void Func2(... array<int> ^){}   // OK

int main() {
   Func2(1, 2, 3);
}
```