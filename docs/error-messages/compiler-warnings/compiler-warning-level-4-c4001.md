---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4001'
title: 컴파일러 경고 (수준 4) C4001
ms.date: 11/04/2016
f1_keywords:
- C4001
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
ms.openlocfilehash: c28c1391b120983d72dc6e5b7a96faa937ee2598
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262219"
---
# <a name="compiler-warning-level-4-c4001"></a>컴파일러 경고 (수준 4) C4001

비표준 확장인 ' 한 줄로 된 주석 '을 사용 했습니다.

> [!NOTE]
> 이 경고는 한 줄 주석이 C99에서 표준 이므로 Visual Studio 2017 버전 15.5에서 제거 되었습니다.

한 줄 주석은 c + +의 표준 이며 C의 표준은 C99부터 시작 합니다.
엄격한 ANSI 호환성 ([/za](../../build/reference/za-ze-disable-language-extensions.md))에서 한 줄로 된 주석을 포함 하는 C 파일은 비표준 확장의 사용으로 인해 C4001을 생성 합니다. 한 줄 주석은 c + +에서 표준 이므로 한 줄로 된 주석을 포함 하는 C 파일은/Ze (Microsoft extensions)를 사용 하 여 컴파일할 때 C4001를 생성 하지 않습니다.

## <a name="example"></a>예제

경고를 사용 하지 않도록 설정 하려면 경고 #pragma 주석 처리를 제거 합니다 [(disable: 4001)](../../preprocessor/warning.md).

```cpp
// C4001.cpp
// compile with: /W4 /Za /TC
// #pragma warning(disable:4001)
int main()
{
   // single-line comment in main
   // C4001
}
```
