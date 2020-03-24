---
title: 컴파일러 오류 C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: 2aa922ebeadb374a7eac73a0f452376472b00984
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206030"
---
# <a name="compiler-error-c2383"></a>컴파일러 오류 C2383

'*symbol*':이 기호에는 기본 인수를 사용할 수 없습니다.

컴파일러 C++ 는 함수에 대 한 포인터에 기본 인수를 허용 하지 않습니다.

이 코드는 Visual Studio 2005 이전 C++ 버전의 Microsoft 컴파일러에서 허용 되었지만 이제 오류를 제공 합니다. 모든 버전의 Visual C++에서 작동 하는 코드의 경우 함수 포인터 인수에 기본값을 할당 하지 마십시오.

## <a name="example"></a>예제

다음 예제에서는 C2383를 생성 하 고 가능한 해결 방법을 보여 줍니다.

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```
