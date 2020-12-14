---
description: '자세한 정보: 컴파일러 오류 C2383'
title: 컴파일러 오류 C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: 862346d7f2bfe92a5d2182a7fe53f260b357ad0b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185936"
---
# <a name="compiler-error-c2383"></a>컴파일러 오류 C2383

'*symbol*':이 기호에는 기본 인수를 사용할 수 없습니다.

C + + 컴파일러는 함수에 대 한 포인터에 기본 인수를 허용 하지 않습니다.

이 코드는 Visual Studio 2005 이전 버전의 Microsoft c + + 컴파일러에서 허용 되었지만 이제 오류를 제공 합니다. Visual C++의 모든 버전에서 작동 하는 코드의 경우 함수 포인터 인수에 기본값을 할당 하지 마십시오.

## <a name="example"></a>예제

다음 예제에서는 C2383를 생성 하 고 가능한 해결 방법을 보여 줍니다.

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```
