---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4716'
title: 컴파일러 경고(수준 1) C4716
ms.date: 11/04/2016
f1_keywords:
- C4716
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
ms.openlocfilehash: 3ea67c6220cfda97989e4ea095856082608aab0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249076"
---
# <a name="compiler-warning-level-1-c4716"></a>컴파일러 경고(수준 1) C4716

'function'은 값을 반환해야 합니다.

지정 된 함수가 값을 반환 하지 않았습니다.

반환 형식이 void 인 함수만 해당 반환 값 없이 return 명령을 사용할 수 있습니다.

이 함수가 호출 되 면 정의 되지 않은 값이 반환 됩니다.

이 경고는 자동으로 오류로 승격 됩니다. 이 동작을 수정 하려는 경우 [#pragma 경고](../../preprocessor/warning.md)를 사용 합니다.

다음 샘플에서는 C4716를 생성 합니다.

```cpp
// C4716.cpp
// compile with: /c /W1
// C4716 expected
#pragma warning(default:4716)
int test() {
   // uncomment the following line to resolve
   // return 0;
}
```
