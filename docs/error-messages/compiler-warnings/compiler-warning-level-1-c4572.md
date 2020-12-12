---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4572'
title: 컴파일러 경고(수준 1) C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: ab447bc7ef5d702599b1583ae94ac0fa94d29a14
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332233"
---
# <a name="compiler-warning-level-1-c4572"></a>컴파일러 경고(수준 1) C4572

[ParamArray] 특성은/clr에서 사용 되지 않습니다. ' ... '를 사용 하세요. 대신

가변 인수 목록을 지정 하는 데 사용 되지 않는 스타일이 사용 되었습니다. CLR 용으로 컴파일하는 경우 대신 줄임표 구문을 사용 <xref:System.ParamArrayAttribute> 합니다. 자세한 내용은 [가변 인수 목록 (...) (c + +/cli)](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4572를 생성 합니다.

```cpp
// C4572.cpp
// compile with: /clr /W1
void Func([System::ParamArray] array<int> ^);   // C4572
void Func2(... array<int> ^){}   // OK

int main() {
   Func2(1, 2, 3);
}
```
