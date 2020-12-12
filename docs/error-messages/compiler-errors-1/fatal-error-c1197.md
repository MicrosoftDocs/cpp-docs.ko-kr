---
description: '자세한 정보: 심각한 오류 C1197'
title: 심각한 오류 C1197
ms.date: 11/04/2016
f1_keywords:
- C1197
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
ms.openlocfilehash: c61cbd71fa8f17dc787fd9ee5eabd0f073aafb39
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268173"
---
# <a name="fatal-error-c1197"></a>심각한 오류 C1197

프로그램이 ' mscorlib.dll_2 '을 (를) 이미 참조 했으므로 ' mscorlib.dll_1 '를 참조할 수 없습니다.

컴파일러는 공용 언어 런타임 버전과 일치 합니다.  그러나 이전 버전에서 공용 언어 런타임 파일의 버전을 참조 하려고 했습니다.

이 오류를 해결 하려면 컴파일하는 Visual C++ 버전으로 제공 된 공용 언어 런타임 버전의 파일만 참조 하십시오.

## <a name="example"></a>예제

다음 샘플에서는 C1197를 생성 합니다.

```cpp
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```
