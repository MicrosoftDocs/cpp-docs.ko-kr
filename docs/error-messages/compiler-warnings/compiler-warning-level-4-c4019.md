---
title: 컴파일러 경고(수준 4) C4019
ms.date: 11/04/2016
f1_keywords:
- C4019
helpviewer_keywords:
- C4019
ms.assetid: 4ecfe85d-673f-4334-8154-36fe7f0b3444
ms.openlocfilehash: d2bfec799b8b2981914b76839e51b7a0d09b30ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401477"
---
# <a name="compiler-warning-level-4-c4019"></a>컴파일러 경고(수준 4) C4019

전역 범위에 빈 문이 있습니다.

전역 범위의 세미콜론 앞에 문이 오지 않습니다.

불필요한 세미콜론을 제거하면 이 경고를 해결할 수 있습니다.

## <a name="example"></a>예제

```
// C4019.c
// compile with: /Za /W4
#define declint( varname ) int varname;
declint( a );   // C4019, int a;;
declint( b )   // OK, int b;

int main()
{
}
```