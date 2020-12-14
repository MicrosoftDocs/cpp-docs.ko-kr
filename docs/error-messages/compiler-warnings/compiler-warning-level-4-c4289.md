---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4289'
title: 컴파일러 경고(수준 4) C4289
ms.date: 11/04/2016
f1_keywords:
- C4289
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
ms.openlocfilehash: c0b82702195aa7f5dcd88cd4e9bffbc1bbd1769f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294615"
---
# <a name="compiler-warning-level-4-c4289"></a>컴파일러 경고(수준 4) C4289

비표준 확장이 사용됨 : 'var' : for 루프에서 선언된 루프 제어 변수가 for 루프 범위 외부에서 사용되었습니다.

[/Ze](../../build/reference/za-ze-disable-language-extensions.md) 및 **/zc: forScope-** 를 사용 하 여 컴파일하는 경우 [for](../../cpp/for-statement-cpp.md) 루프에서 선언 된 변수는 **`for`** -루프 범위 다음에 사용 되었습니다.

/Ze를 사용 하 여 루프에서 표준 동작을 지정 하는 방법에 대 한 자세한 내용은 [/zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 를 참조 하세요 **`for`** .

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4289를 생성 합니다.

```cpp
// C4289.cpp
// compile with: /W4 /Zc:forScope-
#pragma warning(default:4289)
int main() {
   for (int i = 0 ; ; )   // C4289
      break;
   i++;
}
```
