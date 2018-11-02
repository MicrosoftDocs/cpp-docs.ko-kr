---
title: 컴파일러 경고 (수준 4) C4001
ms.date: 11/04/2016
f1_keywords:
- C4001
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
ms.openlocfilehash: dd18dc27ee13eab05ea0253c8ebcc990105c15c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562281"
---
# <a name="compiler-warning-level-4-c4001"></a>컴파일러 경고 (수준 4) C4001

비표준 확장인 '한 줄으로 된 주석' 사용 했습니다.

> [!NOTE]
> 이 경고는 한 줄 주석이 표준 C99에서 되므로 Visual Studio 2017 버전 15.5에서에서 제거 됩니다.

단일 줄 주석 standard c + +에서 및 C C99를 사용 하 여 시작 됩니다.
엄격한 ANSI 호환성 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), 한 줄으로 된 주석을 포함 하는 C 파일 비표준 확장이 사용으로 인해 C4001를 생성 합니다. 한 줄 주석이 표준 c + +에서 되므로 Microsoft 확장명 (/Ze)를 사용 하 여 컴파일하면 C 파일 한 줄 주석이 들어 있는 C4001 생성 되지는 않습니다.

## <a name="example"></a>예제

경고를 해제 하려면 주석 [#pragma warning(disable:4001)](../../preprocessor/warning.md)합니다.

```
// C4001.cpp
// compile with: /W4 /Za /TC
// #pragma warning(disable:4001)
int main()
{
   // single-line comment in main
   // C4001
}
```